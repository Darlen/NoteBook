#Maven properties
## 这里记录所有已经用到的maven相关properties文件

```
<properties>
        <!--测试相关组件-->
        <junit.version>4.9</junit.version>
        
        <!--Spring 相关组件-->
        <spring.version>4.2.6.RELEASE</spring.version>
        
        
        <!--start 日志服务-->
        <commons-logging.version>1.1.3</commons-logging.version>
        <log4j.version>1.2.17</log4j.version>
        <slf4j-api.version>1.7.25</slf4j-api.version>
        <slf4j-log4j12.version>1.7.25</slf4j-log4j12.version>
        
        <--JSON 相关组件-->
        
        <!--Shiro 组件-->
        <shiro-core.version>1.2.2</shiro-core.version>
        <!--Servlet 组件-->
        <servlet.version></servlet.version>
        <jsp.version></jsp.version>
        
        <!-- 数据库 组件-->
        <mysql-connector-java.version>5.1.25</mysql-connector-java.version>
        
        <!--阿里相关组件-->
        <druid.version>0.2.23</druid.version>
        <fastjson.version>1.2.41</fastjson.version>
        
    </properties>
```  
## 所有相关的maven的dependance
```
<!--Spring-->
<dependency>
    <groupId>org.springframework</groupId>
    <artifactId>spring-core</artifactId>
    <version>${spring.version}</version>
</dependency>
<dependency>
    <groupId>org.springframework</groupId>
    <artifactId>spring-web</artifactId>
    <version>${spring.version}</version>
</dependency>
<dependency>
    <groupId>org.springframework</groupId>
    <artifactId>spring-webmvc</artifactId>
    <version>${spring.version}</version>
</dependency>
<dependency>
    <groupId>org.springframework</groupId>
    <artifactId>spring-beans</artifactId>
    <version>${spring.version}</version>
</dependency>
<dependency>
    <groupId>org.springframework</groupId>
    <artifactId>spring-context</artifactId>
    <version>${spring.version}</version>
</dependency>
<dependency>
    <groupId>org.springframework</groupId>
    <artifactId>spring-context-support</artifactId>
    <version>${spring.version}</version>
</dependency>
        
<!--swagger -->
<dependency>
    <groupId>io.springfox</groupId>
    <artifactId>springfox-swagger2</artifactId>
    <version>${swagger2.version}</version>
</dependency>
<dependency>
    <groupId>io.springfox</groupId>
    <artifactId>springfox-swagger-ui</artifactId>
    <version>${swagger2.version}</version>
</dependency>
<dependency>
	<groupId>io.springfox</groupId>
	<artifactId>springfox-staticdocs</artifactId>
<version>${swagger2.version}</version>

<!--servlet-->
<dependency>
    <groupId>javax.servlet</groupId>
    <artifactId>javax.servlet-api</artifactId>
    <version>3.1.0</version>
    <scope>provided</scope>
</dependency>
<dependency>
    <groupId>javax.servlet.jsp</groupId>
    <artifactId>javax.servlet.jsp-api</artifactId>
    <version>2.2.1</version>
    <scope>provided</scope>
</dependency>
 
```