# 如何运行工程中的样本？ #
## 要点 ##
zh-solr-se-0.1.zip中已经包含样本和数据
  * core-chinese
  * source data（json）
  * index data
  * solr.war
  * denpendent jars


## 运行步骤 ##
1. download zh-solr-se-0.1.zip

2. 在/var目录下解压（必须在/var目录下）
  * mv zh-solr-se-0.1.zip /var/
  * unzip zh-solr-se-0.1.zip

3. 进入解压后目录
  * cd /var/zh-solr-se/solr

4. 启动solr
  * ./solr stop
  * ./solr start

5. 访问solr（须保证8983端口可用）
http://localhost:8983/solr/

可以看到页面只有一个core-chinese，点击进入chinese页面

在Query string文本框输入 `*:*`

点击Search，可以看到整个core-chinese的所有数据（xml格式）。