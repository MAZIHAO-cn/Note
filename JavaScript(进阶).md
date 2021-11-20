## JavaScript进阶

### 1. API 和 Web API

#### 1.1 API

**API (Application Programming Interface，应用程序编程接口)**是一些预先定义的函数，目的是提供应用程序与开发人员基于某软件或硬件得以访问一组例程的能力，而又无需访问源码，或理解内部工作机制的细节。 

简单理解：**API是给程序员提供的一种工具，以便能更轻松的实现想要完成的功能。**

#### 1.2 Web API

**Web API** 是浏览器提供的一套操作**浏览器功能**和**页面元素**的**API**（BOM和DOM）

现阶段我们主要针对于浏览器讲解常用的API，主要针对浏览器的交互效果。

#### 1.3 API 和 Web API 总结

1. **API是为我们程序员提供的一个接口，帮助我们实现某种功能，我们会使用就可以了，不必纠结内部如何实现**
2. Web API 主要是针对于浏览器提供的接口，主要针对浏览器的交互效果
3. Web API 一般都有输入和输出（函数的传参和返回值），Web API很多都是方法（函数）
4. 学习Web API 可以结合前面学习内置对象方法的思路学习

### 2. DOM

#### 2.1 DOM简介

##### 2.1.1什么是DOM

文档对象类型（Document Object Model，简称**DOM**），是W3C组织推荐的处理可扩展标记语言（HTML或者XML）的标准**编程接口**。

W3C已经定义了一系列的DOM接口，通过这些DOM接口可以改变网页的内容、结构和样式。

##### 2.1.2 DOM树

<a href="https://imgtu.com/i/f9rggS"><img src="https://z3.ax1x.com/2021/08/02/f9rggS.png" alt="f9rggS.png" border="0" style="zoom:60%;" /></a>

+ 文档：一个页面就是一个文档，DOM中使用document表示
+ 元素：页面中的所有标签都是元素，DOM中使用element表示
+ 节点：网页中的所有内容都是节点（标签、属性、文本、注释等），DOM中使用node表示

**DOM把以上内容都看作是对象**

#### 2.2获取元素

##### 2.2.1如何获取页面元素

DOM在我们实际开发中主要用来操作元素

我们如何来获取页面中的元素呢？

获取页面中的元素可以使用以下几种方式：

+ 根据ID获取
+ 根据标签名获取
+ 通过HTML5新增的方法获取
+ 特殊元素获取

##### 2.2.2根据 ID 获取

使用getElementById()方法可以获取带有ID的元素对象。

因为我们文档页面从上往下加载，所以先得有标签 所以我们script写到标签的下面

参数：id是大小写敏感的字符串	带单引号

返回的是一个元素对象

console.dir() 打印我们返回的元素对象  更好的查看里面的属性和方法

```html
  <div id="time">2021-08-01</div>
  <script>
    var element = document.getElementById('time');
    console.log(element);     // print: <div id="time">2021-08-01</div>
    console.log(typeof element);  // print: object
    console.dir(element);
  </script>
```

##### 2.2.3根据标签名获取

使用getElementsByTagName() 方法可以返回带有指定标签名的**对象的集合**

返回的是  获取过来元素对象的集合  以伪数组的形式存储的

**注意：**

1. **因为得到的是一个对象的集合，所以我们想要操作里面的元素就需要遍历。**
2. **得到元素对象是动态的**
3. 如果页面中只有一个 li ，返回的还是伪数组的形式
4. 如果页面中没有这个元素，返回的空的伪数组的形式

```html
  <ul>
    <li>知否知否，应是等你好久1</li>
    <li>知否知否，应是等你好久2</li>
    <li>知否知否，应是等你好久3</li>
    <li>知否知否，应是等你好久4</li>
    <li>知否知否，应是等你好久5</li>
  </ul>
  <script>
    var li = document.getElementsByTagName('li');
    console.log(li);
    console.log(li[0]); // print: <li>知否知否，应是等你好久1</li>
    // 我们想要依次打印里面的元素对象我们可以采取遍历的方式
    for (var i = 0; i < li.length; i++) {
      console.log(li[i]);
    }
  </script>
```

还可以获取某个元素(父元素)内部所有指定标签名的字元素

