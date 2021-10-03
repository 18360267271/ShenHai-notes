# 安装

<http://nginx.org/en/download.html>

alibaba cloud centos安装nginx教程：<https://www.cnblogs.com/wuxu-dl/p/10516325.html>

```
tar -zxvf nginx-1.20.0.tar.gz -C /opt/module/Copy to clipboardErrorCopied
```

pcre-8.35

```
wget http://downloads.sourceforge.net/project/pcre/pcre/8.35/pcre-8.35.tar.gz

tar -zxvf pcre-8.35.tar.gz -C /opt/module/

cd /opt/module/pcre-8.35/

./configure

make && make install

# 版本
pcre-config --versionCopy to clipboardErrorCopied
```

配置安装

```
cd nginx-1.20.0/

./configure --prefix=/opt/module/nginx --with-http_stub_status_module --with-http_ssl_module --with-pcre=/opt/module/pcre-8.35

make && make installCopy to clipboardErrorCopied
```

## 启动

```
sbin/nginxCopy to clipboardErrorCopied
```

访问<http://192.168.28.116/>

## 部署其他

部署前端，以Griffin为例

#### 部署到服务器

```
npm run-script buildCopy to clipboardErrorCopied
```

得到`dist`

把 dist 文件夹下的打包文件拷贝到 nginx/html 下并重命名为 griffinUI

修改 `conf/nginx.conf `文件

```
location / {
   root html/griffinUI;
   index index.html index.htm;
}Copy to clipboardErrorCopied
```

启动 nginx

```
sbin/nginxCopy to clipboardErrorCopied
```

在浏览器中输入[http://192.168.28.116/即可看到项目](http://192.168.28.116/%E5%8D%B3%E5%8F%AF%E7%9C%8B%E5%88%B0%E9%A1%B9%E7%9B%AE)

> 阿里云服务器如果无法访问，那么需要在conf文件首部加上
>
> ```
> user  root;Copy to clipboardErrorCopied
> ```

## 一些命令

```
(base) [root@glong sbin]# ./nginx -s reload        # 重新加载配置
(base) [root@glong sbin]# ./nginx -s reopen        #  
(base) [root@glong sbin]# ./nginx -s stop          #停止
```


## 自己操作过的步骤

### Nginx入门

#### **简介** 

*Nginx* ("engine x") 是一个高性能的HTTP**和反向代理服务器**,特点是占有内存少，并发能力强，事实上nginx的并发能力确实在同类型的网页服务器中表现较好，中国大陆使用nginx网站用户有：百度、京东、新浪、网易、腾讯、淘宝等。

#### **Nginx** **功能** 

1) 反向代理

什么是反向代理？先看什么是正向代理

 ![img](file:///C:\Users\ADMINI~1\AppData\Local\Temp\ksohtml17560\wps1.jpg)

再看什么是反向代理

 ![img](file:///C:\Users\ADMINI~1\AppData\Local\Temp\ksohtml17560\wps2.jpg)



2) 负载均衡

![img](assets/wps3.jpg) 

负载均衡策略： 轮询

​               权重

​               备机

3) 动静分离

![img](file:///C:\Users\ADMINI~1\AppData\Local\Temp\ksohtml17560\wps4.jpg) 

 

#### *安装*

#####  1）yum安装依赖包	

 ```shell
sudo yum -y install    openssl openssl-devel pcre pcre-devel    zlib zlib-devel gcc gcc-c++
 ```

##### 2） 安装依赖包

```shell
解压缩nginx-xx.tar.gz包。
进入解压缩目录，执行
./configure   --prefix=/opt/module/nginx    
make && make install
```

--prefix=要安装到的目录

##### 3） 启动、关闭命令nginx

 ```shell
启动命令:  在/usr/local/nginx/sbin目录下执行  ./nginx
关闭命令: 在/usr/local/nginx/sbin目录下执行  ./nginx  -s  stop 
重新加载命令: 在/usr/local/nginx/sbin目录下执行  ./nginx  -s reload
 ```

如果启动时报错：

```shell
ln -s /usr/local/lib/libpcre.so.1 /lib64
```



#### 赋权限

nginx占用80端口，默认情况下非root用户不允许使用1024以下端口

 ```shell
sudo setcap cap_net_bind_service=+eip /bigdata/nginx/sbin/nginx
 ```

#### 修改/bigdata/nginx/conf/nginx.conf

 ```shell
http{
   ..........
    upstream logserver{
      server    hadoop1:8080 weight=1;  
      server    hadoop2:8080 weight=1;
      server    hadoop3:8080 weight=1;
 
    }
    server {
        listen       80;
        server_name  logserver;
        
        location / {
            root   html;
            index  index.html index.htm;
            proxy_pass http://logserver;
            proxy_connect_timeout 10;
 
         }
   ..........
}
 ```

### 集群脚本

```shell
#!/bin/bash
JAVA_BIN=/bigdata/jdk1.8.0_152/bin/java
PROJECT=gmall2019
APPNAME=xxxxx.jar
SERVER_PORT=8080
 
case $1 in
 "start")
   {
 
    for i in hadoop1 hadoop2 hadoop3
    do
     echo "========: $i==============="
    ssh $i  "$JAVA_BIN -Xms32m -Xmx64m  -jar /applog/$PROJECT/$APPNAME --server.port=$SERVER_PORT >/dev/null 2>&1  &"
    done
     echo "========NGINX==============="
    /usr/local/nginx/sbin/nginx
  };;
  "stop")
  { 
     echo "======== NGINX==============="
    /usr/local/nginx/sbin/nginx  -s stop
    for i in  hadoop1 hadoop2 hadoop3
    do
     echo "========: $i==============="
     ssh $i "ps -ef|grep $APPNAME |grep -v grep|awk '{print \$2}'|xargs kill" >/dev/null 2>&1
    done
 
  };;
   esac
 
 

```

