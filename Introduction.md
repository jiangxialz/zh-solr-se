# 基于solr的中文搜索引擎（chinese search engine base on solr） #
## 简单介绍 ##
> 本搜索引擎框架实现了针对中文文本索引、搜索的基本功能和扩展接口。在solr/lucence和paoding基础上封装，结合中文文本特点，单独定制开发的一款搜索引擎框架。框架实现了multi-core共享solr，独立的索引创建、部署，支持多种格式数据接口，基本搜索接口、搜索结果多维度评价等功能。本框架中几个子工程需要使用maven2打包、编译。

## 使用的开源框架和版本 ##
  * pache solr 1.4
  * ucence 2.9.3
  * aoding-2.0.4-beta
  * ervlet-2.4
  * aven2
  * un-jdk-1.6

## 下载区文件介绍 ##
  * h-solr-se-src-0.1.zip 本项目的源代码（非常干净）
  * h-solr-se-0.1.zip 项目的部署程序（包含一个core-chinese的实例）

## 源代码组织结构介绍 ##

  * ndexer         --- 创建索引部分
  * ovie-data.json --- 样本文件，json格式
  * om.xml         --- maven pom文件
  * earcher        --- 搜索接口
  * olr            --- solr base 文件
  * olr-paoding-analysis --- paoding绑定solr部分

## FYI ##

  1. 项目使用maven2组织，请使用的同学先安装maven2。
  1. 项目在linux下安装编译，因为项目使用了linux文件系统的路径表法方式，可能在其他系统上会出现问题。