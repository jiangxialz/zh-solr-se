# 如何定制化开发自己的搜索引擎 #

## 索引部分 ##
1. 将indexer工程导入eclipse（any IDE you prefer）
有一个非常简便的方法，进入indexer目录，使用命令 mvn eclipse:eclipse，然后在eclipse中导入现有工程即可。

2. 创建你的indexer
  * 参照chinese包，建立你的包，举个例子，你的包名叫 movie
  * 创建class, 参照ChineseIndexer
```
public class MovieIndexer extends IndexerBase {
...

重写
indexAllDocuments()
main()

```

  * 修改IndexerMain，添加MovieIndexer到工厂方法
```
	private IndexerBase getIndexer(final String coreName)
			throws UnsupportedCoreException {
		if (SolrConstants.CORE_NAME_CHINESE.equalsIgnoreCase(coreName)) {
			return new ChineseIndexer();
		} else if (SolrConstants.CORE_NAME_MOVIE.equalsIgnoreCase(coreName)) {
			return new MovieIndexer();
		} else {
			throw new UnsupportedCoreException(coreName);
		}
	}
```

## 搜索部分 ##
1. 将searcher导入eclipse
2. 参照chinese包，创建你的包，还是用movie举例
```
public class MovieSearchService extends DefaultSearchService {
...
重写 execute()
```

3. 在SearchServiceFactory添加movie的searchservice类


## solr配置 ##
1. 创建core-movie
  * cd /var/zh-solr-se/solr/solr
  * cp -r core-chinese core-movie
  * cd core-movie/conf
  * 修改schema.xml(主要是字段和要选取的数据类型), 这是core-chinese的字段，你需要修改为movie的字段，类型，是否需要索引、是否存储到索引... 修改schma的名字
```
<schema name="chinese" version="1.1">

...

<fields>
   <field name="chinese_id" type="string" indexed="true" stored="true" required="true" />
   <field name="chinese_name" type="string" indexed="true" stored="true" required="false" />
   <field name="chinese_content" type="text" indexed="true" stored="true" required="false" omitNorms="true"/>

   <dynamicField name="_local*" type="sdouble"  indexed="true" stored="true"/>
</fields>
```
  * 修改solrconfig.xml, 制定索引数据位置
```
<dataDir>${solr.data.dir:./solr/core-movie/data}</dataDir>
```

2. 添加core-movie到solr.xml
cd /var/zh-solr-se/solr/solr
添加下面一行：
```
<core name="core-movie" instanceDir="core-movie"/>
```

## 中文解析部分 ##
  * 使用paoding分词
  * 在solr-paoding-analysis工程中
  * 中文字典在solr/dic目录
  * 对于customized后的分词类，在schema.xml中修改
```
 <fieldType name="text" class="solr.TextField" positionIncrementGap="100">
      <analyzer type="index">
        <!--<tokenizer class="solr.WhitespaceTokenizerFactory"/>-->
        <tokenizer class="net.paoding.analysis.analyzer.ChineseTokenizerFactory"/>
...
```