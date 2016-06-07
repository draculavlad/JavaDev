# JavaDevEnv

## Install jdk 7##
```shell
wget --no-cookies \
 --no-check-certificate \
 --header "Cookie: oraclelicense=accept-securebackup-cookie" \
 "http://download.oracle.com/otn-pub/java/jdk/7u55-b13/jdk-7u55-linux-x64.rpm" \
 -O jdk-7-linux-x64.rpm
```

```shell
curl 'http://download.oracle.com/otn-pub/java/jdk/7u79-b15/jdk-7u79-linux-x64.tar.gz?AuthParam=1465303383_a51e5244c6f4a68f85fb7cf53de86b98' -H 'Accept-Encoding: gzip, deflate, sdch' -H 'Accept-Language: zh-CN,zh;q=0.8,en;q=0.6' -H 'Upgrade-Insecure-Requests: 1' -H 'User-Agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 10_11_4) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/51.0.2704.79 Safari/537.36' -H 'Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/webp,*/*;q=0.8' -H 'Referer: http://www.oracle.com/technetwork/java/javase/downloads/jdk7-downloads-1880260.html' -H 'Cookie: s_cc=true; oraclelicense=accept-securebackup-cookie; s_nr=1465303261086; gpw_e24=http%3A%2F%2Fwww.oracle.com%2Ftechnetwork%2Fjava%2Fjavase%2Fdownloads%2Fjdk7-downloads-1880260.html; s_sq=%5B%5BB%5D%5D' -H 'Connection: keep-alive' --compressed -o jdk7.tar.gz
```



## Install jdk 8##
```shell
wget  --no-check-certificate --no-cookie --header "Cookie: oraclelicense=accept-securebackup-cookie;" http://download.oracle.com/otn-pub/java/jdk/8u45-b14/jdk-8u45-linux-x64.tar.gz
```

## Add Java Config into System Env(~/.bashrc or /etc/profile)
```
export JAVA_HOME=/usr/java/jdk1.7.0_55
export PATH=$PATH:$JAVA_HOME/bin
export CLASSPATH=.:$JAVA_HOME/jre/lib:$JAVA_HOME/lib:$JAVA_HOME/lib/tools.jar
```

## Install maven##
```shell
mkdir -p /home/root/.m2/repository
cd /home/root && wget http://www.motorlogy.com/apache/maven/maven-3/3.3.3/binaries/apache-maven-3.3.3-bin.tar.gz
tar zxf apache-maven-3.3.3-bin.tar.gz 
```

## Add Maven Config into System Env(~/.bashrc or /etc/profile)##
* better append the content below following the java config int your system env config
```
export MAVEN_HOME=/opt/apache-maven-3.3.3
export M2_HOME=/opt/apache-maven-3.3.3
export M3_HOME=/opt/apache-maven-3.3.3
export PATH=$PATH:$MAVEN_HOME/bin
```

## configure maven repository config##
```shell
vi /home/root/apache-maven-3.3.3/conf/settings.xml 
  -edit:  (XML_NODE_PATH: settings)  <localRepository>/home/root/.m2/repository</localRepository>
```

## make all the config work##
```shell
source /etc/profile 
```
or
```shell
source ~/.bashrc
```
