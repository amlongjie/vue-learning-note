## Vue.js简介

### 1. Vue.js是什么

Vue.js (读音 /vjuː/，类似于 view) 是一套构建用户界面的渐进式框架。
与其他重量级框架不同的是，Vue 采用自底向上增量开发的设计。
Vue 的核心库只关注视图层，它不仅易于上手，还便于与第三方库或既有项目整合。
另一方面，当与单文件组件和 Vue 生态系统支持的库结合使用时，Vue 也完全能够为复杂的单页应用程序提供驱动。

一句话总结:**简单好用的前端框架.**

参考:[官网](https://cn.vuejs.org/)

### 2. Hello World

学习一个技术,最好的入门方法,一定是去官网找入门程序.

一进入官网就看到了起步.

![](http://upload-images.jianshu.io/upload_images/2656062-2e07ccaed737d8b3.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

跳转到这个页面.发现有样例可以下载.

![](http://upload-images.jianshu.io/upload_images/2656062-8e5a73e00ad23aae.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


下载后打开代码.

``` html
<!DOCTYPE html>
<html>
<head>
    <title>My first Vue app</title>
    <script src="https://unpkg.com/vue"></script>
</head>
<body>
<div id="app">
    {{ message }}
</div>

<script>
    var app = new Vue({
        el: '#app',
        data: {
            message: 'Hello Vue!'
        }
    })
</script>
</body>
</html>
```



打开浏览器

![](http://upload-images.jianshu.io/upload_images/2656062-08bf579e704ef504.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/600)

我们再回头看代码.重点关注下面几行.

```
var app = new Vue({
        el: '#app',
        data: {
            message: 'Hello Vue!'
        }
    })
```

1.  创建了一个Vue对象.
2.  el的值和上面div的id对应.根据写法不难看出就是绑定到id为app的元素(element)上.
3.  data字段里有message,也不难看出和div内部的{{ message }}.而这个大括号的模板语法.在很多后端语言都有.

根据这个Hello World,我们可以看出.Vue确实看起来比较简单,好写.不像angular那样门槛叫高.一上来就比较复杂.

### 3. Go Further

通过Hello World程序,我们已经对Vue有了基本的了解.那接下来,我们改一改Vue的Hello World.
尝试多种不同数据类型的绑定.看看会展示成什么样子.

代码:

``` html
<!DOCTYPE html>
<html>
<head>
    <title>My first Vue app</title>
    <script src="https://unpkg.com/vue"></script>
</head>
<body>
<div id="app">
    {{ message }} <br/>
    {{ messageId }} <br/>
    {{ messageArr }} <br/>
    {{ messageObj }} <br/>
</div>

<script>
    var app = new Vue({
        el: '#app',
        data: {
            message: 'Hello Vue!', // str
            messageId: 13, // int
            messageArr: ["Hello", "Vue", "From", "Arr"],
            messageObj: {
                id: 1,
                message: "Hello Vue From Obj"
            }
        }
    })
</script>
</body>
</html>
```

展示:

![](http://upload-images.jianshu.io/upload_images/2656062-426a3afa783761c9.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/600)

所有类型都进行了正确的展示.Ok,入门完成.

## Vue指令

指令 (Directives) 是带有 v- 前缀的特殊属性。指令属性的值预期是单个 JavaScript 表达式 (v-for 是例外情况，稍后我们再讨论)。指令的职责是，当表达式的值改变时，将其产生的连带影响，响应式地作用于 DOM.

一句话: **增强Html的能力,类似JSTL**

关于指令由于时间有限.大致浏览了一下官网.挑几个入门必备的来记录一下.剩下的遇到了再去查官网.


### 1. 条件指令 v-if

代码

``` html
<div id="app">
    <p v-if="yes">你可以看到这一条</p>
    <p v-if="no">你看不到这一条</p>
</div>

<script>
    var app = new Vue({
        el: '#app',
        data: {
            yes: true,
            no : false,
        }
    })
</script>
```
浏览器展示

![](http://upload-images.jianshu.io/upload_images/2656062-2a26962d34bbaa05.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/600)

看看实际展示的Html源码

![](http://upload-images.jianshu.io/upload_images/2656062-9efa774d5cbbc66a.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/600)

结论: **v-if 根据条件来判断是否需要渲染这个元素**

### 2. 循环指令 v-for

**遍历数组**

代码
``` html
<div id="app">

    <ul>
        <li v-for="(message,index) in messageArr">
            {{index}} - {{ message }}
        </li>
    </ul>

</div>

<script>
    var app = new Vue({
        el: '#app',
        data: {
            messageArr : ["Hello", "Vue", "Js"],
        }
    })
</script>
```

浏览器展示

![image.png](http://upload-images.jianshu.io/upload_images/2656062-1a94c7614175435b.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/600)

提醒: **传统的后端语言遍历都是(key,value).在Vue中是(value,key)**

**遍历对象**

代码
```
<div id="app">
    <ul>
        <li v-for="(value, key) in person">
            {{ key }} - {{ value }}
        </li>
    </ul>
</div>

<script>
    var app = new Vue({
        el: '#app',
        data: {
            person: {id: 1, name : "peter", age : 12}
        }
    })
</script>
```

浏览器展示

![](http://upload-images.jianshu.io/upload_images/2656062-bf8ed090e941f5c8.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/600)

和数组一样.没什么问题.

### 3. 双向数据绑定指令 v-model

个人理解.双向数据绑定的含义是指,模型数据改变会改变视图,而视图数据改变,也会改变模型数据.

代码
```
<div id="app">
    <h1>{{ message }}</h1>
    <input v-model="message" placeholder="edit me">
</div>

<script>
    var app = new Vue({
        el: '#app',
        data: {
            message: ""
        }
    })
</script>
```

浏览器展示

![](http://upload-images.jianshu.io/upload_images/2656062-c86d506f425a55fa.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/600)

### 4. 绑定事件 v-on

使用最简单的click and alter来测试功能

代码
``` html
<div id="app">
    <button v-on:click="doAlert('Hello Vue')">click me</button>
</div>

<script>
    var app = new Vue({
        el: '#app',
        methods : {
            doAlert: function (message) {
                alert(message);
            }
        }
    })
</script>
```

浏览器

![](http://upload-images.jianshu.io/upload_images/2656062-19c950bd001d7e43.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/600)

绑定事件,也很简单.

官网对指令还有更多的介绍.可以去参考.[一键跳转到文档](https://cn.vuejs.org/v2/guide)

## 账户管理功能

根据前面学习的知识点,实现一个简单的账户管理功能.效果图如下

![](http://upload-images.jianshu.io/upload_images/2656062-b5e810eb2455fd97.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1000)



## Github
[代码一键直达](https://github.com/amlongjie/vue-learning-note)