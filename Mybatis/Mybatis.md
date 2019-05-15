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


# 注解

## @Results

### 在@Results注解中声明映射关系（@One, @Many）时，取到的实体类主键值为0

在@Results注解中声明映射关系（@One, @Many）时需要手动声明主键，如：

    @Results({
    		@Result(column = "id", property = "id", id = true),
    		@Result(column = "grade_id", property = "grade", one=@One(select = "pers.dzj0821.SchoolLeaveSystem.dao.GradeDao.selectGradeById")),
    		@Result(column = "major_id", property = "major", one=@One(select = "pers.dzj0821.SchoolLeaveSystem.dao.MajorDao.selectMajorById"))
    	})

## 其他

### 使用@Select、@Insert、@Update、@Delete注解时，即使变量名和占位符内的名称不匹配也可以正常执行SQL语句

当只有一个占位符和一个参数时，默认将这个参数直接装入占位符中而不进行名称检测，多个参数时必须用@Param注解声明变量对应的占位符名称，或用数字（从0开始）指定参数，如：

    @Select("select * from user where id = #{id} and username = #{username}")
    public User selectUserByIdAndUsername(@Param("id") int id, @Param("username") String username);

    @Select("select * from user where id = #{0} and username = #{1}")
	public User selectUserByIdAndUsername(int id, String username);