注意：父元素必须是**单个对象(必须指明是哪一个元素对象)**。获取的时候不包括父元素自己。

```html
  <ul>
    <li>知否知否，应是等你好久1</li>
    <li>知否知否，应是等你好久2</li>
    <li>知否知否，应是等你好久3</li>
    <li>知否知否，应是等你好久4</li>
    <li>知否知否，应是等你好久5</li>
  </ul>
  <ol id="ol">
    <li>生僻字</li>
    <li>生僻字</li>
    <li>生僻字</li>
    <li>生僻字</li>
    <li>生僻字</li>
  </ol>
  <script>
    var ol = document.getElementsByTagName('ol');
    var lis = ol[0].getElementsByTagName('li');
    console.log(lis);
    var Ol = document.getElementById('ol');
    console.log(Ol.getElementsByTagName('li'));
  </script>
```

##### 2.2.4 H5新增获取元素

###### 2.2.4.1 getElementByClassName()

```
1. document.getElementByClassName('类名');	// 根据类名返回元素对象集合
```

```html
  <div class="box">盒子</div>
  <div class="box">盒子</div>
  <div id="nav">
    <ul>
      <li>首页</li>
      <li>产品</li>
    </ul>
  </div>
  <script>
    var boxes = document.getElementsByClassName('box');
    console.log(boxes);
  </script>
```

###### 2.2.4.2 querySelector()

```
2. document.querySelector('选择器');				 // 根据指定选择器返回第一个元素对象	切记 里面的选择器需要加符号
```

```html
  <div class="box">盒子1</div>
  <div class="box">盒子2</div>
  <div id="nav">
    <ul>
      <li>首页</li>
      <li>产品</li>
    </ul>
  </div>
  <script>
    var firstBox = document.querySelector('.box');
    console.log(firstBox);
    var nav = document.querySelector('#nav');
    console.log(nav);
    var li = document.querySelector('li');
    console.log(li);
  </script>
```

###### 2.2.4.3 querySelectorAll()

```
3. document.querySelectorAll('选择器');		  // 根据指定选择器返回
```

```html
<div class="box">盒子1</div>
<div class="box">盒子2</div>
<div id="nav">
  <ul>
    <li>首页</li>
    <li>产品</li>
  </ul>
</div>
<script>
  var allBox = document.querySelectorAll('.box');
  console.log(allBox);
  var lis = document.querySelectorAll('li');
  console.log(lis);
</script>
```

##### 2.2.5获取特殊元素( body , html )

###### 2.2.5.1获取body元素

```html
<script>
  var bodyEle = document.body;
  console.log(bodyEle);
  console.dir(bodyEle);
</script>
```

###### 2.2.5.2获取html元素

```html
<script>
  var htmlEle = document.documentElement;
  console.log(htmlEle);
</script>
```

#### 2.3事件基础

##### 2.3.1事件概述

JavaScript使我们有能力创建动态页面，而事件是可以被JavaScript侦测到的行为。

简单理解：触发 --- 响应机制

网页中的每一个元素都可以产生某些可以触发JavaScript的事件，例如，我们可以在用户点击某按钮时产生一个事件，然后去执行某些操作。

##### 2.3.2事件三要素

+ 事件源  

  事件被触发的对象

+ 事件类型  

  如何触发 什么事件

+ 事件处理程序

  通过一个函数赋值的方式 完成

```html
<button id="btn">唐伯虎</button>
<script>
  // 1. 事件是由三部分组成 事件源 事件类型 事件处理程序   我们也称之为事件三要素
  // (1) 事件源 事件被触发的对象  谁  按钮
  var btn = document.getElementById('btn');
  // (2) 事件类型 如何触发 什么事件 比如鼠标点击(onclick) 还是 鼠标经过 还是 键盘按下
  // (3) 事件处理程序 通过一个函数赋值的方式 完成
  btn.onclick = function() {
    alert('点秋香');
  }
</script>
```

##### 2.3.3执行事件的步骤

1. 获取事件源
2. 注册事件（绑定事件）
3. 添加时间处理程序（采取函数赋值形式）

```html
<div>123</div>
<script>
  // 1. 获取事件源
  var div = document.querySelector('div');
  // 2. 绑定事件 注册事件
  div.onclick = function() {
    console.log('我被选中了');
  }
</script>
```

