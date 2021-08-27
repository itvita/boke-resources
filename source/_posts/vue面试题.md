---
title: vue面试题
categories: ["前端","VUE"]
toc: true
recommend: 1
uniqueId: '2021-08-27 03:15:00/vue面试题.html'
date: 2021-08-27 11:15:00
thumbnail: https://cdn.jsdelivr.net/gh/itvita/resources@master/images/20210827111747.jpeg
tags: vue
keywords: vue
---

# ***三更灯火五更鸡，正是男儿读书时\*。**

### 基础面试题

- v-if和v-show的区别
> v-show是使用display:none的特性。控制元素的显示和隐藏，元素节点已创建  
v-if 是通过控制dom的创建和销毁来打到显示隐藏，如果频繁切换dom就不适合用
- 为何v-for中要用key
> 在列表重新渲染的时候，会有一个就地复用策略;列表数据修改的时候,他会根据key值去判断某个值是否修改,如果修改,则重新渲染这一项,否则复用之前的元素。
- v-for和v-if能一起使用吗？
> v-for和v-if同时使用时，有一个先后运行的优先级，v-for比v-if的优先级更高，这就说明在v-for的每次循环运行中每一次都会调用v-if的判断，所以不推荐v-if和v-for在同一个标签内同时使用。
- vue的生命周期
    - created和mounted的区别
    - 父子组件的生命周期是什么样的一个执行顺序
> vue的声明周期分为三个阶段:  
挂载阶段：(beforeCreate,  created,  beforeMount,  mounted)created阶段只创建了vue的实例，dom元素还未渲染。mounted阶段dom已经渲染完成  
更新阶段：(beforeUpdate, updated)  
销毁阶段：(beforeDestroy, destroyed) 如果在组件中使用的有自定义事件，要在beforeDestroy中及时解绑，因为自定义事件会造成内存泄漏，销毁阶段主要是解绑自定义事件，清除定时器、监听、销毁子组件等  
父子组件生命周期的执行顺序：父created----->子created---->子mounted---->父mounted  销毁时子destroyed---->父destoryed
- vue组件是如何通讯？
> 父子组件是定义props属性和$emit事件进行通讯，兄弟组件和其他组件通讯可以通过自定义事件的方式来进行通讯(或者是用vuex状态管理器)，组件销毁要及时解绑自定义事件，防止内存泄漏
- computed和watch的区别？
> computed是一个计算属性。具有缓存，页面刷新页面会返回之前的执行结果不会再次执行计算函数  
watch是个监听属性。可以监听props，$emit或本组件的值执行的异步操作，无缓存，页面重新渲染时值不变化也会执行，对象的深度监听用deep: true属性，对象立即监听用immediate： true
- 怎样解决vuex页面刷新数据丢失问题?
> 配合使用缓存  
1.在app.vue的created方法中读取sessionstorage中的数据存储在store中，此时用vuex.store的replaceState方法，替换store的根状态  
2.在beforeunload方法中将store.state存储到sessionstorage中。
```
//在页面加载时读取sessionStorage里的状态信息
if (sessionStorage.getItem("store") ) {
    this.$store.replaceState(Object.assign({}, this.$store.state,JSON.parse(sessionStorage.getItem("store"))))
}

//在页面刷新时将vuex里的信息保存到sessionStorage里
window.addEventListener("beforeunload",()=>{
    sessionStorage.setItem("store",JSON.stringify(this.$store.state))
})

```
- vuex的属性有哪些?(state、getters、mutations、actions、modules)
- vuex在那个属性中处理异步函数?action
    - 有两个action，分别是actionA和actionB，其内都是异步操作，在actionB要提交actionA，需在actionA处理结束再处理其它操作，怎么实现？
 >利用ES6的async和await来实现。 
```
actions:{
    async actionA({commit}){
        //...
    },
    async actionB({dispatch}){
        await dispatch ('actionA')//等待actionA完成
        // ... 
    }
}
```
-


### 高级面试题

#### 自定义v-model
``` 

```
##### $nextTick $refs
```
1.vue是异步渲染
2.data数据更新之后不会立即渲染dom
3.$nextTick会在Dom渲染完成只有触发，可以获取最新的dom节点
在组件上面定义ref 可以通过$refs获取dom元素节点
```
##### slot 插槽
```
1.插槽就是想要把父组件的值带到子组件
2.作用域插槽
3.具名插槽
```
##### 动态、异步组件
```

```
##### keep-alive
```
1.用于tab切换
```
##### mixin
```
1.多个组件有相同的逻辑抽离出来
存在的问题
-变量来源不明确，会不便于阅读
-当一个组件引用多个mixin时，可能会造成命名冲突
-mixin和组件存在多对多的关系，复杂度较高
```

## css水平、垂直居中的写法，请至少写出4种？

> 这题考查的是css的基础知识是否全面，所以平时一定要注意多积累

*水平居中*

- 行内元素: `text-align: center`
- 块级元素: `margin: 0 auto`
- position:absolute +left:50%+ transform:translateX(-50%)
- `display:flex + justify-content: center`

*垂直居中*

- 设置line-height 等于height
- position：absolute +top:50%+ transform:translateY(-50%)
- `display:flex + align-items: center`
- display:table+display:table-cell + vertical-align: middle;

## 用js递归的方式写1到100求和？

> 递归我们经常用到，vue在实现双向绑定进行数据检验的时候用的也是递归，但要我们面试的时候手写一个递归，如果对递归的概念理解不透彻，可能还是会有一些问题。

```text
function add(num1,num2){
	var num = num1+num2;
        if(num2+1>100){
	 return num;
	}else{
	  return add(num,num2+1)
        }
 }
var sum =add(1,2);         
```

## 如何中断ajax请求？

一种是设置超时时间让ajax自动断开，另一种是手动停止ajax请求，其核心是调用XML对象的abort方法，ajax.abort()

## 说一下闭包？

闭包的实质是因为函数嵌套而形成的作用域链

闭包的定义即：函数 `A` 内部有一个函数 `B`，函数 `B` 可以访问到函数 `A` 中的变量，那么函数 `B` 就是闭包

## export和export default的区别？

使用上的不同

```text
export default  xxx
import xxx from './'

export xxx
import {xxx} from './'
```

