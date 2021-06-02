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