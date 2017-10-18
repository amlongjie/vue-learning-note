# Vue学习笔记

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

![image.png](http://upload-images.jianshu.io/upload_images/2656062-2e07ccaed737d8b3.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

跳转到这个页面.发现有样例可以下载.

![image.png](http://upload-images.jianshu.io/upload_images/2656062-8e5a73e00ad23aae.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


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

![image.png](http://upload-images.jianshu.io/upload_images/2656062-08bf579e704ef504.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

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
2.  el的值和上面div的id对应.根据写法不难看出就是绑定到id位app的元素(element)上.
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

![image.png](http://upload-images.jianshu.io/upload_images/2656062-426a3afa783761c9.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

所有类型都进行了正确的展示.Ok,入门完成.