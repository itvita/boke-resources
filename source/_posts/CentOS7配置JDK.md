---
title: CentOS7配置JDK
categories: ["centos"]
uniqueId: '2021-08-26 01:28:51/CentOS7配置JDK.html'
date: 2021-08-26 09:28:51
thumbnail: https://cdn.jsdelivr.net/gh/itvita/resources@master/images/20210826093346.jpeg
tags: linux
keywords: jdk,centos
---

#### 下载

http://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html

#### 解压

```
tar -zxvf  jdk-8u271-linux-x64.tar.gz.tar.gz
```

#### 配置环境变量

```
#vim /etc/profile -- 所有用户生效
#vim ~/.bash_profile --当前用户生效
JAVA_HOME=/opt/jdk1.8.0_271 
JRE_HOME=/opt/jdk1.8.0_271/jre 
CLASSPATH=.:$JAVA_HOME/lib/dt.jar:$JAVA_HOME/lib/tools.jar:$JRE_HOME/lib 
PATH=$JAVA_HOME/bin:$PATH 
export PATH JAVA_HOME CLASSPATH
```

#### 刷新

```
source  /etc/profile
```

