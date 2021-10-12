---
title: CentOS7配置Maven
categories: ['centos']
uniqueId: '2021-08-31 06:21:41/CentOS7配置Maven.html'
date: 2021-08-31 14:21:41
thumbnail: https://cdn.jsdelivr.net/gh/itvita/resources@master/images/20210913100605.jpeg
tags: linux
keywords: centos,maven
---

### 下载
```
wget https://dlcdn.apache.org/maven/maven-3/3.8.2/binaries/apache-maven-3.8.2-bin.tar.gz
```

### 解压
```
tar -zxvf apache-maven-3.8.2-bin.tar.gz
```

### 配置环境变量

```
vim /etc/profile

export MAVEN_HOME=/opt/apache-maven-3.8.2
export PATH=$PATH:$MAVEN_HOME/bin
```

### 刷新配置
```
source /etc/profile
```