###### 2.3.3.1常用的鼠标事件

| 鼠标事件    | 触发条件         |
| ----------- | ---------------- |
| onclick     | 鼠标点击左键触发 |
| onmouseover | 鼠标经过触发     |
| onmouseout  | 鼠标离开触发     |
| onfocus     | 获取鼠标焦点触发 |
| onblur      | 失去鼠标焦点触发 |
| onmousemove | 鼠标移动触发     |
| onmouseup   | 鼠标弹起触发     |
| onmousedown | 鼠标按下触发     |

##### 2.3.4分析事件三要素

下拉菜单三要素

关闭广告三要素

#### 2.4操作元素

JavaScript的DOM操作可以改变网页内容、结构和样式，我们可以利用DOM操作元素来改变元素里面的内容、属性等。注意以下都是属性

##### 2.4.1改变元素内容

```
element.innerText
```

从起始位置到终止位置的内容，但他去除html标签，同时空格和换行也会去掉

```html
<head>
  <meta charset="UTF-8">
  <meta http-equiv="X-UA-Compatible" content="IE=edge">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <link rel="stylesheet" href="css/demo.css">
  <title>Document</title>
  <style>
    div,
    p {
      width: 300px;
      height: 30px;
      line-height: 30px;
      color: #fff;
      background-color: pink;
    }
  </style>
</head>
<body>
  <button>显示当前系统时间</button>
  <div>某个时间</div>
  <p>123</p>
  <script>
    // 当我们点击了按钮，div里面的文字会发生变化
    // 1. 获取元素
    var btn = document.querySelector('button');
    var div = document.querySelector('div');

    // 2. 注册事件  
    btn.onclick = function() {
      div.innerText = getDate();
    }
    function getDate() {
      // 格式化日期	年月日
      var date = new Date();
      // 我们写一个 2021年 7月 29日 星期三
      var year = date.getFullYear();
      var month = date.getMonth() + 1;
      var dates = date.getDate();
      var day = date.getDay();
      var arr = ['星期日', '星期一', '星期二', '星期三', '星期四', '星期五', '星期六', ];
      return '今天是' + year + '年' + month + '月' + dates + '日' + arr[day];
    }
    // 我们元素可以不用添加事件
    var p = document.querySelector('p');
    p.innerText = getDate();
  </script>
</body>
```



```
element.innerHTML
```

从起始位置到终止位置的内容，包括html标签，同时保留空格和换行



innerText 跟 innerHTML 的区别：

```html
    <div></div>
    <p>
        我是文字
        <span>123</span>
    </p>
    <script>
        // 1. innerText 不识别html标签 非标准  去除空格和换行
        var div = document.querySelector('div');
        div.innerText = '<strong>今天是：</strong>2021'; // print: <strong>今天是：</strong>2021
        // 2. innerHTML 识别html标签 W3C标准  保留空格和换行
        div.innerHTML = '<strong>今天是：</strong>2021'; // print: 今天是：2021
        // 这两个属性是可读写的 可以获取元素里面的内容
        var p = document.querySelector('p');
        console.log(p.innerText); // print: 我是文字 123
        console.log(p.innerHTML); // print: 
                                        //   我是文字
                                        // <span>123</span>
    </script>
```

##### 2.4.2常用元素的属性操作

```
1. innerText、innerHTML
2. src、href
3. id、alt、title
```

##### 2.4.2-1 案例：分时显示不同图片，显示不同问候语

根据不同的时间，页面显示不同图片，同时显示不同问候语

如果上午时间打开页面，显示上午好，显示上午图片；

如果下午时间打开页面，显示下午好，显示下午图片；

如果晚上时间打开页面，显示晚上好，显示晚上图片。

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <link rel="stylesheet" href="css/demo.css">
    <title>Document</title>
    <style>
        img {
            width: 300px;
        }
    </style>
