---
title: app无法打开或已损坏解决办法
categories: ["mac"]
uniqueId: '2021-08-27 06:43:19/app无法打开或已损坏解决办法.html'
date: 2021-08-27 14:43:19
thumbnail: https://cdn.jsdelivr.net/gh/itvita/resources@master/images/20210827144429.jpeg
tags: mac
keywords: mac
---


1、系统偏好设置... -> 安全性与隐私-->修改为任何来源

2、如果没有任何来源  ,打开终端执行:sudo spctl --master-disable

如果还不行 

sudo xattr -d com.apple.quarantine /Applications/Navicat\ for\ SQL\ Server.app

 

/Applications/Navicat\ for\ SQL\ Server.app 为app路径  

如果有空格，空格前加 \