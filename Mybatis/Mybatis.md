# 环境简述
操作系统：Windows

IDE：Eclipse for JavaEE

JDK版本：1.8.0_202

项目编码：UTF-8

Mybatis版本：3.2.6

# 数据类型与Java类型转换

## 命名方式转换

### 驼峰命名与下划线命名互相转换

mybatis-config.xml中添加

    <configuration>
        <settings>
            <setting name="mapUnderscoreToCamelCase" value="true"/>
        </settings>
    </configuration>

## 枚举

### 使用枚举序号（从0开始）进行转换

mybatis-config.xml中添加

    <configuration>
        <typeHandlers>
            <typeHandler handler="org.apache.ibatis.type.EnumOrdinalTypeHandler" javaType="com.foo.ProcessStatus"/>
        </typeHandlers>
    </configuration>

# XML配置

## mybatis-config.xml

### Error: The content of element type "configuration" must match "(properties?,settings?,typeAliases?,typeHandlers?,objectFactory?,objectWrapperFactory?,plugins?,environments?,mappers?)".

XML标签需要按顺序编写。

### Waring: Stream not available

将

    <!DOCTYPE configuration
      PUBLIC "-//mybatis.org//DTD Config 3.0///EN"
      "http://mybatis.org/dtd/mybatis-3-config.dtd">

更改为

    <!DOCTYPE configuration
      PUBLIC "-//mybatis.org//DTD//EN"
      "http://mybatis.org/dtd/mybatis-3-config.dtd">