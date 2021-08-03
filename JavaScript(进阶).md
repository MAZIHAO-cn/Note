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