</head>
<body>
    <img src="image/s.jpg" alt="">
    <div>亲，上午好</div>
    <script>
        // 根据系统不同时间来判断，所以需要用到日期内置对象
        // 利用多分支语句来设置不同的图片
        // 需要一张图片，并且根据时间修改图片，就需要用到操作元素src属性
        // 需要一个div元素，显示不同问候语，修改元素内容即可
        // 1. 获取元素
        var img = document.querySelector('img');
        var div = document.querySelector('div');
        // 2. 得到当前的小时数
        var date = new Date();
        var h = date.getHours();
        // 3. 判断小时数，改变图片和文字信息
        if (h > 6 && h <= 12) {
            img.src = 'image/s.jpg';
            div.innerHTML = '亲，上午好';
        } else if (h > 12 && h <= 18) {
            img.src = 'image/x.jpg';
            div.innerHTML = '亲，下午好';
        } else {
            img.src = 'image/w.jpg';
            div.innerHTML = '亲，晚上好';
        }
    </script>
</body>
</html>
```

##### 2.4.3 表单元素的属性操作

利用DOM可以操作如下表单元素的属性：

```
type、value、checked、selected、disabled
```

```html
<body>
    <button>按钮</button>
    <input type="text" value="输入内容">
    <script>
        // 1. 获取元素
        var btn = document.querySelector('button');
        var input = document.querySelector('input');
        // 2. 注册事件  处理程序
        btn.onclick = function() {
            // input.innerHTML = '点击了'; //这个是普通盒子 比如 div 标签里面的内容
            // 表单里面的值 文字内容是通过 value 来修改的
            input.value = '被点击了';
            // 如果想要某个表单被禁用 不能再点击 disabled 我们想要这个按钮button被禁用
            // btn.disabled = true; 
            this.disabled = true;
            // this 指向的是事件函数的调用者 btn
        }
    </script>
</body>
```

##### 2.4.3-1 案例：仿京东显示密码

点击按钮将密码框切换为文本框，并可以查看密码明文。

```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <link rel="stylesheet" href="css/demo.css">
    <title>Document</title>
    <style>
        .box {
            position: relative;
            width: 400px;
            border-bottom: 1px solid #ccc;
            margin: 100px auto;
        }
        
        .box input {
            width: 370px;
            height: 30px;
            border: 0;
            outline: none;
        }
        
        .box img {
            position: absolute;
            top: 2px;
            right: 2px;
            width: 24px;
        }
    </style>
</head>

<body>
    <div class="box">
        <label for="">
            <img src="image/close.png" alt="" id="eye">
        </label>
        <input type="password" name="" id="pwd">
    </div>
    <script>
        // 1. 获取元素
        var eye = document.getElementById('eye')
        var pwd = document.getElementById('pwd')

        // 2. 注册事件  处理程序
        var flag = 0;
        eye.onclick = function() {
            // 点击一次之后，flag一定要发生变化
            if (flag == 0) {
                this.src = 'image/open.png';
                pwd.type = 'text';
                flag = 1;  // 赋值操作
            } else {
                this.src = 'image/close.png';
                pwd.type = 'password';
                flag = 0;
            }
        }
    </script>
</body>

</html>
```

##### 2.4.4 样式属性操作

我们可以通过JS修改元素的大小、颜色、位置等样式。

```
1. element.style			行内样式操作
2. element.className	类名样式操作
```

```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <link rel="stylesheet" href="css/demo.css">
    <title>Document</title>
    <style>
        div {
            width: 200px;
            height: 200px;
            background-color: pink;
        }
    </style>
</head>

<body>
    <div></div>
    <script>
        // 1. 获取元素
        var div = document.querySelector('div');
        // 2. 注册事件 处理程序
        var flag = 0
        div.onclick = function() {
            if (flag == 0) {
                this.style.backgroundColor = 'purple';
                this.style.width = '250px';
                flag = 1;
            } else {
                this.style.backgroundColor = 'pink';
                this.style.width = '200px';
                flag = 0;
            }
        }
    </script>
</body>

</html>
```

##### 2.4.4-1 案例：淘宝点击关闭二维码

当鼠标点击二维码关闭按钮的时候，则关闭整个二维码。

```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <link rel="stylesheet" href="css/demo.css">
    <title>Document</title>
    <style>
        img {
            width: 200px;
        }
    </style>
</head>

<body>
    <div class="box">
        淘宝二维码
        <img src="image/tao.jpg" alt="">
        <i class="close_btn">✖️</i>
    </div>
    <script>
        // 1. 获取元素
        var btn = document.querySelector('.close_btn');
        var box = document.querySelector('.box');
        // 2. 注册事件 处理程序
        btn.onclick = function() {
            box.style.display = 'none';
        }
    </script>
