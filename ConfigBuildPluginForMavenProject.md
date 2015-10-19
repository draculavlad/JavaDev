# ConfigWebServerForMavenProject #

## Tomcat 7 ##
```xml
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
