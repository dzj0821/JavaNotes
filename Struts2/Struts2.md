# 环境简述
操作系统：Windows

IDE：Eclipse for JavaEE

JDK版本：1.8.0_202

Struts2版本：2.5.20

项目编码：UTF-8

# 国际化

## 国际化页面出现乱码

### 配置文件未使用Unicode编码

如果未使用Unicode编码，且文件编码与项目（系统？）编码不一致，就会出现乱码。

解决办法：使用jdk自带的native2ASCII命令将文件转换为Unicode编码（注意指定编码格式）.

DOS命令如**native2ASCII -encoding=UTF-8 message\_zh\_CN.properties message\_zh\_CN.properties**，其中第一个message\_zh\_CN.properties为源文件路径，第二个message\_zh\_CN.properties为目标文件路径。

### JSP页面编码与项目编码不一致

如果使用Eclipse模板创建JSP页面，则JSP的默认编码为ISO-8859-1，而Struts2进行国际化替换的文本为UTF-8编码，就会出现乱码（文字显示为?号）。

解决办法：将JSP页面头部定义的**contentType="text/html; charset=ISO-8859-1"**和**pageEncoding="ISO-8859-1"**修改为UTF-8编码。