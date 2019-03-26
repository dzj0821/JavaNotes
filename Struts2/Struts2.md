#环境简述
操作系统：Windows

IDE：Eclipse for JavaEE

Struts2：2.5.20

#框架搭建

#国际化
## 简述
1. 编写内含键值对形式的配置文件
2. 在JSP中添加i18n标签，name属性指定配置文件位置
3. 在i18n标签内的需要进行国际化的标签添加key属性，与配置文件中的key对应
4. 框架会根据用户的语言（由请求Header中的Accept-Language得到）将网页中