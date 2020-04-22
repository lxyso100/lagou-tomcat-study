### 源码搭建
 * maven
 ```xml
  <?xml version="1.0" encoding="UTF-8"?>
<project xmlns="http://maven.apache.org/POM/4.0.0"
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd">

    <modelVersion>4.0.0</modelVersion>
    <groupId>org.apache.tomcat</groupId>
    <artifactId>Tomcat8.5</artifactId>
    <name>Tomcat8.5</name>
    <version>8.5.23</version>

    <dependencies>
        <dependency>
            <groupId>junit</groupId>
            <artifactId>junit</artifactId>
            <version>4.12</version>
            <scope>test</scope>
        </dependency>

        <dependency>
            <groupId>org.apache.ant</groupId>
            <artifactId>ant</artifactId>
            <version>1.10.1</version>
        </dependency>

        <dependency>
            <groupId>org.eclipse.jdt</groupId>
            <artifactId>org.eclipse.jdt.core</artifactId>
            <version>3.13.0</version>
        </dependency>

        <!--远程过程调用工具包-->
        <dependency>
            <groupId>javax.xml</groupId>
            <artifactId>jaxrpc</artifactId>
            <version>1.1</version>
        </dependency>
        <!--soap协议处理工具包-->
        <dependency>
            <groupId>javax.xml.soap</groupId>
            <artifactId>javax.xml.soap-api</artifactId>
            <version>1.4.0</version>
        </dependency>
        <!--解析webservice的wsdl文件工具-->
        <dependency>
            <groupId>wsdl4j</groupId>
            <artifactId>wsdl4j</artifactId>
            <version>1.6.2</version>
        </dependency>
        <!--Eclipse Java编译器-->
        <dependency>
            <groupId>org.eclipse.jdt.core.compiler</groupId>
            <artifactId>ecj</artifactId>
            <version>4.5.1</version>
        </dependency>

        <!---easymock辅助单元测试-->
        <dependency>
            <groupId>org.easymock</groupId>
            <artifactId>easymock</artifactId>
            <version>3.4</version>
        </dependency>

    </dependencies>

    <build>
        <finalName>Tomcat8.5</finalName>
        <sourceDirectory>java</sourceDirectory>
        <testSourceDirectory>test</testSourceDirectory>
        <resources>
            <resource>
                <directory>java</directory>
            </resource>
        </resources>
        <testResources>
            <testResource>
                <directory>test</directory>
            </testResource>
        </testResources>
        <plugins>
            <plugin>
                <groupId>org.apache.maven.plugins</groupId>
                <artifactId>maven-compiler-plugin</artifactId>
                <version>3.1</version>
                <configuration>
                    <encoding>UTF-8</encoding>
                    <source>1.8</source>
                    <target>1.8</target>
                </configuration>
            </plugin>
        </plugins>
    </build>

</project>
 
 ```
 
 * 日志乱码问题
 ```java
   /** 主要把string字符串UTF-8编码输出
    *org.apache.tomcat.util.res.StringManager方法 getString
    *org.apache.jasper.compiler方法 getMessage
    *org.apache.naming.StringManager方法 getString
    **/
    try {
           value = new String(value.getBytes("ISO-8859-1"), "UTF-8");
        } catch (Exception e) {
            e.printStackTrace();
        }
 
 ```
 
 * 提示类找不到
```1. CookieFilter 找不到，把 home\webapps\examples\WEB-INF\classes\util\CookieFilter.java 文件拷贝到 test\util 目录下  
   2. HTMLFilter 找不到，把 home\webapps\examples\WEB-INF\classes\util\CookieFilter.java 文件拷贝到 test\util 目录下
   3. 控制台或网页报错：Servlet.service() for servlet [jsp] in context with path [] threw exception [org.apache.jasper.JasperException: Unable to compile class for JSP] with root cause
     编辑 org.apache.catalina.startup.ContextConfig 文件的 configureStart() 方法，添加初始化 JSP 解析器的代码
```
 
 ### 启动流程start
 * bootstrap.init();
 * bootstrap.load(args);
 * bootstrap.start();
 
 #### 1. bootstrap.init()
 
 #### 2. bootstrap.load(args)
 
 #### 3. bootstrap.start();
 
 
 
 
