本搜索引擎框架实现了针对中文文本索引 搜索的基本功能和扩展接口 在solr/lucence和paoding基础上封装,结合中文文本特点,单独定制开发的一款搜索引擎框架 框架实现了multi-core共享solr,独立的索引创建 部署,支持多种格式数据接口,基本搜索接口 搜索结果多维度评价等功能 本框架中几个子工程需要使用maven2打包 编译。

This search engine framework implementation in Chinese text index search the basic functions and the extended interface in solr/lucence and paoding basis encapsulation, combined with Chinese text characteristics, individual customization development one search engine framework framework realized multi says Andrea giancoli of sharing solr, independent index create deployment, support for multiple format data interface, basic search interface search results multidimensional evaluation function this framework several son engineering need to use maven2 packing compilation.


---

V0.1 功能：

  1. 实现paoding分词到solr绑定
  1. 实现indexer基本功能（暂时只支持json格式数据）（单独project）
  1. 实现基本searcher接口（独立project）
  1. 实现一个core-中文搜索实例
  1. maven组织3个工程依赖关系
  1. 安装部署文档撰写


---

V0.2 PLANNING

  1. indexer数据输入接口定义
  1. 实现indexer接收数据格式多元化（xml、csv...）
  1. 实现multi-core实例
  1. 实现indexer数据部署脚本
  1. 结果评价模块
  1. bug fix
