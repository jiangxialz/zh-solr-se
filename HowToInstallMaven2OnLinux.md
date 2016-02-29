# 在linux下安装maven2 #
## linux分类 ##
一般来说著名的linux系统基本上分两大类：
  1. RedHat 系列：Redhat、Centos、Fedora等
  1. Debian 系列：Debian、Ubuntu等
## 安装工具 ##
  1. RedHat 系列：yum
  1. Debian 系列：apt-get
请按照上面的安装工具分类安装不同的软件。请确保你的linux机器上已经安装过相应的安装软件工具。
## 安装maven2 ##
  1. RedHat系列：yum install maven2
  1. Debian系列：apt-get install maven2
## 验证 ##
在用户根目录下，有一个隐藏文件，使用ls -al命令察看，可以看到一个 .m2 的目录，该目录就是maven2的本地库。

在用户根录，运行mvn -v命令可以看到类似下面的信息：
```
Apache Maven 2.2.1 (rdebian-8)  -- maven版本
Java version: 1.6.0_06  -- java版本
Java home: /usr/lib/jvm/java-6-sun-1.6.0.06/jre -- jre位置
Default locale: zh_CN, platform encoding: UTF-8  -- 本地编码
OS name: "linux" version: "3.2.0-29-generic" arch: "amd64" Family: "unix" -- 系统名称
```