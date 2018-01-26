# MAVEN 相关
## 其他
### 1. maven缺少依赖包，强制更新命令, 如果依旧失败，需要到jar包目录删除*.lastUpdated，获取整个jar包
```
mvn clean install -e -U

-e详细异常，-U强制更新
```  
### 2. 

##Maven Plug相关
### 1. [maven部署的时候同时部署source和javadoc](http://asialee.iteye.com/blog/1879960  )
 
```
<plugin>  
    <groupId>org.apache.maven.plugins</groupId> 
    <artifactId>maven-source-plugin</artifactId>  
    <version>2.2.1</version>
    <configuration>
        <attach>true</attach>
    </configuration>
    <executions>
        <execution>
            <id>attach-sources</id>
            <phase>deploy</phase>
        </execution>
    </executions>
</plugin>  

```  
2. 