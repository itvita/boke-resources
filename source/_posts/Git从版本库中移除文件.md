---
title: Git从版本库中移除文件
categories: ['工具']
uniqueId: '2021-08-23 10:27:15/Git从版本库中移除文件.html'
date: 2021-08-23 18:27:15
thumbnail: https://cdn.jsdelivr.net/gh/itvita/resources@master/images/20210823182908.jpg
tags: git
keywords: git
---

> 如果你想把一个文件从版本控制中移除，并且保留本地的文件，首先需要把这个文件加入到gitignore文件中。然后执行以下命令就可以了

```
git rm file_path --cached
```

> 以上命令将file_path所代表的文件从版本控制中删除，并保留本地文件，此外还要进行commit操作才能将服务端的文件删掉。如果想把一个文件夹从版本控制中删除并保留本地的文件，只需在上述命令的基础上加上-r参数，即

```
git rm -r folder_path --cached
```

> 如果想把所有gitignore中的文件从版本控制中删除的话，需要执行以下两个命令，即先移除所有文件，再执行添加所有文件（这次会忽略gitignore中的文件）。

```
git rm -r . --cached
git add .
```
