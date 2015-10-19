# Config Build Plugin For Maven Project #

-----------------
-----------------
For Jar App
-----------------
```xml
  <build>
    <finalName>${artifactId}</finalName>
    <resources>
      <resource>
        <filtering>false</filtering>
        <directory>${basedir}/src/main/java</directory>
        <includes>
          <include>**/*.properties</include>
          <include>**/*.xml</include>
        </includes>
        <excludes>
          <exclude>**/*.doc</exclude>
        </excludes>
      </resource>
    </resources>
    <plugins>
      <plugin>
        <groupId>org.apache.maven.plugins</groupId>
        <artifactId>maven-shade-plugin</artifactId>
        <version>2.4</version>
        <executions>
          <execution>
            <phase>package</phase>
            <goals>
              <goal>shade</goal>
            </goals>
            <configuration>
              <transformers>
                <transformer implementation="org.apache.maven.plugins.shade.resource.ManifestResourceTransformer">
                  <mainClass>${absolute.class.name}</mainClass>
                </transformer>
              </transformers>
            </configuration>
          </execution>
        </executions>
      </plugin>
    </plugins>
  </build>
```

-----------------
-----------------
For Web App
-----------------
## Tomcat 7 ##
```xml
          <plugin>
            <groupId>org.apache.maven.plugins</groupId>
            <artifactId>maven-compiler-plugin</artifactId>
            <version>3.1</version>
          </plugin>
          
           <plugin>
            <groupId>org.apache.maven.plugins</groupId>
            <artifactId>maven-surefire-plugin</artifactId>
            <version>2.16</version>
          </plugin>
            
  <plugin>
        <groupId>org.apache.tomcat.maven</groupId>
        <artifactId>tomcat7-maven-plugin</artifactId>
        <version>2.2</version>
        <configuration>
          <path>/</path>
          <uriEncoding>UTF-8</uriEncoding>
          <warFile>target/${project.artifactId}</warFile>
        </configuration>
      </plugin>
```

* fixingTomcatPluginIncampatibleIssue 
* replace servlet-api:3.0 with below:

```xml
<dependency>
    <groupId>org.apache.tomcat</groupId>
    <artifactId>tomcat-servlet-api</artifactId>
    <version>7.0.30</version>
    <scope>provided</scope>
</dependency>
```

## Jetty ##
```xml
          <plugin>
            <groupId>org.apache.maven.plugins</groupId>
            <artifactId>maven-compiler-plugin</artifactId>
            <version>3.1</version>
          </plugin>
          
           <plugin>
            <groupId>org.apache.maven.plugins</groupId>
            <artifactId>maven-surefire-plugin</artifactId>
            <version>2.16</version>
          </plugin>
          <plugin>
            <groupId>org.eclipse.jetty</groupId>
            <artifactId>jetty-maven-plugin</artifactId>
            <version>${jetty.version}</version>
            <configuration>
              <stopKey>foo</stopKey>
              <stopPort>9090</stopPort>
              <httpConnector>
                <port>8080</port>
              </httpConnector>
              <webApp>
                <contextPath>/</contextPath>
              </webApp>
              <war>target/${project.artifactId}</war>
            </configuration>
          </plugin>
```
