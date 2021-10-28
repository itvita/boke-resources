---
title: xui-admin API
top: 1
toc: true
recommend: 1 
keywords: categories-github
date: 2019-09-19 22:10:43
thumbnail: https://cdn.jsdelivr.net/gh/itvita/liuqiang@master/boke/peitu/lf4.jpg
tags: vue
categories: ["前端","VUE自定义组件仓库"]
# encrypt: false  #加密
# password: 123456 #此处为文章密码
# abstract: 咦，这是一篇加密文章，好像需要输入密码才能查看呢！
# message: 嗨，请准确无误地输入密码查看哟！
# wrong_pass_message: 不好意思，密码没对哦，在检查检查呢！
# wrong_hash_message: 不好意思，信息无法验证！
---

## 图片上传
### 示例
![](https://cdn.jsdelivr.net/gh/itvita/resources@master/images/20210910175339.png)
### 代码
```html
<template>
  <div>
    <xui-image-upload
      baseUrl="https://norisk-dev-1305901002.cos.ap-chengdu.myqcloud.com/"
      action="http://192.168.1.59:9001/app/company/h5/v1/common/ant/upload"
      :headers="headers"
      v-model="images"
      :maxNum="3"
      ></xui-image-upload
    >
  </div>
</template>
<script>
export default {
  data () {
    return {
      headers: {
        xxx: 'xxxxxxx'
      },
      images: [
        {
          name: '测试1',
          original:
            '20210910/3ec7557b2a0d40a69b58b9f16a7cf2b1.png?imageMogr2/format/tpg',
          path: '20210910/3ec7557b2a0d40a69b58b9f16a7cf2b1.png'
        }
      ]
    }
  },
  mounted () {},
  methods: {}
}
</script>
<style scoped lang="less"></style>

```

### 属性
| 属性   | 说明                    | 类型   | 默认值 |
| ------ | ----------------------- | ------ | ------ |
| baseUrl  | 图片访问跟地址                | String |    |
|action|文件上传地址|String||
|headers|上传header|Object|{}|
|v-model|绑定数据|Array|[]|
|maxNum|最大上传数量|Number|5|
|size|大小限制，单位MB|Number|2|
|accept|限制格式|String|.png, .jpg, .jpeg, .gif|

### 事件
| 事件名称     | 说明               | 回调参数         |
| ------------ | ------------------ | ---------------- |
| done | 上传完成调用 | function(values) |

## ztree树形展示
### 示例
![](https://cdn.jsdelivr.net/gh/itvita/resources@master/images/20210910180104.png)
### 代码
```html
<template>
  <div>
    <xui-ztree ref="ztree" />
  </div>
</template>
<script>
export default {
  components: {},
  data () {
    return {}
  },
  mounted () {
    var zNodes = [
      {
        id: '1',
        areaCode: '110000000000',
        name: '北京市',
        sysCode: '100',
        pId: '0'
      },
      {
        id: '2',
        areaCode: '120000000000',
        name: '天津市',
        sysCode: '101',
        pId: '0'
      },
      {
        id: '3',
        areaCode: '130000000000',
        name: '河北省',
        sysCode: '102',
        pId: '0'
      },
      {
        id: '1-1',
        areaCode: '130000000000',
        name: '河北省',
        sysCode: '102',
        pId: '1'
      }
    ]
    var root = {
      open: true,
      id: 0,
      pId: -1,
      name: '公司根目录',
      icon: 'https://cdn.jsdelivr.net/gh/itvita/liuqiang@master/nage/gongsi.png'
    }
    zNodes.forEach(d => {
      d.icon = 'https://cdn.jsdelivr.net/gh/itvita/liuqiang@master/nage/gongsi.png'
    })
    zNodes.push(root)
    this.$refs.ztree.init(zNodes)
  },
  methods: {}
}
</script>
<style scoped lang="less"></style>

```


### 事件
| 事件名称     | 回调参数         |说明               | 
| ------------ | ------------------ | ---------------- |
| click |  function(values) |点击事件，选中项的数据 |

### 方法
| 方法名称     | 参数               | 说明         |
| ------------ | ------------------ | ---------------- |
| init | 树形简单数据[{id,name,pId}] | 树形初始化 |

## 多选
### 示例
![](https://cdn.jsdelivr.net/gh/itvita/resources@master/images/20210910180900.png)
### 代码
```html
<template>
  <div>
    <xui-multiple-choice
      ref="xMultipleChoice"
      :multiple="true"
      @change="handelChange"
      :dataSource="data"
    />
    <a @click="done">获取选择结果</a>
  </div>
</template>
<script>
export default {
  data () {
    const data = [
      {
        name: '现场管理',
        children: []
      },
      {
        name: '基础管理',
        children: []
      }
    ]
    for (var i = 0; i < data.length; i++) {
      for (var x = 0; x < 10; x++) {
        data[i].children.push({
          id: i + '' + x,
          name: i + '-测试数据' + x
        })
      }
    }
    return {
      data: data
    }
  },
  mounted () {},
  methods: {
    /**
     * @Time: 2021-07-23 23:05:02
     * @author: liu.q [916000612@qq.com]
     * @des:  item 当前操作项, type【'selected'选择，'unselected'取消选择】, selectIds 最终结果id数组
     * */
    handelChange ({ item, type, selectIds }) {
      console.log(item, type, selectIds)
    },
    /**
     * @Time: 2021-07-23 23:06:14
     * @author: liu.q [916000612@qq.com]
     * @des:  获取最终选择结果
     * */
    done () {
      /* 获取选中ID */
      const selectIds = this.$refs.xMultipleChoice.getSelectIds()
      console.log(selectIds)
      /* 获取选中对象 */
      const selectObjects = this.$refs.xMultipleChoice.getSelectObjects()
      console.log(selectObjects)
    }
  }
}
</script>
<style scoped lang="less"></style>
```

### 属性
| 属性   | 说明                    | 类型   | 默认值 |
| ------ | ----------------------- | ------ | ------ |
| multiple  | 是否多选                | Boolean |  false  |
|dataSource|数据源，两级数组[{id,name,children}]|Array||

### 事件
| 事件名称     |回调参数         | 说明               | 
| ------------ | ------------------ | ---------------- |
| change | function({ item, type, selectIds }) | 选项改变，item 当前操作项, type【'selected'选择，'unselected'取消选择】, selectIds 最终结果id数组 


### 方法
| 方法名称     | 参数               | 说明         |
| ------------ | ------------------ | ---------------- |
| getSelectIds |  | 获取选中ID |
| getSelectObjects |  | 获取选中对象 |

## 描述列表
### 示例
![](https://cdn.jsdelivr.net/gh/itvita/resources@master/images/20210917094248.png)
### 代码
```html
<template>
<div>
  <xui-descriptions label-width="200px" label="测试标题" >
    斐济电视剧覅哦啊江东四杰佛i啊惊世毒妃
  </xui-descriptions>
  <xui-descriptions label="测试标题" label-width="200px">
    斐济电视剧覅
  </xui-descriptions>
   <xui-descriptions label="测试标题" label-width="200px">
    <div><img src="fidjsif"/></div>
  </xui-descriptions>
</div>
</template>
<script>
export default {
data () {
return {}
},
mounted () {},
methods: {}
}
</script>
<style scoped lang="less"></style>

```


### 属性
| 属性   | 说明                    | 类型   | 默认值 |
| ------ | ----------------------- | ------ | ------ |
| label  | 标题                | String |    |
|label-width|标题宽度，单位px|String|0px|

## 图片预览
### 示例
![](https://cdn.jsdelivr.net/gh/itvita/resources@master/images/20211021113519.png)

![](https://cdn.jsdelivr.net/gh/itvita/resources@master/images/20211021113828.png)

![](https://cdn.jsdelivr.net/gh/itvita/resources@master/images/20211021113549.png)

### 代码

```html
<template>
  <div>
    <xui-image-preview
      :showBtn="true"
      :showName="false"
      width="100px"
      height="100px"
      :baseUrl="baseUrl"
      url="path"
      v-model="ImgList"
    />
  </div>
</template>
<script>
export default {
  data () {
    return {
      baseUrl: 'https://norisk-prod-1305901002.cos.ap-chengdu.myqcloud.com/',
      ImgList: [
        {
          name: '测试',
          path: '20211015/f9cec9d0e43d4edb91c69d5d2b9389b0.jpg'
        },
        {
          name: '测试',
          path: '20211015/f9cec9d0e43d4edb91c69d5d2b9389b0.jpg'
        },
        {
          name: '测试',
          path: '20211015/f9cec9d0e43d4edb91c69d5d2b9389b0.jpg'
        },
        {
          name: '测试',
          path: '20211015/f9cec9d0e43d4edb91c69d5d2b9389b0.jpg'
        },
        {
          name: '测试',
          path: '20211015/f9cec9d0e43d4edb91c69d5d2b9389b0.jpg'
        }
      ]
    }
  },
  mounted () {},
  methods: {}
}
</script>
<style scoped lang="less"></style>

```
### 属性
| 属性   | 说明                    | 类型   | 默认值 |
| ------ | ----------------------- | ------ | ------ |
| v-model(value)  | 数据[{name:xx,url:xx}]                | Array | []   |
|url|url 键名|String|url|
|baseUrl|图片访问跟域名|String|''|
|width|宽|String|100px|
|height|高|String|100px|
|showBtn|是否显示预览 删除按钮|Boolean|false|
|showName|是否显示图片名称|Boolean|false|

### 事件
| 事件名称     |回调参数         | 说明               | 
| ------------ | ------------------ | ---------------- |
| change | function(newData) | 图片列表改变后的数组
| delete | function(newData,delData) | 删除事件，newData删除后的结果，delData删除数据

## 富文本
### 示例
![](https://cdn.jsdelivr.net/gh/itvita/resources@master/images/20211028105103.png)
### 代码
```html
<template>
  <div>
    <xui-editor
      v-model="values"
      @change="handelChange"
      placeholder="输入内容提示文字。。。"
      :action="action"
      :basePath="basePath"
      :height="300"
    />
  </div>
</template>
<script>
export default {
  data () {
    return {
      action: 'https://apis.norisk.com.cn/app/company/v1/common/ant/upload', // 文件上传地址
      basePath: 'https://norisk-prod-1305901002.cos.ap-chengdu.myqcloud.com/', // 文件预览跟地址
      values: '<p>我是默认内容</p>'
    }
  },
  mounted () {},
  methods: {
    handelChange () {
      console.log(this.values)
    }
  }
}
</script>
<style scoped lang="less"></style>
```
### 属性
| 属性   | 说明                    | 类型   | 默认值 |
| ------ | ----------------------- | ------ | ------ |
| v-model(value)  | 数据(html内容)   | String | ''  |
|action|文件上传地址|String|''|
|basePath|图片访问跟路径|String|''|
|placeholder|空内容提示性文字|String|请输入内容...|
|height|高(单位px)|Number|300|

### 事件
| 事件名称     |回调参数         | 说明               | 
| ------------ | ------------------ | ---------------- |
| change | function(newValue) | 内容改变触发