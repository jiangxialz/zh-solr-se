# 如何从源代码编译部署工程 #

## 环境准备 ##
下面的环境是必须的：
  * linux, 暂时不支持其他平台
  * maven2, 工程的组织以来maven
  * jvm1.6, java工程


## 编译 ##
  1. 下载、解压
    * download zh-solr-se-src-0.1.zip
    * rm -rf /var/zh-solr-se*** mv zh-solr-se-src-0.1.zip /var/
    * unzip zh-solr-se-src-0.1.zip
  1. 编译
    * cd /var/zh-solr-se
    * mvn clean
    * mvn install
如果运行成功会看到下面的信息：
```
[INFO] ------------------------------------------------------------------------
[INFO] Reactor Summary:
[INFO] ------------------------------------------------------------------------
[INFO] zh-solr-se-parent ..................................... SUCCESS [1.368s]
[INFO] zh-solr-se-solr-paoding-analysis ...................... SUCCESS [4.122s]
[INFO] zh-solr-se-indexer .................................... SUCCESS [4.328s]
[INFO] zh-solr-se-searchser .................................. SUCCESS [2.428s]
[INFO] ------------------------------------------------------------------------
[INFO] ------------------------------------------------------------------------
[INFO] BUILD SUCCESSFUL
[INFO] ------------------------------------------------------------------------
```**





## 部署 ##
  1. 启动solr
    * cd solr
    * ./solr.sh stop
    * ./solr.sh start
    * cd logs
    * more solr.log -- 检查日志是否有异常信息
  1. 创建core-chinese的索引，并且部署索引
    * cd /var/zh-solr-se/solr/indexer
    * ./run-indexer.sh core-chinese
```
FYI.
如果上面创建索引的命令出现curl异常，需要你的linux机器上安装curl，使用命令 apt-get install curl 或者 yum install curl

```
## 测试 ##
http://localhost:8983/solr/

可以看到页面只有一个core-chinese，点击进入chinese页面

在Query string文本框输入 `*:*`

点击Search，可以看到整个core-chinese的所有数据（xml格式）。