</body>

</html>
```

##### 2.4.4-2 案例：循环精灵图背景

可以利用for循环设置一组元素的精灵图背景

```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <link rel="stylesheet" href="css/demo.css">
    <title>Document</title>
    <style>
        .box ul {
            list-style: none;
        }
        
        .box {
            width: 300px;
            margin: 100px auto;
        }
        
        .box li {
            float: left;
            width: 24px;
            height: 24px;
            background-color: pink;
            margin: 15px;
            background: url(image/sprite.png) no-repeat;
        }
    </style>
</head>

<body>
    <div class="box">
        <ul>
            <li></li>
            <li></li>
            <li></li>
            <li></li>
            <li></li>
            <li></li>
            <li></li>
            <li></li>
            <li></li>
            <li></li>
            <li></li>
            <li></li>
        </ul>
    </div>
    <script>
        // 1. 获取元素 所有的小li
        var lis = document.querySelectorAll('li')
        for (var i = 0; i < lis.length; i++) {
            // 让索引号乘以44就是每个li的背景y坐标 index就是我们的y坐标
            var index = i * 44;
            lis[i].style.backgroundPosition = '0 -' + index + 'px';
        }
    </script>
</body>

</html>
```

##### 2.4.4-3 案例：显示隐藏文本框内容

当鼠标点击文本框时，里面的默认文字隐藏，当鼠标离开文本框时，里面的文字显示。

```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <link rel="stylesheet" href="css/demo.css">
    <title>Document</title>
    <style>
        input {
            color: #999;
        }
    </style>
</head>

<body>
    <input type="text" value="" placeholder="手机">
    <script>
        // 1. 获取元素
        var text = document.querySelector('input');
        // 2. 注册事件 获得焦点事件 onfocus
        text.onfocus = function() {
            // console.log('得到了焦点');
            this.placeholder = '';
            // 获得焦点需要把文本框里面的文字颜色变黑
            this.style.color = '#333';
        }

        // 3. 注册事件 失去焦点事件 onblur
        text.onblur = function() {
            // console.log('失去了焦点');
            this.placeholder = '手机';
        }
    </script>
</body>

</html>
```

##### 2.4.5 通过className更改元素样式

```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <link rel="stylesheet" href="css/demo.css">
    <title>Document</title>
    <style>
        .first {
            width: 100px;
            height: 100px;
            background-color: pink;
        }
        
        .change {
            width: 100px;
            height: 100px;
            background-color: purple;
            color: #fff;
            font-size: 25px;
            margin-top: 100px;
        }
    </style>
</head>

<body>
    <div class="first">文本</div>
    <script>
        var test = document.querySelector('div');
        var flag = 0;
        test.onclick = function() {
            // 1. 使用 element.style 获得修改元素样式 如果样式比较少 或者 功能简单的情况下使用
            // this.style.backgroundColor = 'purple';
            // this.style.color = '#fff';
            // this.style.fontSize = '25px';
            // this.style.marginTop = '100px';

            // 让我们当前元素的类名改为了 change
            // 2. 使用 element.className 获得修改元素样式 适用于样式比较多 或者 功能复杂的情况
            // this.className = 'change';

            // 3. 如果想要保留原先的类名 我们可以这么做
            // this.className = 'first change';
            if (flag == 0) {
                this.className = 'change';
                flag = 1;
            } else {
                this.className = 'first';
                flag = 0;
            }
        }
    </script>
</body>

</html>
```

##### 2.4.6 操作元素总结

操作元素是DOM核心内容

##### 2.4.6-1 作业

1.世纪佳缘 用户名 显示隐藏内容

2.京东关闭广告（直接隐藏即可）

3.新浪下拉菜单（微博即可）

4.开关灯案例（见素材）

```html
<button id="btn">开关灯</button>
<script>
  var btn = document.getElementById('btn');
  var flag = 0;
  btn.onclick = function() {
    if (flag == 0) {
      document.body.style.backgroundColor = 'black';
      flag = 1;
    } else {
      document.body.style.backgroundColor = '#fff';
      flag = 0;
    }
  }
</script>
```

