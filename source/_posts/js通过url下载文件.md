---
title: js通过url下载文件
categories: ["前端"]
toc: true
recommend: 1
uniqueId: '2021-08-23 10:29:56/js通过url下载文件.html'
date: 2021-08-23 18:29:56
thumbnail: https://cdn.jsdelivr.net/gh/itvita/resources@master/images/20210823183228.jpeg
tags: javascript
keywords: js,javascript
---

```javascript
fetch(src).then(res => res.blob().then(blob => {
  let a = document.createElement('a');
  let url = window.URL.createObjectURL(blob);
  a.href = url;
  a.download = name;
  a.click();
  window.URL.revokeObjectURL(url);
}))
```