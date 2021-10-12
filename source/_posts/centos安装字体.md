---
title: centos安装字体
categories: ["centos"]
uniqueId: '2021-09-13 08:45:31/centos安装字体.html'
date: 2021-09-13 16:45:31
thumbnail: https://cdn.jsdelivr.net/gh/itvita/resources@master/images/20210913172731.jpeg
tags: linux
keywords: centos,字体,linux
---
### 事先安装
```shell
yum -y install fontconfig
yum -y install mkfontscale
```
### 查看已安装字体
```shell
fc-list
```
### 查看linux已安装中文字体
```shell
fc-list :lang=zh
```
### 安装字体
#### 1. 进入字体目录
```
cd /usr/share/fonts
```
#### 2. 新建目录 myfonts
```
mkdir myfonts
```
#### 3. 上传字体到myfonts,并进入目录
> window字体目录 C:\Windows\Fonts 
#### 4. 开始安装
```shell
# 更新字体库索引
mkfontscale
mkfontdir
# 更新字体缓存
fc-cache
```