---
title: vscode配置
categories: ["工具"]
uniqueId: '2021-08-27 03:21:28/vscode配置.html'
date: 2021-08-27 11:21:28
thumbnail: https://cdn.jsdelivr.net/gh/itvita/resources@master/images/20210827112244.jpg
tags: vscode
keywords: vscode
---

```js
{
  "workbench.colorTheme": "Atom One Dark",
  "workbench.iconTheme": "vscode-icons-mac",
  "editor.fontFamily": "Courier New",
  "editor.fontSize": 18,
  // "files.autoSave": "afterDelay", //打开自动保存
  "editor.lineHeight": 20, //设置文字行高
  // "editor.lineNumbers": "on", //开启行数提示
  // "window.zoomLevel": 0, // 调整窗口的缩放级别
  // "editor.detectIndentation": false,
  // "emmet.triggerExpansionOnTab": true,
  // "editor.formatOnSave": true, // eslint保存格式化
  // "javascript.format.enable": false, // 不启动JavaScript格式化
  // "prettier.eslintIntegration": true,
  // "[vue]": {
  //     "editor.defaultFormatter": "esbenp.prettier-vscode"
  // } // 让prettier遵循eslint格式美化

  "editor.tabSize": 2,
  "files.associations": {
    "*.vue": "vue"
  },
  "eslint.codeActionsOnSave": true,
  "eslint.options": {
    "extensions": [".js", ".vue"]
  },
  // "eslint.validate": [
  //     "javascript",{
  //         "language": "vue",
  //         "autoFix": true
  //     },"html",
  //     "vue"
  // ],
  "search.exclude": {
    "**/node_modules": true,
    "**/bower_components": true,
    "**/dist": true
  },
  "emmet.syntaxProfiles": {
    "javascript": "jsx",
    "vue": "html",
    "vue-html": "html"
  },
"git.confirmSync": false,
  "editor.renderWhitespace": "boundary",
  "editor.cursorBlinking": "smooth",
  "editor.minimap.enabled": true,
  "editor.minimap.renderCharacters": false,
  "window.title": "${dirty}${activeEditorMedium}${separator}${rootName}",
  "editor.codeLens": true,
  "editor.snippetSuggestions": "top",
  "editor.codeActionsOnSave": {
    "source.fixAll.eslint": true
  },
  "[vue]": {
    "editor.defaultFormatter": "esbenp.prettier-vscode"
  },
  "git.enableSmartCommit": true,
  "[jsonc]": {
    "editor.defaultFormatter": "esbenp.prettier-vscode"
  },
  "[javascript]": {
    "editor.defaultFormatter": "esbenp.prettier-vscode"
  },
  "[html]": {
    "editor.defaultFormatter": "esbenp.prettier-vscode"
  },
  "files.autoSave": "onFocusChange",

  "backgroung.enable": true,
  "background.useDefault": false,
  "background.customImages": ["file:///Users/liuqiang/Pictures/7天/1Y1A0798.jpg"],
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
    // "opacity": 0
  },
  "explorer.confirmDelete": false,
  "[json]": {
    "editor.defaultFormatter": "esbenp.prettier-vscode"
  },
  "explorer.confirmDragAndDrop": false,
  "javascript.updateImportsOnFileMove.enabled": "always",
  "vetur.format.defaultFormatterOptions": {

    "js-beautify-html": {
      "wrap_attributes": "force-expand-multiline"
    },
    "prettyhtml": {
      "printWidth": 100,
      "singleQuote": false,
      "wrapAttributes": false,
      "sortAttributes": false
    }
  },
  "node-module-intellisense.modulePaths": [
  
  ],
  "editor.accessibilitySupport": "on",
  "git.autofetch": true
}
```