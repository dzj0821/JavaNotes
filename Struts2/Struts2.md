#环境简述
操作系统：Windows

IDE：Eclipse for JavaEE

Struts2版本：2.5.20

#框架搭建

#国际化
## 简述
将JSP中的文本信息替换成自定义的key，通过配置文件建立起不同语言的key-value映射，以达到不同语言的用户访问时显示不同语言的文本的目的。

##操作流程
前置条件：Struts2框架项目

1. 在任意包内编写内含键值对形式的，名为**自定义名称_语言缩写.properties**的语言配置文件

![](https://i.imgur.com/DbdH3uM.jpg)

2. 在JSP中添加i18n标签，name属性指定配置文件位置
3. 在i18n标签内的需要进行国际化的标签添加key属性，与配置文件中的key对应
4. 框架会根据用户的语言（由请求Header中的Accept-Language得到）将网页中