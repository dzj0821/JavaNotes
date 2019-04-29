# 环境简述
操作系统：Windows

IDE：Eclipse for JavaEE

JDK版本：1.8.0_202

Spring版本：4.3.9RELEASE

项目版本：UTF-8

# 注解

## @RequestMapping

### 类与方法的地址映射注解可以叠加，顺序为/类映射目录/方法映射目录，内部类注解不可与外部类叠加，会与普通类一样直接映射。

## @ResponseBody

### 使用@ResponseBody网页中文乱码

SpringMVC默认返回的Content-Type为ISO-8859-1，可以在springmvc-servlet.xml中添加

    <beans>
    	<mvc:annotation-driven>
    		<mvc:message-converters register-defaults="true">
      			<bean class="org.springframework.http.converter.StringHttpMessageConverter">
    				<property name="supportedMediaTypes" value="text/html;charset=UTF-8"/>
      			</bean>
    		</mvc:message-converters>
      	</mvc:annotation-driven>
    </beans>
进行全局修改。

# 数据库连接配置

## 将数据库配置信息与spring配置文件分离

在springmv-servlet.xml中添加

    <beans>
    	<bean id="propertyConfigurer" class="org.springframework.beans.factory.config.PropertyPlaceholderConfigurer">
    		<property name="locations" value="classpath:jdbc.properties"/>
    	</bean>
    </beans>

在需要连接配置处填写如：

    <beans>
    	<bean id="dataSource" class="com.mchange.v2.c3p0.ComboPooledDataSource">
    		<property name="driverClass" value="${jdbc.driverClassName}"></property>
    		<property name="jdbcUrl" value="${jdbc.url}"></property>
    		<property name="user" value="${jdbc.username}"></property>
			<property name="password" value="${jdbc.password}"></property>
    		<property name="minPoolSize" value="1"></property>
    		<property name="maxPoolSize" value="5"></property>
    		<property name="initialPoolSize" value="1"></property>
    		<property name="acquireIncrement" value="1"></property>
    	</bean>
    <beans>

jdbc.properties如：

    jdbc.driverClassName=com.mysql.jdbc.Driver
    jdbc.url=jdbc:mysql://localhost:3306/sql
    jdbc.username=root
    jdbc.password=root