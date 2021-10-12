---
title: VSCode使用背景图设置
categories: ['工具']
uniqueId: '2021-08-23 10:22:27/VSCode使用背景图设置.html'
date: 2021-08-23 18:22:27
thumbnail: https://cdn.jsdelivr.net/gh/itvita/resources@master/images/20210823182331.jpeg
tags: vscode
keywords: vscode
---

> 下载地址

[点我下载](https://code.visualstudio.com/)

# 中文设置

1. cmd+Shift+p，在搜索框中输入“configure display language” 点击确定
2. 选择zh-cn 然后重启

# 背景图设置

1. 安装background插件
2. 配置setting.json增加：

```json
"backgroung.enable": true,
  "background.useDefault": false,
  "background.customImages": ["file:///Users/liuqiang/Pictures/1581747557830.jpg"],
  "background.style": {
    "content": "''",
    "pointer-events": "none",
    "position": "fixed",
    "top": "0",
    "right": "0",
    "width": "100%",
    "height": "100%",
    "z-index": "99999",
    // "background.repeat": "no-repeat",
    // contain
    "background-size": "cover",
    "opacity": 0.1
  }
```

<font color='red'>注意：顶部会出现[不受支持]（无所谓，可忽略）,提示损坏xxx ，选择不在提示即可</font>