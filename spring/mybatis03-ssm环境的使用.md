1）搭建Spring+SpringMVC+Mybatis开发环境

2）使用SSM完成增删改查功能


1）搭建Spring+SpringMVC+Mybatis开发环境

	jar包：
	spring-core-3.2.3.RELEASE.jar
	spring-webmvc-3.2.3.RELEASE.jar
	spring-web-3.2.3.RELEASE.jar
	spring-jdbc-3.2.3.RELEASE.jar
	spring-context-3.2.3.RELEASE.jar
	spring-beans-3.2.3.RELEASE.jar
	spring-context-support-3.2.3.RELEASE.jar
	spring-tx-3.2.3.RELEASE.jar
	spring-aop-3.2.3.RELEASE.jar
	aopalliance-1.0.jar
	spring-expression-3.2.3.RELEASE.jar
	
	
	mysql-connector-java-5.1.0-bin.jar
	mybatis-3.2.2.jar
	mybatis-spring-1.0.2.jar
	commons-dbcp.jar
	commons-pool.jar
	commons-logging-1.1.1.jar
	log4j-1.2.16.jar
	
pom.xml文件：
	
	<project xmlns="http://maven.apache.org/POM/4.0.0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
	xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/maven-v4_0_0.xsd">
	<modelVersion>4.0.0</modelVersion>
	<groupId>com.qyxy</groupId>
	<artifactId>ssm</artifactId>
	<packaging>war</packaging>
	<version>1.0-SNAPSHOT</version>
	<name>ssm Maven Webapp</name>
	<url>http://maven.apache.org</url>
	<dependencies>
	<dependency>
	  <groupId>junit</groupId>
	  <artifactId>junit</artifactId>
	  <version>3.8.1</version>
	  <scope>test</scope>
	</dependency>
	<!-- https://mvnrepository.com/artifact/org.springframework/spring-webmvc -->
	<dependency>
	  <groupId>org.springframework</groupId>
	  <artifactId>spring-webmvc</artifactId>
	  <version>5.0.2.RELEASE</version>
	</dependency>
	<!-- https://mvnrepository.com/artifact/javax.servlet/javax.servlet-api -->
	<dependency>
	  <groupId>javax.servlet</groupId>
	  <artifactId>javax.servlet-api</artifactId>
	  <version>3.1.0</version>
	  <scope>provided</scope>
	</dependency>
	<!-- https://mvnrepository.com/artifact/javax.servlet/jstl -->
	<dependency>
	  <groupId>javax.servlet</groupId>
	  <artifactId>jstl</artifactId>
	  <version>1.2</version>
	</dependency>
	
	<!-- https://mvnrepository.com/artifact/com.alibaba/fastjson -->
	<dependency>
	<groupId>com.alibaba</groupId>
	<artifactId>fastjson</artifactId>
	<version>1.2.44</version>
	</dependency>
	
	<!-- https://mvnrepository.com/artifact/commons-fileupload/commons-fileupload -->
	<dependency>
	<groupId>commons-fileupload</groupId>
	<artifactId>commons-fileupload</artifactId>
	<version>1.3.1</version>
	</dependency>
	<!-- https://mvnrepository.com/artifact/org.mybatis/mybatis -->
	<dependency>
	<groupId>org.mybatis</groupId>
	<artifactId>mybatis</artifactId>
	<version>3.4.5</version>
	</dependency>
	
	<!-- https://mvnrepository.com/artifact/mysql/mysql-connector-java -->
	<dependency>
	<groupId>mysql</groupId>
	<artifactId>mysql-connector-java</artifactId>
	<version>5.1.44</version>
	</dependency>
	
	<!-- https://mvnrepository.com/artifact/org.springframework/spring-aop -->
	<dependency>
	<groupId>org.springframework</groupId>
	<artifactId>spring-aop</artifactId>
	<version>5.0.2.RELEASE</version>
	</dependency>
	
	<!-- https://mvnrepository.com/artifact/org.aspectj/aspectjweaver -->
	<dependency>
	<groupId>org.aspectj</groupId>
	<artifactId>aspectjweaver</artifactId>
	<version>1.8.13</version>
	</dependency>
	
	<!-- https://mvnrepository.com/artifact/org.springframework/spring-tx -->
	<!--<dependency>-->
	<!--<groupId>org.springframework</groupId>-->
	<!--<artifactId>spring-tx</artifactId>-->
	<!--<version>5.0.2.RELEASE</version>-->
	<!--</dependency>-->
	
	<!-- https://mvnrepository.com/artifact/aopalliance/aopalliance -->
	<dependency>
	<groupId>aopalliance</groupId>
	<artifactId>aopalliance</artifactId>
	<version>1.0</version>
	</dependency>
	
	<!-- https://mvnrepository.com/artifact/org.apache.commons/commons-dbcp2 -->
	<dependency>
	<groupId>org.apache.commons</groupId>
	<artifactId>commons-dbcp2</artifactId>
	<version>2.1.1</version>
	</dependency>
	
	<!-- https://mvnrepository.com/artifact/org.springframework/spring-jdbc -->
	<dependency>
	<groupId>org.springframework</groupId>
	<artifactId>spring-jdbc</artifactId>
	<version>5.0.2.RELEASE</version>
	</dependency>
	
	<!-- https://mvnrepository.com/artifact/org.mybatis/mybatis-spring -->
	<dependency>
	<groupId>org.mybatis</groupId>
	<artifactId>mybatis-spring</artifactId>
	<version>1.3.1</version>
	</dependency>
	<!-- https://mvnrepository.com/artifact/org.apache.logging.log4j/log4j-core -->
	<dependency>
	<groupId>org.apache.logging.log4j</groupId>
	<artifactId>log4j-core</artifactId>
	<version>2.10.0</version>
	</dependency>
	
	
	</dependencies>
	<build>
	<finalName>ssm</finalName>
	</build>
	</project>

