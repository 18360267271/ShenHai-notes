本NOTES的所有相关的安装包和文档均在本人的百度云网盘中，也可进入相关组件的官网浏览，github上输入相关组件也可以。

快速配置3台互相免密的虚拟机的方法在离线数仓项目或者在线教育项目（阿里云）上。



# 简历

[待完善](docs/沈海的简历/简历.md )

# 数据结构



# 算法



# mysql



# 大数据

大数据最初，3台安装Linux系统的虚拟机集群，至少16G

相关大数据书籍文档下载：

https://www.yuque.com/kuangxiqiruogu/sglzt1/ydl8wy



## 云/物理服务器安装

[老男孩教育-李导-手把手带你玩转物理服务器](https://www.bilibili.com/video/BV1rb411n7a8)

[我在公司安装物理服务器集群的记录](docs/安装物理服务器/物理服务器.md )

[公司服务完整搭建](docs/公司服务完整搭建/公司服务完整搭建.md )

### Nginx

1.[Nginx安装与使用](docs/Nginx的安装与使用/Nginx.md )



### API网关

#### 1.[kong](docs/kong/kong.md )



### Restful

1.https://www.bilibili.com/video/BV1et411T7SS?p=2&spm_id_from=pageDriver

2.百度搜索京东万象





## 数据中台

视频

[网易大数据专家，为你剖析数据中台的现状及未来](https://www.bilibili.com/video/BV1EQ4y1M7fW?from=search&seid=4799545926254065116)

[笔记](https://www.bilibili.com/read/cv5693165?spm_id_from=333.788.b_636f6d6d656e74.9)



## 数据生成

1.[用户行为数据生成](docs/数据生成/用户行为数据生成.md )

2.业务数据



## 数据采集消费

### DataX

1.[安装与使用](docs/DataX/安装与使用.md )

2.[使用DataX将数据从MySQL导入到HDFS](docs/DataX/使用DataX将数据从MySQL导入到HDFS.md )



### Sqoop





### Flume

[Flume文档](docs/Flume/尚硅谷Flume.md )

```
flume-ng agent --conf-file /opt/module/flume/conf/file-flume-hdfs.conf --name agent1 --conf conf -Dflume.root.logger=INFO,console 
```

1. 拦截器
2. 日志采集 Flume 安装
3. 消费 Kafka 数据 Flume
4. Flume内存优化



### Kafka

Kafka文档

1.Kafka压力测试

2.SpringBoot集成Kafka

3.[kafka源码](docs/Kafka/kafka源码.md )



### Pulsar

[TGIP-CN直播合集](https://www.bilibili.com/video/BV1T741147B6/?spm_id_from=333.788.b_636f6d6d656e74.8)

1.[Pulsar](docs/Pulsar/Pulsar安装.md )



### DBUS

[DBUS部署](https://bridata.github.io/DBus/deploy.html)



## 数据存储

### hadoop

hadoop文档



#### 分布式协调服务

zookeeper



### HDFS

hdfs文档



### MapReduce

Mapreduce文档



### Yarn

Yarn文档



### Hue

集成一体化

hue文档



### Hive

hive文档



### Hbase

hbase文档



### 数据湖

hudi

[汇总Apache Hudi相关资料](https://github.com/leesf/hudi-resources)

1.[Hudi概念](docs/Hudi/概念.md)

2.[Hudi安装](docs/Hudi/安装.md )

iceberg、delta lake

### Clickhouse

文档：https://clickhouse.tech/docs/zh/

1.[Clickhouse介绍](docs/Clickhouse/介绍.md )

2.[Clickhouse安装](docs/Clickhouse/安装.md )



### ElasticSearch

安装

使用+kibana

## 数据处理

### Zeppelin

1.[zeppelin安装和使用](docs/Zeppelin/zeppelin安装和使用.md )



### Flink

Flink文档



### Spark

sparkcore

sparksql

sparkstreaming

[spark分区源码阅读](docs/spark/spark分区源码阅读.md )



## 即席查询

### Kylin

kylin文档



### Druid

Druid部署



### Presto

Presto部署



### Wormhole

[wormhole部署](https://edp963.github.io/wormhole/deployment.html)



## 数据质量

### Griffin

1.[Griffin部署](docs/Griffin/部署.md )



### 任务调度

1.[DolphinScheduler安装和使用](docs/Dolphinscheduler/DolphinScheduler安装和使用.md )

2.oozie

3.azkaban



## 元数据管理

### Atlas

Atlas文档



### Metacat

1.[Metacat安装](docs/Metacat/安装.md )





## 数据可视化

### Superset

[Superset部署和使用](docs/Superset/部署和使用.md )

#### FineBI



## 集群监控

### Zabbix

文档



### open-falcon

文档



### promethus

文档



## 算法中台

[sqlflow](docs/sqlflow算法/sqlflow安装和使用.md )



### 运维

1.[Prometheus和Grafana](docs/Prometheus和Grafana/Prometheus和Grafana.md )

2.[Grafana汉化](doc/Prometheus和Grafana/Grafana汉化.md )



## 脚本

[脚本合集](docs/脚本/合集.md )



## 大数据面试题



# 云计算



## Docker

Docker文档



## Kubernets

kubernets文档



## Kubeflow

kubeflow



## MlFlow

[Mlflow安装](docs/Mlflow/安装.md )



# 项目（文档+笔记）

## 离线数仓项目

项目总结



## 实时数仓项目

项目总结



## 在线教育项目

项目总结



## Spark实战项目：电商用户行为分析大数据平台

项目总结



## 大数据实战：电信电话项目（企业真实项目）

项目总结



## 基于大数据技术推荐系统算法案例实战

项目总结



## 大数据电商城（真实企业项目）

项目总结



## 友盟网-大数据（真实企业项目）

项目总结



## 团购网站标签生成（企业真实项目）

项目总结



## 大型电商日志分析项目

项目总结



## 共享单车项目

项目总结



## 智慧交通

项目总结



## 智能APP推荐项目

项目总结



## 大数据项目之开发电商数仓视频教程

项目总结



## 2018大数据spark sql日志分析

项目总结



## 精准广告推送之Spark实战用户画像及离线报表分析

项目总结



## 某团购网大型离线电商数据分析平台

项目总结



## 用户画像（企业真实项目）

项目总结



## CSDN电商项目（快学班）

项目总结



## Spark进阶大数据离线与实时项目实战

项目总结



## Spark Streaming实时流处理项目实战

项目总结



## SparkSQL极速入门 整合Kudu实现广告业务数据分析

项目总结







# Python



# 机器学习



# 清数研究院实习日志及相关资料

实习笔记

# 其他





