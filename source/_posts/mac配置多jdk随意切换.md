---
title: mac配置多jdk随意切换
categories: ["mac"]
uniqueId: '2021-08-27 06:39:48/mac配置多jdk随意切换.html'
date: 2021-08-27 14:39:48
thumbnail: https://cdn.jsdelivr.net/gh/itvita/resources@master/images/20210827144122.jpeg
tags: mac
keywords: jdk
---

1下载安装

jdk6：https://support.apple.com/kb/DL1572?locale=zh_CN

2配置环境变量

open .bash_profile

export PATH=$PATH:/usr/local/apache-tomcat-7.0.79/bin
export JAVA_6_HOME=/Library/Java/JavaVirtualMachines/1.6.0.jdk/Contents/Home
export JAVA_7_HOME=/Library/Java/JavaVirtualMachines/jdk1.7.0_79.jdk/Contents/Home
export JAVA_8_HOME=/Library/Java/JavaVirtualMachines/jdk1.8.0_131.jdk/Contents/Home

 

#设置默认的jdk版本

export JAVA_HOME=$JAVA_8_HOME 

 

#设置alias 用于切换

alias jdk8='export JAVA_HOME=$JAVA_8_HOME'
alias jdk7='export JAVA_HOME=$JAVA_7_HOME'
alias jdk6='export JAVA_HOME=$JAVA_6_HOME'

保存退出

source .bash_profile

3 切换jdk

　　输入  jdk6，再输入java -version 查看当前版本即可实现动态切换，jdk7，jdk8同样。

 

 

 

 