web.xml 配置
	
	<?xml version="1.0" encoding="UTF-8"?>
	<web-app version="2.5"
	         xmlns="http://java.sun.com/xml/ns/javaee"
	         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
	         xsi:schemaLocation="http://java.sun.com/xml/ns/javaee
		http://java.sun.com/xml/ns/javaee/web-app_2_5.xsd">
	
	  <!-- 指定Spring Bean的配置文件所在目录。默认配置在WEB-INF目录下 -->
	  <context-param>
	    <param-name>contextConfigLocation</param-name>
	    <param-value>classpath:spring.xml</param-value>
	  </context-param>
	
	  <!-- spring字符编码过滤器start-->
	  <filter>
	    <!--① Spring 编码过滤器 -->
	    <filter-name>encodingFilter</filter-name>
	    <filter-class>
	      org.springframework.web.filter.CharacterEncodingFilter
	    </filter-class>
	    <!--② 编码方式  -->
	    <init-param>
	      <param-name>encoding</param-name>
	      <param-value>UTF-8</param-value>
	    </init-param>
	    <!--③ 强制进行编码转换 -->
	    <init-param>
	      <param-name>forceEncoding</param-name>
	      <param-value>true</param-value>
	    </init-param>
	  </filter>
	  <!-- ② 过滤器的匹配 URL -->
	  <filter-mapping>
	    <filter-name>encodingFilter</filter-name>
	    <url-pattern>/*</url-pattern>
	  </filter-mapping>
	  <!-- spring字符编码过滤器end-->
	
	
	  <!-- Spring MVC配置 -->
	  <!-- ====================================== -->
	  <servlet>
	    <servlet-name>spring</servlet-name>
	    <servlet-class>org.springframework.web.servlet.DispatcherServlet</servlet-class>
	    <init-param>
	      <param-name>contextConfigLocation</param-name>
	      <param-value>classpath:spring-mvc.xml</param-value>
	    </init-param>
	    <load-on-startup>1</load-on-startup>
	  </servlet>
	  <servlet-mapping>
	    <servlet-name>spring</servlet-name>
	    <url-pattern>/</url-pattern>
	  </servlet-mapping>
	
	
	  <!-- Spring配置 -->
	  <!-- ====================================== -->
	  <listener>
	    <listener-class>org.springframework.web.context.ContextLoaderListener</listener-class>
	  </listener>
	
	
	  <welcome-file-list>
	    <welcome-file>index.jsp</welcome-file>
	  </welcome-file-list>
	</web-app>

spring.xml文件
	
	<?xml version="1.0" encoding="UTF-8"?>
	<beans xmlns="http://www.springframework.org/schema/beans"
	           xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
	           xmlns:aop="http://www.springframework.org/schema/aop"
	           xmlns:p="http://www.springframework.org/schema/p"
	           xmlns:tx="http://www.springframework.org/schema/tx"
	           xmlns:context="http://www.springframework.org/schema/context"
	           xsi:schemaLocation="
	                http://www.springframework.org/schema/beans 
	                http://www.springframework.org/schema/beans/spring-beans-2.5.xsd
	                http://www.springframework.org/schema/aop 
	                http://www.springframework.org/schema/aop/spring-aop-2.5.xsd
	                http://www.springframework.org/schema/tx
	                http://www.springframework.org/schema/tx/spring-tx-2.5.xsd
	                http://www.springframework.org/schema/context 
	                http://www.springframework.org/schema/context/spring-context.xsd">
	        <context:annotation-config></context:annotation-config>
	        <context:component-scan base-package="com.qyxy.service.impl,com.qyxy.dao,com.qyxy.domain"></context:component-scan>
	        <!-- Properties文件读取配置，base的properties -->
	        <context:property-placeholder location="classpath:jdbc.properties"/>
	
	        <!-- JNDI获取数据源(使用dbcp连接池) -->
	        <bean id="dataSource" class="org.apache.commons.dbcp2.BasicDataSource" destroy-method="close" scope="singleton">
	            <property name="driverClassName" value="${driverClassName}"/>
	            <property name="url" value="${url}"/>
	            <property name="username" value="${uname}"/>
	            <property name="password" value="${password}"/>
	        </bean>

        <!-- enable transaction demarcation with annotations -->
        <tx:annotation-driven />

        <!-- (事务管理)transaction manager, use JtaTransactionManager for global tx -->
        <bean id="transactionManager" class="org.springframework.jdbc.datasource.DataSourceTransactionManager">
            <property name="dataSource" ref="dataSource" />
        </bean>

        <!-- define the SqlSessionFactory, notice that configLocation is not needed when you use MapperFactoryBean -->
        <bean id="sqlSessionFactory" class="org.mybatis.spring.SqlSessionFactoryBean">
            <property name="dataSource" ref="dataSource" />
            <property name="configLocation" value="classpath:mybatis-config.xml" />
        </bean>
        <!-- scan for mappers and let them be autowired
        MapperScannerConfigurer Mybatis-Spring 会自动为我们注册Mapper对应的MapperFactoryBean对象-->
        <!-- Mapper接口所在包名，Spring会自动查找其下的Mapper -->
        <bean class="org.mybatis.spring.mapper.MapperScannerConfigurer">
            <property name="basePackage" value="com.qyxy.dao" />
        </bean>



    </beans>

spring-mvc.xml文件：

	<?xml version="1.0" encoding="UTF-8"?>
	<beans xmlns="http://www.springframework.org/schema/beans"
	       xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
	       xmlns:context="http://www.springframework.org/schema/context"
	       xmlns:mvc="http://www.springframework.org/schema/mvc"
	       xsi:schemaLocation="http://www.springframework.org/schema/beans
	       http://www.springframework.org/schema/beans/spring-beans.xsd
	       http://www.springframework.org/schema/context
	       http://www.springframework.org/schema/context/spring-context.xsd
	       http://www.springframework.org/schema/mvc 
	       http://www.springframework.org/schema/mvc/spring-mvc.xsd">
	
	    <context:component-scan base-package="com.qyxy.controller" />
	    <mvc:annotation-driven></mvc:annotation-driven>
	    <mvc:default-servlet-handler/>
	    <beans>
	
	        <!-- ****************视图解析器，解析jsp视图，默认使用jstl，classpath下需要有jstl的包*************** -->
	        <bean class="org.springframework.web.servlet.view.InternalResourceViewResolver">
	            <!-- 默认支持下面的jstl -->
	            <!-- <property name="viewClass" value="org.springframework.web.servlet.view.JstlView"/> -->
	            <!-- jsp路径前缀 -->
	            <property name="prefix" value="/WEB-INF/jsp/"/>
	            <!-- jsp路径后缀 -->
	            <property name="suffix" value=".jsp"></property>
	        </bean>
	
	        <bean id="multipartResolver"
	              class="org.springframework.web.multipart.commons.CommonsMultipartResolver">
	            <!-- 设置上传文件的最大尺寸为1MB -->
	            <property name="maxUploadSize">
	                <value>1024000000</value>
	            </property>
	        </bean>
	
	
	    </beans>
	
	</beans>


mybatis-config.xml文件

	<?xml version="1.0" encoding="UTF-8"?>  
    <!DOCTYPE configuration   
        PUBLIC "-//mybatis.org//DTD Config 3.0//EN"   
        "http://mybatis.org/dtd/mybatis-3-config.dtd">  
    <configuration>  
        <settings>  
            <!-- changes from the defaults -->  
            <setting name="lazyLoadingEnabled" value="false" />
            <setting name="mapUnderscoreToCamelCase" value="true"/>
        </settings>  
       <typeAliases>  
           <!--这里给实体类取别名，方便在mapper配置文件中使用--> 
           <!-- <typeAlias alias="user" type="com.qyxy.domain.User"/>  -->
           <package name="com.qyxy.domain"/>
       </typeAliases>  
    </configuration>  


jdbc.properties

	driverClassName=com.mysql.jdbc.Driver
	url=jdbc:mysql://127.0.0.1:3306/mydb
	uname=root
	password=hnqy
	minIdle=10
	maxIdle=50
	initialSize=5
	maxActive=100
	maxWait=100
	removeAbandonedTimeout=180
	removeAbandoned=true

log4j2.xml文件：

	<?xml version="1.0" encoding="UTF-8"?>
        <Configuration status="trace">
       <Appenders>
         <Console name="Console" target="SYSTEM_OUT">
           <PatternLayout pattern="%d{HH:mm:ss.SSS} [%t] %-5level %logger{36} - %msg%n"/>
         </Console>
       </Appenders>
       <Loggers>
         <Root level="trace">
           <AppenderRef ref="Console"/>
         </Root>
       </Loggers>
     </Configuration>	


mybatis  sql日志输出：

log4j2.xml

	<?xml version="1.0" encoding="UTF-8"?>
	    <Configuration status="trace">
        <Appenders>
            <Console name="Console" target="SYSTEM_OUT">
                <PatternLayout pattern="%d{HH:mm:ss.SSS} [%t] %-5level %logger{36} - %msg%n"/>
            </Console>
        </Appenders>
        <Loggers>
            <Root level="trace">
                <AppenderRef ref="Console"/>
            </Root>
            <Logger name="com.qyxy.mapper" level="trace" additivity="false">
                <AppenderRef ref="Console"/>
            </Logger>

        </Loggers>
    </Configuration>
    
 mybatis-confgi.xml
 
     <setting name="cacheEnabled" value="false"/>
       <!-- <setting name="lazyLoadingEnabled" value="true"></setting>-->
        <!--打开延迟加载的开关  -->
        <setting name="lazyLoadingEnabled" value="true"/>
        <!--将积极加载改为消极加载及按需加载  -->
        <setting name="aggressiveLazyLoading" value="false"/>
        <setting name="mapUnderscoreToCamelCase" value="true"/>

        <setting name="logImpl" value="LOG4J2" />

    </settings>
