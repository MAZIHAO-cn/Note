# JavaScript黑马笔记

脚本语言：不需要编译，运行过程中由js解释器（js引擎）逐行来进行解释并执行。

现在也可以基于node.js技术来进行服务器端编程。

### 1.4 浏览器执行JS

浏览器分为两部分：渲染引擎和JS引擎

渲染引擎：用来解析HTML和CSS，俗称内核，比如谷歌浏览器的blink，老版本的webkit。

JS引擎：也称为JS解释器。用来读取网页中的JavaScript代码，对其处理后运行，比如chrome浏览器的V8。



### 2.1 JS注释

#### 1.单行注释

```js
//	...Code...
```

#### 2.多行注释

```js
/*
	...Code_one...
	...Code_two...
	......
*/
```



### 2.2 输入输出语句

#### 1.弹出警示框

```js
alert(msg);
```

#### 2.打印输出

```js
console.log(msg);
```

#### 3.弹出输入框，用户可以输入

```js
prompt(info);
```



### 3.1 变量

#### 3.1.1变量在内存中的存储

本质：变量是程序在内存中申请的一块用来存放数据的空间。

#### 3.1.2变量的使用

变量在使用时分为两步：1、声明变量		2、赋值

##### 	1、声明变量

```js
var age;
```

##### 	2、赋值

```js
age = 18;
```

##### 	3、变量的初始化

```js
var age = 18;
```

##### 	4.1、案例：变量的使用

有个叫卡卡西的人在旅店登记的时候前台让他填一张表，这张表里的内容要存到电脑上，表中的内容有：姓名、年龄、邮箱、家庭住址和工资，存储之后需要把这些信息显示出来，所显示的内容如下：

我叫旗木卡卡西，我住在火影村，我今年30岁了，我的邮箱是kakasi@itcast.cn，我的工资是2000。

```js
<script>
    var myName = '旗木卡卡西';
    var address = '火影村';
    var age = 30;
    var email = 'kakaxi@itcast.cn';
    var salary = 2000;
    console.log(myName);
    console.log(address);
    console.log(age);
    console.log(email);
    console.log(salary);
  </script>
```

##### 	4.2、案例：变量的使用

1、弹出一个输入框，提示用户输入姓名。

```js
<script>
    var myName = prompt('请输入你的名字');
		//alert(myName);
  </script>
```

2、弹出一个对话框，输出用户刚才输入的姓名。

```js
<script>
    //var myName = prompt('请输入你的名字');
    alert(myName);
  </script>
```



#### 3.1.3变量语法扩展

##### 1、更新变量

```js
<script>
    var name = 'Mr.Ma';
    console.log(name);
    name = '迪丽热巴';
    console.log(name);
  </script>
```

##### 2、同时声明多个变量

```js
<script>
    var age = 18,
        address = '火影村',
        salary = 2000;
  </script>
```

##### 3、声明变量的特殊情况

###### 3.1只声明不赋值，结果是？（Undefined）

```js
<script>
    var sex;
    console.log(sex); //结果：undefined
  </script>
```

###### 3.2不声明不赋值，直接使用，结果是？（会报错）

```js
<script>
    console.log(tel);	//结果：Uncaught ReferenceError: tel is not defined
  </script>
```

###### 3.3不声明直接赋值，结果是？（110）

```js
<script>
  	qq = 110;
  	console.log(qq);	//结果：110
	</script>
```

#### 3.1.4变量命名规范

由字母、数字、下划线、美元符号组成

严格区分大小写

不能以数字开头

不能是关键字、保留字

变量名必须有意义

遵守驼峰命名法。首字母小写、后面单词的首字母需要大写

##### 3.1.4.1、案例：课堂练习

要求：交换两个变量的值（实现思路：使用一个临时变量temp来用做中间存储）

```js
<script>
    var temp;
    var apple1 = '青苹果';
    var apple2 = '红苹果';
    temp = apple1;
    apple1 = apple2;
    apple2 = temp;
    console.log("apple1 = " + apple1);
    console.log("apple2 = " + apple2);
	</script>
```



### 4.1数据类型

#### 4.1.1数据类型简介

##### 4.1.1.1变量的数据类型

变量是用来存储值的所在处，它们有名字和数据类型。变量的数据类型决定了如何将代表这些值的位存储到计算机的内存中。**JavaScript是一种弱类型或者说动态语言。**这意味着不用提前声明变量的类型，在程序运行的过程中，类型会被自动确定。

```js
<script>
  var num = 100;            //这是数字类型
  var str = 'HelloWorld!';  //这是字符串类型
</script>
```



JavaScript拥有动态类型，同时也意味着相同的变量可用作不同的类型。

```js
<script>
  var x = 6;              //x为数字
  		x = 'HelloWorld';   //x为字符串
</script>
```

##### 4.1.1.2数据类型的分类

###### 1、简单数据类型（基本数据类型）

Number, String, Boolean, Undefined, Null

| 简单数据类型 | 说明                                            | 默认值    |
| ------------ | ----------------------------------------------- | --------- |
| Number       | 数字型：整数型、浮点型，如21，0.1               | 0         |
| String       | 布尔值类型，如true, false，等价于1和0           | false     |
| Boolean      | 字符串类型，如“张三”，js里面字符串都带引号      | ""        |
| Undefined    | var a; 声明了变量a但没有给值，此时a = undefined | undefined |
| Null         | var a = null; 声明了变量a为空值                 | null      |

1⃣️Number

1、在现阶段，JS中八进制前面加0，十六进制前面加0x。

2、JS中数值的最大值和最小值

```js
<script>
  console.log(Number.MAX_VALUE);  //print: 1.7976931348623157e+308
  console.log(Number.MIN_VALUE);  //print: 5e-324
</script>
```

3、数字型三个特殊值

```js
<script>
  console.log(Infinity);            //print: Infinity     无穷大
  console.log(Infinity * 2); 				//print: Infinity     无穷大
  
  console.log(-Infinity);           //print: -Infinity    无穷小
  console.log(-Infinity * 2);       //print: -Infinity    无穷小

  console.log(NaN);                 //print: NaN          非数值
  console.log('HelloWorld' - 10);   //print: NaN          非数值
</script>
```

4、isNaN()

​	用处：用来判断是否是非数字，是非数字返回true，是数字返回false。

```js
<script>
  console.log(isNaN(12));   					//print: false  
  console.log(isNaN('12'));						//print: false
  console.log(isNaN('HelloWorld!'));	//print: true
</script>
```



2⃣️String

1、可以是引号中的任意文本，可以是**双引号**，也可以是**单引号**
	  因为HTML标签里面的属性用的是双引号，所以我们JS推荐使用单引号

2、可以单引号嵌套双引号
	  也可以双引号嵌套单引号
	  **(外双内单，外单内双)**

3、字符串转义符

| 转义符 | 解释说明                 |
| ------ | ------------------------ |
| \n     | 换行符，n是newline的意思 |
| \ \    | 斜杠\                    |
| \ '    | '  单引号                |
| \ "    | "  双引号                |
| \t     | tab缩进                  |
| \b     | 空格，b是blank的意思     |

4、案例：弹出网页警示框

msg:   欢迎来到：”德莱联盟！“  
		    我很强！
		    你很菜！

```js
<script>
  alert('欢迎来到："德莱联盟！"\n我很强！\n你很菜！')
</script>
```



5、字符串长度

通过length属性可以获取整个字符串的长度。

```js
<script>
  var str = '你好啊～世界！';
  console.log(str.length);  //print: 7
</script>
```



6、字符串拼接

多个字符串可以用 + 拼接，其拼接方式：**字符串 + 任何类型 = 拼接之后新的字符串**

拼接前会把与字符串相加的任何类型转变成字符串，在拼接成一个新的字符串

​	**+号总结口诀：数值相加，字符相连**

```js
<script>
  console.log('沙漠' + '骆驼');       //print: 沙漠骆驼
  console.log('HelloWorld' + 18);    //print: HelloWorld18
  console.log('HelloWorld' + true);  //print: HelloWorldtrue
  console.log(12 + 12);              //print: 24
  console.log('12' + 12);            //print: 1212
</script>
```



7、字符串加强

我们经常会将字符串和变量来拼接，因为变量可以很方便地修改里面的值

变量是不能添加引号的，因为加引号的变量会变成字符串

如果变量两侧都有字符串拼接，口诀：**“引引加加”**，删掉数字，变量写在中间



8、案例分析：

交互编程的三个基本要素：

​	1.你喜欢我吗？-->	这是**用户输入**

​	2.女孩想了想	-->	这是**程序内部处理**

​	3.最后给你一巴掌  -->	这是**输出结果**

```js
<script>
  var age = prompt('请输入你的年龄');
  var str = '你今年已经'+ age +'岁了。';
  alert(str);
</script>
```



3⃣️Boolean

布尔类型有两个值：true和false，其中true表示真(对)，false表示假(错)。

一个声明后没有被赋值的变量会有一个默认值undefined（如果进行相加或者相连是，注意结果）

一个声明变量给null值，里面存的值为空（学习对象时，我们继续研究null）

```js
<script>
  var flag = true;
  var flag1 = false;
  console.log(flag + 1);    //print: 2
  console.log(flag1 + 1);   //print: 1
</script>
```

4⃣️Undefined和Null

```js
<script>
	var str;
  console.log(str);         //undefined
  var variable = undefined;
  console.log(variable + 'pink'); //print: undefinedpink
  console.log(variable + 1);      //print: NaN  undefined和数字相加 最后结果是NaN
  var space = null;
  console.log(space + 'Hello');   //print: nullHello
  console.log(space + 1);         //print: 1
</script>
```



###### 2、复杂数据类型

Object



#### 4.1.2获取变量数据类型

##### 4.1.2.1获取检测变量的数据类型

typeof可用来获取检测变量的数据类型

```js
<script>
  var num = 100;
  console.log(typeof num);    //print: number
  var str = 'hello';
  console.log(typeof str);    //print: string
  var flag = true;
  console.log(typeof flag);   //print: boolean
  var vari = undefined;
  console.log(typeof vari);   //print: undefined
  var timer = null;
  console.log(typeof timer);  //print: object
</script>
```

#### 

##### 4.1.2.2字面量

字面量是源代码中一个固定值的表示法，通俗来说，就是字面量表示如何表达这个值。

​	数字字面量：8，9，10

​	字符字面量：‘黑马程序员’，"大前端"

​	布尔字面量：true，false



#### 4.1.3数据类型的转换

##### 4.1.3.1什么是数据类型转换

​	使用表单、prompt获取过来的数据默认是字符串类型，此时就不能直接简单的进行加法运算，而需要转换变量的数据类型。通俗来说，就是**把一种数据类型的变量转换成另外一种数据类型**。

转换为字符串类型

转换为数字型

转换为布尔型



##### 4.1.3.2转换为字符串

| 方式               | 说明                       | 案例                                       |
| :----------------- | -------------------------- | ------------------------------------------ |
| toString()         | 转成字符串                 | var num = 1;   alert(num.toString());      |
| String()强制转换   | 转成字符串                 | var num = 1;   alert.(String(num));        |
| **加号拼接字符串** | 和字符串拼接的结果是字符串 | var num = 1;   alert.(num + '我是字符串'); |

toString()和String()	使用方式不一样

三种转换方式，我们更喜欢用第三种加号拼接字符串转换方式，这一种方式也称之为隐式转换。

##### 4.1.3.3转换为数字型（重点）

| 方式                        | 说明                           | 案例                 |
| --------------------------- | ------------------------------ | -------------------- |
| **parseInt(string)函数**    | 将string类型转换成整数数值型   | parseInt('78');      |
| **parseFloat(string)函数**  | 将string类型转换成浮点数数值型 | parseFloat('78.21'); |
| Number()强制转换函数        | 将string类型转换成数值型       | Number('12');        |
| **js隐式转换（ -  *  / ）** | 利用算数运算隐式转换成数值型   | '12' - 0             |

```js
<script>
  console.log(parseInt('rem123.1'));    //print: NaN
  console.log(parseFloat('rem123.1'));  //print: NaN
  console.log('123' - 0);               //print: 123
  console.log('123' - '120');           //print: 3
  console.log('123' * 1);               //print: 123
  console.log('123' / 1);               //print: 123
</script>
```

注意parseInt和parseFloat**单词的大小写**，这2个是重点

隐式转换是我们在进行算数运算的时候，JS自动转换了数据类型。

##### 4.1.3.4-1案例1：计算年龄

此案例要求在页面中弹出一个输入框，我们输入出生年份后，能计算出我们的年龄。

```js
<script>
  var year = prompt('请输入你的出生年份：');
  var age = 2021 - year;
  alert('你今年已经' + age + '岁了');
</script>
```

##### 4.1.3.4-2案例2：简单加法器

计算两个数的值，用户输入第一个值后，继续弹出第二个输入框并输入第二个值，最后通过弹出窗口显示出两次输入值相加的结果。

```js
<script>
  var num1 = prompt('请输入第一个值');
  var num2 = prompt('请输入第二个值');
  var result = parseInt(num1) + parseFloat(num2);
  alert('相加结果是' + result);
</script>
```

##### 4.1.3.5转换为布尔型

| 方式          | 说明               | 案例             |
| ------------- | ------------------ | ---------------- |
| Boolean()函数 | 其他类型转成布尔值 | Boolean('true'); |

代表**空、否定的值**会被转换成false，如"、0、NaN、null、undefined

其他值都会被转换成true

```js
<script>
  //如"、0、NaN、null、undefined
  console.log(Boolean(''));
  console.log(Boolean(0));
  console.log(Boolean(NaN));
  console.log(Boolean(null));
  console.log(Boolean(undefined));
</script>
```

#### 4.1.4扩展阅读

##### 4.1.4.1解释型语言和编译型语言

翻译器翻译的方式有两种：一个是**编译**、另外一个是**解释**。两个方式之间的区别在于**翻译的时间点不同**

编译器是在**代码执行之前进行编译**，生成中间代码文件

解释器是在**运行时进行及时解释**，并立即执行（当编译器以解释方式运行的时候，也称之为解释器）

##### 4.1.4.2标识符、关键字、保留字

###### 1、标识（zhi）符

​	就是指开发人员为变量、属性、函数、参数取的名字

​	**标识符不能是关键字或保留字**

###### 2、关键字

​	是指JS本身已经使用了的字，不能再用他们充当变量名、方法名

###### 3、保留字

​	实际上就是预留的关键字，意思是现在虽然还不是关键字，但是未来可能会成为关键字，同样不能使用他们当变量名或方法名



##### 4.1.4.3课后作业

依次询问并获取用户的姓名、年龄、性别、并打印用户信息如图

```js
<script>
  var myName = prompt('请输入您的姓名：');
  var myAge = prompt('请输入您的年龄：');
  var mySex = prompt('请输入您的性别：');
  alert('您的姓名是：' + myName + '\n您的年龄是：' + myAge + '\n您的性别是：' + mySex);
</script>
```



### 5.运算符

#### 5.1运算符

运算符（operator）也被称为**操作符**，是用于实现赋值、比较和执行算数运算等功能的符号

#### 5.2算数运算符

##### 5.2.1算数运算符的概述

概念：算术运算使用的符号，用于执行两个变量或值的算数运算

+

-

*

/

%

##### 5.2.2浮点数的精度问题

浮点数值的最高精度是17位小数，但在进行算数运算时其精度远远不如整数

```js
<script>
      console.log(3 % 5); //print: 3
      //浮点数运算会出现问题
      console.log(0.1 + 0.2); //print: 0.30000000000000004
      console.log(0.07 * 100); //print: 7.000000000000001
      //不能直接拿浮点数来直接相比较 是否相等
      var num = 0.1 + 0.2;
      console.log(num == 0.3); //print: false
  </script>
```

所以：**不要直接判断两个浮点数是否相等！**

##### 5.2.3课堂提问

1、我们怎么判断一个数能够被整除呢？

​	**它的余数是0就说明这个数能被整除，这就是%取余运算符的主要用途。**

2、请问1 + 2 * 3结果是？

​	**结果是7，先乘除后加减，有小括号先算小括号里面。**



##### 5.2.4表达式和返回值

**表达式：**是由数字、运算符、变量等以能求得数值的有意义排列方法所得的组合。

简单理解：是由数字、运算符、变量等组成的句子。



#### 5.3递增和递减运算符

##### 5.3.1概述

如果需要反复给数字变量添加或减去1，可以用**递增（++）和递减（--）**运算符来完成

**注意：递增和递减运算符必须和变量配合使用**

##### 5.3.2前后区别

后的口诀：**先返回原值，后自加（减）**。

```js
  <script>
    var age = 10;
    console.log(age++ + 10);   //print: 20
    console.log(age);         //print: 11
  </script>
```

前的口诀：**先自加（减），后运算**。

```js
  <script>
    var age = 10;
    console.log(++age + 10);   //print: 21
    console.log(age);         //print: 11
  </script>
```

##### 5.3.3前置递增和后置递增的小结

+ 前置递增和后置递增运算可以简化代码的编写，让变量的值 +1，比以前写法简单

+ 单独使用时，运行结果相同
+ 与其他代码联用时，执行结果会不同
+ 后置：先原值运算，后自加（先人后己）
+ 前置：先自增，后运算（先己后人）
+ 开发时，大多使用后置递增/减，并且代码独占一行，例如：num++; 或者num--;

#### 5.4比较运算符

##### 5.4.1概述

比较运算符（关系运算符）是**两个数据进行比较时所使用的运算符**，比较运算后，会**返回一个布尔值**（true / false）作为比较运算的结果

 >

 <

 >=

 <=

 ==

 !=

 ===		!==

##### 5.4.2	=小结

| 符号 | 作用 | 用法                                     |
| ---- | ---- | ---------------------------------------- |
| =    | 赋值 | 把右边给左边                             |
| ==   | 判断 | 判断两边值是否相等（注意此时有隐式转换） |
| ===  | 全等 | 判断两边的值和数据类型是否完全相同       |

#### 5.5逻辑运算符

##### 5.5.1概述

逻辑运算符是用来进行布尔值运算的运算符，其返回值也是布尔值。后面开发中经常用于多个条件的判断

&&

||

！

##### 5.5.2逻辑与&&

两边都是true才返回true，否则返回false

##### 5.5.3逻辑非！

逻辑非（！）也叫做取反符，用来取一个布尔值相反的值，如true的相反值是false

##### 5.5.4短路运算（逻辑中断）

**短路运算的原理**：当有多个表达式（值）时左边的表达式可以确定结果时，就不再继续运算右边的表达式的值

###### 5.5.4.1逻辑与

+ 语法：**表达式1&&表达式2**
+ 如果第一个表达式的值为真，则返回表达式2
+ 如果第一个表达式的值为假，则返回表达式1

```js
  <script>
      console.log(123 && 456); //456
      console.log(0 && '123' & 123); //0
  </script>
```

###### 5.5.4.1逻辑或

+ 语法：**表达式1 || 表达式2**
+ 如果第一个表达式的值为真，则返回表达式1
+ 如果第一个表达式的值为假，则返回表达式2

```js
  <script>
    var num = 0;
    console.log(123 || num++);  //print: 123
    console.log(num);           //print: 0
  </script>
```

#### 5.6赋值运算符

##### 5.6.1概述

用来把数据赋值给变量的运算符

=

+=、-=

*=、/=、%=

#### 5.7运算符优先级

+ 一元运算符里面的**逻辑非优先级很高**
+ 逻辑与比逻辑或优先级高



### 6.流程控制

流程控制就是来控制我们的代码按照什么结构顺序来执行

流程控制主要有三种结构，分别是**顺序结构**、**分支结构**和**循环结构**，这三种结构代表三种代码执行的顺序

#### 6.1顺序流程控制

​	顺序结构是程序中最简单、最基本的流程控制。它没有特定的语法结构，程序会按照**代码的先后顺序，依次执行**，程序中大多数的代码都是这样执行的

#### 6.2分支流程控制if语句

##### 6.2.1分支结构

由上到下执行代码的过程中，根据不同的条件，执行不同的路径代码（执行代码多选一的过程），从而得到不同的结果

##### 6.2.2 if语句

语法结构：

```js
  <script>
    //条件成立执行代码，否则什么都不做
    if (条件表达式1) {
      //条件成立执行的代码语句
      //语句1
    } else if (条件表达式2) {
      //语句2
    } else if (条件表达式3) {
      //语句3
     ....
    } else {
      //上述条件都不成立执行此代码
      //最后的语句
    }
  </script>
```

语句可以理解为一个行为，循环语句和分支语句就是典型的语句。一个程序由很多个语句组成，一般情况下，会分割成一个一个的语句

##### 6.2.3-1案例：进入网吧

弹出一个输入框，要求用户输入年龄，如果年龄大于等于18岁，允许进入网吧。

```js
  <script>
    var age = prompt('请输入你的年龄：');
    if (age >= 18) {
      alert('我想带你去网吧偷耳机。');
    }else {
      alert('滚，回家做作业去！');
    }
  </script>
```

##### 6.2.3-2案例：判断闰年

接收用户输入的年份，如果是闰年就弹出闰年，否则弹出是平年

**案例分析**：

​	算法：能被4整除**且**不能整除100的为闰年（如2004年就是闰年，1901年不是闰年）**或者**能够被400整除的就是闰年

```js
  <script>
    //算法：能被4整除**且**不能整除100的为闰年（如2004年就是闰年，1901年不是闰年）**或者**能够被400整除的就是闰年
    var year = prompt('请您输入年份：');
    if (year % 4 == 0 && year % 100 != 0 || year % 400 == 0) {
      alert(year + '年是闰年。')
    } else {
      alert(year + '年是平年。')
    }
  </script>
```

##### 6.2.3-3独立完成案例：判断是否中奖

接收用户输入的姓名，来判断是否中奖，如果输入的是刘德华，则提示中了5块钱，否则提示没有中奖。

```js
  <script>
    //接收用户输入的姓名，来判断是否中奖，如果输入的是刘德华，则提示中了5块钱，否则提示没有中奖。
    var client = prompt('请您输入姓名：');
    if (client == '刘德华') {
      alert('您中了5块钱。');
    } else {
      alert('您没有中奖。');
    }
  </script>
```

##### 6.2.3-4案例：判断成绩级别

要求：接收用户输入的分数，根据分数输出对应的等级字母A、B、C、D、E。

其中：

1.90分（含）以上，输出：A

2.80分（含）以上～90分（不含），输出：B

3.70分（含）以上～80分（不含），输出：C

4.60分（含）以上～70分（不含），输出：D

5.60分（不含）以下，输出：E

```js
  <script>
    var score = prompt('请你输入分数：');
    if (score >= 90 && score <= 100) {
      alert('A');
    } else if (score >= 80 && score < 90) {
      alert('B');
    } else if (score >= 70 && score < 80) {
      alert('C');
    } else if (score >= 60 && score < 70) {
      alert('D');
    } else {
      alert('E');
    }
  </script>
```

#### 6.3三元表达式

三元表达式也能做一些简单的条件选择，有三元运算符组成的式子称为三元表达式

语法结构：**条件表达式 ？表达式1 ：表达式2**

**执行思路**：如果条件表达式结果为**真**，则返回**表达式1**的值；如果条件表达式结果为**假**，则返回**表达式2**的值

##### 案例：数字补0

用户输入数字，如果数字小于10，则在前面补0，比如01、09，如果数字大于10，则不需要补，比如20。

```js
  <script>
    var num = parseInt(prompt('请你输入一个0～59之间的一个数字：'));
    var result = num < 10 ? '0' + num : num;
    alert(result);
  </script>
```

#### 6.4分支流程控制switch语句

##### 6.4.1语法结构

switch语句也是多分支语句，它用于基于不同的条件来执行不同的代码。当要针对变量设置一系列的特定值的选项时，就可以使用switch

```js
  <script>
    switch(表达式){
      case value1:
        //表达式 等于value1时要执行的代码
        break;
      case value2:
        //表达式 等于value2时要执行的代码
        break;
      default:
        //表达式 不等于任何一个value时要执行的代码
    }
  </script>
```

##### 6.4.2switch注意事项

1、我们开发里面	表达式我们经常写成变量

2、我们num的值和case里面的值相匹配的时候是 全等 必须是值和数据类型一致才可以num===1

3、break如果当前的case里面没有break	则不会退出switch	是继续执行下一个case

##### 6.4.3案例：查询水果

用户在弹出框里面输入一个水果，如果有就弹出该水果的价格，如果没有该水果就弹出“没有此水果”。

```js
  <script>
    var fruit = prompt('请你输入要查询的水果：');
    switch (fruit) {
      case '苹果':
        alert('苹果的价格是3.5元/斤');
        break;
      case '榴莲':
        alert('榴莲的价格是35元/斤');
        break;
      default:
        alert('没有此水果');
    }
  </script>
```

##### 6.4.4switch语句和if else if语句的区别

1、一般情况下，它们两个语句可以互相替换

2、switch...case语句通常处理case为比较确定值的情况，而if...else...语句更加灵活，常用于范围判断（大于、等于某个范围）

3、switch语句进行条件判断后直接执行到程序的条件语句，效率更高。而if...else...语句有几种条件，就得判断多少次

4、但分支比较少时，if...else...语句的执行效率比switch语句高

5、当分支比较多时，switch语句的执行效率比较高，而且结构更清晰

##### 6.4.5作业

1、判断时间阶段。

比如用户输入12点弹出中午好
		用户输入18点弹出傍晚好
		用户输入23点弹出深夜好

```js
  <script>
    var time = prompt('请输入整点数：（例：13点）：');
    switch (time) {
      case '12点':
        alert('中午好');
        break;
      case '18点':
        alert('傍晚好');
        break;
      case '23点':
        alert('深夜好');
        break;
      default:
        alert('现在是' + time);
    }
  </script>
```

2、比较数大小

比较两个数的最大值（用户依次输入两个值，最后弹出最大的那个值）

```js
<script>
  var num1 = prompt('请输入第一个值：');
  var num2 = prompt('请输入第二个值：');
  if (num1 >= num2) {
    alert('最大值是：' + num1);
  } else {
    alert('最大值是：' + num2);
  } 
</script>
```

3、判断奇偶

用户输入一个数，来判断是奇数还是偶数

```js
<script>
  var num = prompt('请输入一个整数来判断奇偶：');
  if (num % 2 == 0) {
    alert(num + '是偶数');
  }else {
    alert(num + '是奇数');
  }
</script>
```

4、查询星期

根据用户输入的数值（数字1到数字7），返回星期几

```js
    <script>
        var date = parseInt(prompt('请输入1～7，来返回星期几：'));
        switch (date) {
            case 1:
                alert('星期一');
                break;
            case 2:
                alert('星期二');
                break;
            case 3:
                alert('星期三');
                break;
            case 4:
                alert('星期四');
                break;
            case 5:
                alert('星期五');
                break;
            case 6:
                alert('星期六');
                break;
            case 7:
                alert('星期日');
                break;
        }
    </script>
```



### 7.循环

在JS中，主要有三种类型的循环语句：

+ for循环
+ while循环
+ do...while循环

#### 7.1for循环

##### 7.1.1for循环执行过程

在程序中，一组被重复执行的语句被称为**循环体**，能否继续重复执行，取决于循环的**终止条件**。由循环体及循环的终止条件组成的语句，被称之为**循环语句**。

语法结构：

```js
  <script>
    for (初始化变量; 条件表达式; 操作表达式) {
      //循环体
    }
  </script>
```

##### 7.1.2for循环重复相同的代码

```js
  <script>
    var print = prompt('请您输入要循环的次数：');
    for (var num = 1; num <= print; num++) {
      console.log('我好大家好');
    }
  </script>
```

##### 7.1.3for循环重复不相同的代码

for循环可以重复执行不同的代码	因为我们有计数器变量 i 的存在	i 每次循环值都会变化

```js
//我们想要输出1个人 1～100岁
  <script>
    for (var i = 1; i <= 100; i++) {
      console.log('我今年' + i + '岁了')
    }
  </script>
```

##### 7.1.4for循环重复某些相同操作

for循环因为有了计数器的存在，我们还可以重复的执行某些操作，比如做一些算术运算。

###### 7.1.4-1课堂案例：求1～100之间所有整数的累加和

```js
  <script>
    var sum = 0;
    for (var num = 1; num <= 100; num++) {
      sum += num;
    }
    console.log(sum);
  </script>
```

###### 7.1.4-2课堂案例：求1～100之间所有数的平均值

```js
  <script>
    var sum = 0;
    var age = 0;
    for (var num = 1; num <= 100; num++) {
      sum += num;
    }
    ave = sum / 100;
    console.log(ave);
  </script>
```

###### 7.1.4-3课堂案例：求1～100之间所有偶数和奇数的和

```js
  <script>
    var even = 0;
    var odd = 0;
    for(var num = 1; num <= 100; num++) {
      if(num % 2 == 0) {
        even += num;
      } else {
        odd += num;
      }
    }
    console.log('偶数和是：' + even);
    console.log('奇数和是：' + odd);
  </script>
```

###### 7.1.4-4课堂案例：求1～100之间所有能被3整除的数字的和

```js
  <script>
    var sum = 0;
    for (var num = 1; num <= 100; num++) {
      if(num % 3 == 0){
        sum += num;
      }
    }
    console.log('能被三整除的数字的和是：' + sum);
  </script>
```

###### 7.1.4-5课堂案例：求学生成绩

要求用户输入班级人数，之后依次输入每个学生的成绩，最后打印出该班级总的成绩以及平均成绩。

```js
  <script>
    var gross = parseInt(prompt('请输入班级的总人数：'));
    var sum = 0;
    var ave = 0;
    for (var i = 1; i <= gross; i++) {
      var stu = parseFloat(prompt('请输入第' + i + '个学生的成绩：'));
      sum += stu;
      ave = sum / gross;
    }
    console.log('总成绩为：' + sum);
    console.log('平均成绩为：' + ave);
  </script>
```

###### 7.1.4-6课堂案例：一行打印数颗星星

```js
  <script>
    var num = prompt('请输入星星的个数：');
    var str = '';
    for (var i = 1; i <= num; i++) {
      str += '★';
    }
    console.log(str);
  </script>
```

#### 7.2双重for循环

##### 7.2.1概述

**循环嵌套**是指**在一个循环语句中在定义一个循环语句的语法结构**，例如在for循环语句中，可以再嵌套一个for循环，这样的for循环语句我们称之为**双重for循环**。

##### 7.2.2语法结构

```js
  <script>
    //双重for循环 语法结构
    for (外层的初始化变量; 外层的条件表达式; 外层的操作表达式) {
      for (里层的初始化变量; 里层的条件表达式; 里层的操作表达式) {
        //执行语句;
      }
    }
  </script>
```

1、我们可以把里面的循环看做是外层循环的语句

2、外层循环循环一次，里面的循环执行全部

3、代码验证

```js
  <script>
    for (var i = 1; i <=3; i++) {
      console.log('这是外层循环第' + i + '次');
      for (var j = 1; j <= 3; j++) {
        console.log(' 这是里层循环第' + j + '次');
      }
    }
  </script>
```

##### 7.2.3案例：打印五行五列星星

```js
  <script>
    var num = 5;
    var str = '';
    for (var i = 1; i <= num; i++) {
      for (var j = 1; j <= num; j++) {
        str += '★';
      }
      str += '\n';
    }
    console.log(str);
  </script>
```

##### 7.2.4-1课堂案例：打印n行n列星星

```js
  <script>
      var row = prompt('请输入行数：');
      var col = prompt('请输入列数：');
      var str = '';
      for (var i = 1; i <= row; i++) {
          for (var j = 1; j <= col; j++) {
              str += '★';
          }
          str += '\n';
      }
      console.log(str);
  </script>
```

##### 7.2.4-2课堂案例：打印倒三角形

```js
  <script>
    var str = '';
    for (var i = 1; i <= 10; i++) {
      for (var j = i; j <= 10; j++) {
        str += '★';
      }
      str += '\n';
    }
    console.log(str);
  </script>
```

##### 7.2.4-3课堂案例：打印九九乘法表

```js
  <script>
    var str = '';
    for (var i = 1; i <= 9; i++) {
      for (var j = 1; j <= i; j++) {
        var result = i * j;
        str += i + '*' + j + '=' + result + '\t';
      }
      str += '\n';
    }
    console.log(str);
  </script>
```



##### 7.2.5课后作业案例：打印正三角形

```js
  <script>
    var str = '';
    for (var i = 1; i <= 10; i++) {
      for (var j = 11 - i; j <= 10; j++) {
        str += '★';
      }
      str += '\n';
    }
    console.log(str);
  </script>
```

#### 7.3for循环小结

+ for循环可以重复执行某些相同的代码
+ for循环可以重复执行些许不同的代码，因为我们有计数器
+ for循环可以重复执行某些操作，比如算术运算符加法操作
+ 随着需求增加，双重for循环可以做更多，更好看的效果
+ 双重for循环，外层循环一次，内层for循环执行全部
+ for循环是循环条件和数字直接相关的循环

+ 分析要比写代码更重要
+ 一些核心算法想不到，但是要学会，分析他执行过程
+ 举一反三，自己经常总结，做一些相似的案例

#### 7.4while循环

##### 7.4.1概述

while语句可以在条件表达式为真的前提下，循环执行指定的一段代码，直到表达式不为真时结束循环。

##### 7.4.2while语法结构

```js
  <script>
    while (条件表达式) {
      //循环体代码
    }
  </script>
```

1、执行思路：当条件表达式结果为true	则执行循环体	否则	退出循环

2、里面应该也有计数器	初始化变量

3、里面应该也有操作表达式	完成计数器的更新	防止死循环

4、代码验证：

```js
  <script>
    var num = 1;
    while (num <= 100) {
      console.log('Hello');
      num++;
    }
  </script>
```

##### 7.4.3-1课堂案例：打印人生

打印人的一生，从1岁到100岁。

```js
  <script>
    var age = 1;
    while (age <= 100) {
      console.log(age + '岁');
      age++;
    }
  </script>
```

##### 7.4.3-2课堂案例：计算累加和

计算1～100之间所有整数的和

```js
  <script>
    var num = 1;
    var sum = 0
    while (num <= 100) {
      sum += num;
      num++
    }
    console.log('1~100累加和是：' + sum);
  </script>
```

##### 7.4.3-3课堂案例：老流氓

弹出一个提示框，你爱我吗？如果输入我爱你，就提示结束，否则一直询问。

```js
  <script>
    var love = prompt('你爱我吗？');
    while (love !== '我爱你') {
      love = prompt('爱不爱我！？');
    }
    alert('我也爱你');
  </script>
```



#### 7.5do while循环

##### 7.5.1概述

​	do...while语句其实是while语句的一个变体。该循环会先执行一次代码块，然后对条件表达式进行判断，如果条件表达式为真，就会重复执行循环体，否则退出循环。

##### 7.5.2do...while语法结构

```js
  <script>
    do {
      //循环体
    } while (条件表达式)
  </script>
```

1、执行思路：跟while不同的地方在于do while 先执行一次循环体，再判断条件；如果条件表达式为真，就会重复执行循环体，否则退出循环。

2、我们的do while**循环体至少执行一次**

3、代码验证

```js
  <script>
    var i = 1;
    do {
      console.log('how are you?');
      i++;
    } while (i <= 100)
  </script>
```

##### 7.5.3-1课堂案例：打印人生

打印人的一生，从1岁到100岁。

```js
  <script>
    var age = 1;
    do {
      console.log(age + '岁');
      age++;
    } while (age <= 100)
  </script>
```

##### 7.5.3-2课堂案例：计算累加和

计算1～100之间所有整数的和

```js
  <script>
    var num = 1;
    var sum = 0;
    do {
      sum += num;
      num++;
    } while (num <= 100)
    console.log('1~100累加和是：' + sum);
  </script>
```

##### 7.5.3-3课堂案例：老流氓

弹出一个提示框，你爱我吗？如果输入我爱你，就提示结束，否则一直询问。

```js
  <script>
    do {
      var love = prompt('爱不爱我！？');
    } while (love !== '我爱你');
    alert('我也爱你');
  </script>
```

#### 7.6循环小结

+ JS中循环有for、while、do while
+ 三个循环很多情况下都可以相互替代使用
+ 如果是用来计次数，跟数字相关的，三者使用基本相同，但是我们更喜欢for
+ while和do...while可以做更复杂的判断条件，比for循环灵活一些
+ while和do...while执行顺序不一样，while先判断后执行，do...while先执行一次，再判断执行
+ while和do...while执行次数不一样，do...while至少会执行一次循环体，而while可能一次也不执行
+ 实际工作中，**我们更常用for循环语句**，他写法更简洁美观，所以这个要重点学习

#### 7.7continue break

##### 7.7.1continue关键字

**continue关键字**用于立即**跳出本次循环**，**继续下一次循环**（本次循环体中continue之后的代码就会少执行一次）。

##### 7.7.2break关键字

**break关键字用于**立即**跳出整个循环**（循环结束）。

#### 7.8命名规范以及语法格式

##### 7.8.1标识符命名规范

+ 变量、函数的命名必须有意义
+ 变量的名称一般用名词
+ 函数的名称一般用动词

##### 7.8.2操作符规范

+ 操作符的左右两侧各保留一个空格

##### 7.8.3单行注释规范

+ 单行注释前面注意有个空格

#### 7.9循环作业

1、求1～100之间所有数的总和和平均值

```js
  <script>
    var sum = 0,
        ave = 0;
    for (var i = 1; i <= 100; i++) {
      sum += i;
    }
    ave = sum / 100;
    console.log(sum);
    console.log(ave);
  </script>
```

2、求1～100之间所有偶数的和

```js
  <script>
    var even = 0;
    for (var i = 1; i <= 100; i++) {
      if (i % 2 == 0) {
        even += i;
      } else {
        continue;
      }
    }
    console.log(even);
  </script>
```

3、求100以内7的倍数的总和

```js
  <script>
    var gross = 0;
    for (var i = 1; i <= 100; i++) {
      if (i % 7 == 0) {
        gross += i;
      } else {
        continue;
      }
    }
    console.log(gross);
  </script>
```

4、使用for循环打印矩形，要求每次只能输出一个★

```js
  <script>
    var str = '';
    var num = prompt('请输入行列数：');
    for (var i = 1; i <= num; i++) {
      for (var j = 1; j <= num; j++) {
        str += '★';
      }
      str += '\n';
    }
    console.log(str);
  </script>
```

5、使用for循环打印正三角形

```js
  <script>
    var str = '';
    var num = prompt('请输入行列数：');
    for (var i = 1; i <= num; i++) {
      for (var j = 1; j <= i; j++) {
        str += '★';
      }
      str += '\n';
    }
    console.log(str);
  </script>
```

6、使用for循环打印99乘法表

```js
  <script>
    var str = '';
    for (var i = 1; i <= 9; i++) {
      for (var j = 1; j <= i; j++) {
        var result = i * j;
        str += i + '*' + j + '=' + result + '\t';
      }
      str += '\n';
    }
    console.log(str);
  </script>
```

7、接收用户输入的用户名和密码，若用户名为“admin”，密码为“123456”，则提示用户登录成功！否则，让用户一直输入。

```js
  <script>
    var admin = prompt('请输入用户名：');
    var password = prompt('请输入密码：');
    while (admin !== 'admin' || password !== '123456') {
      admin = prompt('请重新输入用户名：');
      password = prompt('请重新输入密码：');
    }
    alert('登录成功');
  </script>
```

8、求整数1～100的累加值，但要求跳过所有个位是3的数【用continue实现】

```js
  <script>
    var sum = 0;
    for (var i = 1; i <= 100; i++) {
      if(i % 10 == 3) {
        continue;
      } else {
        sum += i;
      }
    }
    console.log(sum);
  </script>
```

9、小组项目：简易ATM

+ 里面现存有100块钱。
+ 如果存钱，就用输入钱数加上先存的钱数，之后会弹出显示余额提示框。
+ 如果取钱，就减去取的钱数，之后弹出显示余额提示框。
+ 如果显示余额，就输出余额。
+ 如果退出，弹出退出信息提示框。

```js
  <script>
      var op = parseInt(prompt('请输入您要的操作：\n1.存钱\n2.取钱\n3.显示余额\n4.退出'));
      var balance = 100;
      while (op !== 1 && op !== 2 && op !== 3 && op !== 4) {
          alert('您输入有误，请回车重新输入');
          op = parseInt(prompt('请输入您要的操作：\n1.存钱\n2.取钱\n3.显示余额\n4.退出'));
      }
      while (op == 1) {
          var add = parseInt(prompt('您要存的钱数是：'));
          if (add <= 0) {
              alert('您输入的钱数有误，请重新输入：');
              add = parseInt(prompt('您要存的钱数是：'));
          } else {
              balance += add;
              alert('余额为：' + balance);
              op = parseInt(prompt('请输入您要的操作：\n1.存钱\n2.取钱\n3.显示余额\n4.退出'));
          }
      }
      while (op == 2) {
          var withdraw = prompt('您要取的钱数是：');
          if (withdraw <= 0) {
              alert('您输入的钱数有误，请重新输入：');
              withdraw = parseInt(prompt('您要存的钱数是：'));
          } else {
              balance += withdraw;
              alert('余额为：' + balance);
              op = parseInt(prompt('请输入您要的操作：\n1.存钱\n2.取钱\n3.显示余额\n4.退出'));
          }
      }
      while (op == 3) {
          alert('您现在的余额是：' + balance);
          op = parseInt(prompt('请输入您要的操作：\n1.存钱\n2.取钱\n3.显示余额\n4.退出'));
      }
      if (op == 4){
          alert('你正在退出！');
      }
  </script>
```

### 8.数组

#### 8.1概念

​	数组可以把一组相关的数据一起存放，并提供方便的访问（获取）方式。

​	数组是指**一组数据的集合**，其中的每个数据被称为**元素**，在数组中可以**存放任意类型的元素**。数组是一种将**一组数据存储在单个变量名下**的优雅方式。

#### 8.2创建数组

##### 8.2.1数组的创建方式

JS中创建数组有两种方式：

+ 利用new创建数组
+ 利用数组字面量创建数组

##### 8.2.2利用new创建数组

```js
  <script>
    var 数组名 = new Array();
    var arr = new Array();  //创建一个新数组
  </script>
```

+ 这种方式暂且了解，等学完对象再看
+ 注意Array()，A要大写

##### 8.2.3利用数组字面量创建数组

```js
  <script>
    var arr = []; //创建一个空数组
    var arr1 = [1, 2, 'Hello', true];
  </script>
```

数组里面的数据	比如1, 2, 'Hello', true	我们称为数组元素

字面量方式也是我们以后**最多使用方式**

##### 8.2.4数组元素的类型

数组中可以存放**任意类型**的数据，例如字符串，数字，布尔值等。

#### 8.3获取数组元素

##### 8.3.1数组的索引

获取数组元素	格式：**数组名[索引号]**

**索引（下标）**：用来访问数组元素的序号（数组下标从0开始）。

数组可以通过**索引**来访问、设置、修改对应的数组元素，我们可以通过 “**数组名[索引]**” 的形式来获取数组中的元素。

这里的**访问**就是获取得到的意思。

##### 8.3.2课堂练习：数组练习

定义一个数组，里面存放星期一、星期二......直到星期日(共7天)，在控制台输出：星期日。

```js
  <script>
    var arr = ['星期一', '星期二', '星期三', '星期四', '星期五', '星期六', '星期日'];
    console.log(arr[6]);
  </script>
```

#### 8.4遍历数组

##### 8.4.1概述

**遍历：**就是把数组中的每个元素从头到尾都访问一次（类似我们每天早上学生的点名）

```js
  <script>
    var arr = ['red', 'green', 'pink'];
    for (var i = 0; i <= 2; i++) {
      console.log(arr[i]);
    }
  </script>
```

##### 8.4.2数组的长度

使用 “数组名.length” 可以访问数组元素的数量（数组长度）。

##### 8.4.3-1课堂案例：遍历数组

请将【“关羽”、“张飞”、“马超”、“赵云”、“黄忠”、“刘备”、“姜维”】；数组里的元素一次打印到控制台。

```js
  <script>
    var arr = ['关羽', '张飞', '马超', '赵云', '黄忠', '刘备', '姜维'];
    for (var i = 0; i < arr.length; i++) {
      console.log(arr[i]);
    }
  </script>
```

##### 8.4.3-2课堂案例：数组求和及平均值

求数组[2,6,1,7,4]里面所有元素的**和**以及**平均值**。

```js
  <script>
    var arr = [2, 6, 1, 7, 4];
    var sum = 0,
        ave = 0;
    for (var i = 0; i < arr.length; i++) {
      sum += arr[i];
    }
    ave = sum / arr.length;
    console.log(sum, ave);
  </script>
```

##### 8.4.3-3课堂案例：数组最大值

求数组[2,6,1,77,52,25,7]中的最大值

```js
  <script>
    var arr = [2, 6, 1, 77, 52, 25, 7];
    var max = arr[0],
        temp = 0;
    for (var i = 0; i < arr.length; i++) {
      if(arr[i] > max) {
        max = arr[i];
      }
    }
    console.log(max);
  </script>
```

##### 8.4.3-4课堂案例：数组转换为分割字符串

要求：将数组['red', 'green', 'blue', 'pink']转换为字符串，并且用｜或其他符号分割

输出：‘’red|green|blue|pink|'

```js
  <script>
    var arr = ['red', 'green', 'blue', 'pink'];
    var str = '';
    for (var i = 0; i < arr.length; i++) {
      str += arr[i] + '|';
    }
    console.log(str);
  </script>
```

#### 8.5数组中新增元素

##### 8.5.1概述

可以通过修改length长度以及索引号增加数组元素

##### 8.5.2通过修改length长度新增数组元素

+ 可以通过修改length长度来实现数组扩容的目的。
+ length属性是可读写的
+ 声明变量未给值，默认值就是**undefined**。

##### 8.5.3通过修改数组索引新增数组元素

+ 可以通过修改数组索引的方式追加数组元素。

##### 8.5.4-1课堂案例：数组新增元素

新建一个数组，里面存放10个整数（1～10）

```js
  <script>
    var arr = [];
    for (var i = 0; i < 10; i++) {
      arr[i] = i + 1;
    } 
    console.log(arr);
  </script>
```

##### 8.5.4-2课堂案例：筛选数组

要求：叫数组[2, 0, 6, 1, 77, 0, 52, 0, 25, 7]中大于等于10的元素选出来，放入新数组

```js
  //方式一
  <script>
    var arr = [2, 0, 6, 1, 77, 0, 52, 0, 25, 7];
    var new_arr = [];
    var j = 0;
    for (var i = 0; i < arr.length; i++) {
      if(arr[i] >= 10) {
        new_arr[j] = arr[i];
        j++;
      } else {
        continue;
      }
    }
    console.log(new_arr);
  </script>
```

```js
//方式二
  <script>
    var arr = [2, 0, 6, 1, 77, 0, 52, 0, 25, 7];
    var new_arr = [];
    for (var i = 0; i < arr.length; i++) {
      if(arr[i] >= 10) {
        new_arr[new_arr.length] = arr[i];
      } else {
        continue;
      }
    }
    console.log(new_arr);
  </script>
```

##### 8.5.5数组案例

###### 课堂案例1：删除指定数组元素

要求：将数组[2, 0, 6, 1, 77, 0, 52, 0, 25, 7]中的0去掉后，形成一个不包含0的新数组。

```js
  <script>
    var arr = [2, 0, 6, 1, 77, 0, 52, 0, 25, 7];
    var new_arr = [];
    for (var i = 0; i < arr.length; i++) {
      if(arr[i] == 0) {
        continue;
      } else {
        new_arr[new_arr.length] = arr[i]; 
      }
    }
    console.log(new_arr);
  </script>
```

###### 课堂案例2：翻转数组

要求：将数组['red', 'green', 'blue', 'pink', 'purple']的内容反过来存放。

输出：['purple', 'pink', 'blue', 'green' ,'red']

```js
  <script>
    var arr = ['red', 'green', 'blue', 'pink', 'purple'];
    var new_arr = [];
    for (var i = arr.length - 1; i >= 0; i--) {
      new_arr[new_arr.length] = arr[i];
    }
    console.log(new_arr);
  </script>
```

###### 课堂案例3：数组排序（冒泡排序）

冒泡排序：是一种算法，把一系列的数据按照一定的顺序进行排列显示（从小到大或从大到小）

```js
  <script>
    var arr = [5, 4, 3, 2, 1];
    var temp = 0;
    for (var i = 0; i < arr.length; i++) {
      for(var j = 0; j < arr.length - i; j++) {
        if (arr[j] > arr[j + 1]) {
          temp = arr[j];
          arr[j] = arr[j + 1];
          arr[j + 1] = temp;
        } else {
          continue;
        }
      }
    }
    console.log(arr);
  </script>
```

### 9.函数

#### 9.1函数的概念

**函数**：就是封装了一段**可被重复调用执行的代码块**。通过此代码块可以实现大量代码的重复使用。

```js
  <script>
    function getSum(num1, num2) {
      var sum = 0;
      for(var i = num1; i <= num2; i++) {
        sum += i;
      }
      console.log(sum);
    }
    getSum(1, 100);
    getSum(10, 50);
  </script>
```

#### 9.2函数的使用

函数在使用时分为两步：**声明函数**和**调用函数**

##### 9.2.1声明函数

语法结构：

```js
    function 函数名() {
        //函数体
    }
```

1、function声明函数的关键字全部小写

2、函数是做某件事情，函数名一般是动词	sayHi

3、函数不调用自己不执行

##### 9.2.2调用函数

语法结构：

```js
		函数名();
```

+ 调用的时候千万**不要忘记添加小括号**。
+ 口诀：函数不调用，自己不执行。

**注意：声明函数本身并不会执行代码，只有调用函数时才会执行函数体代码。**

##### 9.2.3函数的封装

+ 函数的封装是把一个或者多个功能通过**函数的方式封装起来**，对外只提供一个简单的函数接口。
+ 简单理解：封装类似于将电脑配件整合组装到机箱中（类似快递打包）

##### 9.2.4案例：利用函数计算1～100之间的累加和

```js
  <script>
    function getSum(num1, num2) {
      var sum = 0;
      for(var i = num1; i <= num2; i++) {
        sum += i;
      }
      console.log(sum);
    }
    getSum(1, 100);
  </script>
```

#### 9.3函数的参数

##### 9.3.1形参和实参

语法结构：

```js
  <script>
    function 函数名 (形参1, 形参2, ...) { //在声明函数小括号里面是 形参（形式上的参数）

    }
    函数名 (实参1, 实参2, ...); //在函数调用的小括号里面是 实参（实际的参数）
  </script>
```

执行过程：

```js
  <script>
    function cook (aru) { // 形参是接收实参的 aru = '酸辣肥牛'; 形参类似于一个变量
      console.log(aru);
    }
    cook('酸辣肥牛');
    cook('酸辣鱼');
  </script>
	//未完善
```

函数的参数可以有，也可以没有，个数不限

在**声明函数**时，可以在函数后面的小括号中添加一些参数，这些参数被称为**形参**，而在**调用该函数**时，同样也需要传递相应的参数，这些参数被称为**实参**。

| 参数     | 说明                                                         |
| -------- | ------------------------------------------------------------ |
| **形参** | **形**式上的参数，**函数定义**的时候传递的参数，当前并不知道是什么 |
| **实参** | **实**际上的参数，**函数调用**的时候传递的参数，实参是传递给形参的 |

##### 9.3.2-1案例：求任意两个数的和

```js
  <script>
    function getSum (num1, num2) {
      console.log(num1 + num2);
    }
    getSum(2, 3);
  </script>
```

##### 9.3.2-2案例：求任意两个数之间的和

```js
  <script>
    function getSums (start, end) {
      var sum = 0;
      for (var i = start; i <= end; i++) {
        sum += i;
      }
      console.log(sum);
    }
    getSums(1, 10);
  </script>
```

**注意点：**

+ 多个参数之间用逗号隔开
+ 形参可以看做是不用声明的变量

##### 9.3.3函数形参和实参个数不匹配问题

1、如果实参的个数多于形参的个数	会取到形参的个数

2、如果实参的个数少于形参的个数	多余的形参定义为undefined	最终结果就是NaN
		形参可以看成是不用声明的变量，XXX是一个变量但是没有接收值，结果就是undefined

建议：我们尽量让实参的个数和形参相匹配

| 参数个数                 | 说明                             |
| ------------------------ | -------------------------------- |
| 实参个数**等于**形参个数 | 输出正常结果                     |
| 实参个数**多于**形参个数 | 只取到形参的个数                 |
| 实参个数**少于**形参个数 | 多余的定义为undefined，结果为NaN |

**注意**：在JavaScript中，形参的默认值是**undefined**。

##### 9.3.4小结

+ 函数可以带参数也可以不带参数
+ 声明函数的时候，函数名括号里面的是形参，形参的默认值为undefined。
+ 调用函数的时候，函数名括号里面的是实参
+ 多个参数中间用逗号分隔
+ 形参的个数可以和实参个数不匹配，但是结果不可预计，我们尽量要匹配

#### 9.4函数的返回值

##### 9.4.1 return语句

有的时候，我们会希望函数将值返回给调用者，此时通过使用return语句就可以实现。

语法结构：

```js
  <script>
    function 函数名() {
      return 需要返回的结果;
    }
    函数名();
  </script>
```

1、我们函数只是实现某种功能，最终的结果需要返回给函数的调用者函数名()	通过return来实现的

2、只要函数遇到return，就把后面的结果	返回给函数的调用者	函数名() = return 后面的结果

3、代码验证：

```js
  <script>
    function getResult() {
      return 666;
    }
    getResult();
    console.log(getResult());
  </script>
```

```js
//完善上面的代码
  <script>
    function cook(aru) {
      return aru;
    }
    console.log(cook('酸辣肥牛'));
    console.log(cook('酸辣鱼'));
  </script>
```

4、求任意两个数的和

```js
  <script>
    function getSum(num1, num2) {
      return num1 + num2;
    }
    console.log(getSum(2, 3));
  </script>
```

##### 9.4.2-1案例：利用函数求任意两个数的最大值

```js
  <script>
    function getMaxNum(num1, num2) {
      return num1 > num2 ? num1 : num2;
    }
    console.log(getMaxNum(2, 4));
    console.log(getMaxNum(11, 2));
  </script>
```

##### 9.4.2-2案例：利用函数求任意一个数组中的最大值

求数组[5, 2, 99, 101, 67, 77]中的最大数值。

```js
  <script>
    function getArrMax(arr) {
      var max = arr[0];
      for (var i = 1; i <= arr.length; i++) {
        if (arr[i] > max) {
          max = arr[i];
        }
      }
      return max;
    }
    console.log(getArrMax([5, 2, 99, 101, 67, 77]));
    //console.log(getArrMax([1, 3, 9, 8]));
    //在我们实际开发里面，我们经常用一个变量来接收 函数的返回结果 使用更简单
    var re = getArrMax([5, 2, 99, 101, 67, 77]);
    console.log(re);
  </script>
```

##### 9.4.3 return终止函数

return语句之后的代码不被执行

##### 9.4.4 return的返回值

**return只能返回一个值**。如果用逗号隔开多个值，以**最后一个**为准。

##### 9.4.4-1案例：我们求任意两个数的加减乘除结果

```js
  <script>
    function getResult(num1, num2) {
      return [num1 + num2, num1 - num2, num1 * num2, num1 / num2];
    }
    var re = getResult(1,2);  //返回的是一个数组
    console.log(re);
  </script>
```

##### 9.4.5函数没有return返回undefined

函数都是有返回值的

1、如果有return则返回return后面的值

2、如果没有return则返回undefined

##### 9.4.6 break、continue、return的区别

+ break：结束当前的循环体（如for、while）
+ continue：跳出本次循环，继续执行下次循环（如for、while）
+ return：不仅可以退出循环，还能够返回return语句中的值，同时还可以结束当前的函数体内的代码

#### 9.5通过榨汁机看透函数

[![WRFWaq.png](https://z3.ax1x.com/2021/07/25/WRFWaq.png)](https://imgtu.com/i/WRFWaq)

#### 9.6 arguments使用

当我们不确定有多少个参数传递的时候，可以用**arguments**来获取。在JavaScript中，arguments实际上它是当前函数的一个**内置对象**。所有函数都内置了一个arguments对象，arguments对象中**存储了传递的所有实参**。

**arguments展示形式是一个伪数组**，因此可以进行遍历。伪数组具有以下特点：

+ 具有length属性
+ 按索引方式储存数据
+ 不具有数组的push、pop等方法

```js
  <script>
    function fn() {
      console.log(arguments); // 里面存储了所有传递过来的参数 arguments = [1, 2, 3]
      console.log(arguments.length);
      console.log(arguments[1]);
      // 我们可以按照数组的方式遍历arguments
      for (var i = 0; i < arguments.length; i++) {
        console.log(arguments[i]);
      }
    }
    fn(1, 2, 3);
    fn(5, 4, 3, 2, 1);
  </script>
```

##### 9.6.1案例：利用函数求任意个数的最大值（不是用数组）

```js
  <script>
    function getMax() {
      var max = arguments[0];
      for (var i = 1; i < arguments.length; i++) {
        max = arguments[i] > max ? arguments[i] : max;
      }
      return max;
    }
    console.log(getMax(1, 2, 3));
    console.log(getMax(1, 2, 3, 4, 5));
  </script>
```

#### 9.7函数案例

##### 9.7.1案例一：利用函数封装方式，翻转任意一个数组

```js
  <script>
    function reverse(arr) {
      var new_arr = [];
      for(var i = arr.length - 1; i >= 0; i--) {
        new_arr[new_arr.length] = arr[i];
      }
      return new_arr;
    }
    var arr1 = reverse([1, 2, 5, 6, 9]);
    console.log(arr1);
    var arr2 = reverse(['pink', 'red', 'green', 'purple']);
    console.log(arr2);
  </script>
```

##### 9.7.2案例二：利用函数封装方式，对数组排序——冒泡排序

```js
  <script>
    function getBubbleSort(arr) {
      var new_arr = [];
      for (var i = 0; i < arr.length - 1; i++) {
        for(var j = 0; j < arr.length - i - 1; j++) {
          if (arr[j] > arr[j + 1]) {
            var temp = arr[j];
            arr[j] = arr[j + 1];
            arr[j + 1] = temp;
          }
        }
      }
      return arr;
    }
    var arr1 = [1, 4, 5, 2, 3];
    console.log(getBubbleSort(arr1));
    var arr2 = [11, 7, 2, 999];
    console.log(getBubbleSort(arr2));
  </script>
```

##### 9.7.3案例三：判断闰年

要求：输入一个年份，判断是否是闰年（闰年：能被4整除并且不能被100整数，或者能被400整除）

```js
  <script>
    function isRunYear(year) {
      // 要求：如果是闰年，我们返回true 否则返回false
      // 方式一：三元表达式
      var flag;
      flag = year % 4 == 0 && year % 100 != 0 || year % 400 == 0 ? true : false;
      // 方式二：if判断语句
      // var flag = false;
      // if (year = year % 4 == 0 && year % 100 != 0 || year % 400 == 0) {
      //   flag = true;
      // }
      return flag;
    }
    console.log(isRunYear(2000));
  </script>
```

##### 9.7.4函数可以调用另外一个函数

因为每个函数都是独立的代码块，用于完成特殊任务，因此经常会用到函数相互调用的情况。

```js
  <script>
    function fn1() {
      console.log(11);
      fn2();  //在fn1 函数里面调用了 fn2 函数
    }
    fn1();	//print: 11	22
    function fn2() {
      console.log(22);
    }
    fn2();	//print: 22
  </script>
```

##### 9.7.5案例四：用户输入年份，输出当前年份2月份的天数

```js
  <script>
    function backDay() {
      var year = prompt('请您输入年份：');
      if (isRunYear(year)) {
        alert('您输入的年份是闰年,二月有29天。');
      } else {
        alert('您输入的年份不是闰年,二月有28天。');
      }
    }
    backDay();
    // 判断是否闰年的函数
    function isRunYear(year) {
      // 要求：如果是闰年，我们返回true 否则返回false
      // 方式一：三元表达式
      var flag;
      flag = year % 4 == 0 && year % 100 != 0 || year % 400 == 0 ? true : false;
      // 方式二：if判断语句
      // var flag = false;
      // if (year = year % 4 == 0 && year % 100 != 0 || year % 400 == 0) {
      //   flag = true;
      // }
      return flag;
    }
  </script>
```

#### 9.8函数的两种声明方式

1、利用函数关键字自定义函数（命名函数）

2、函数表达式（匿名函数）

语法结构：

```js
  <script>
    var 变量名 = function() {};
		//eg:
    var fun = function(aru) {
      console.log('I\'m function');
      console.log(aru);
    }
    fun('pink');
  </script>
```

+ fun是变量名	不是函数名
+ 函数表达式声明方式跟声明变量差不多，只不过变量里面存的是值，而函数表达式里面存的是函数
+ 函数表达式也可以进行传递参数

### 10.JavaScript作用域

#### 10.1作用域

##### 10.1.1作用域概述

通常来说，一段程序代码中所用到的名字并不总是有效和可用的，而限定这个名字的**可用性的代码范围**就是这个名字的**作用域**。作用域的使用提高了程序逻辑的局部性，增强了程序的可靠性，减少了名字冲突。

##### 10.1.2 js的作用域（es6）之前

+ 全局作用域：整个script标签	或者是一个单独的js文件
+ 局部作用域：在函数内部就是局部作用域。这个代码的名字只在函数内部起效果和作用

##### 10.1.3 es6块级作用域（了解即可）



#### 10.2变量的作用域

##### 10.2.1变量作用域的分类

在JavaScript中，根据作用域的不同，变量可以分为两种：

+ 全局变量：在全局作用域下的变量
+ 局部变量：在局部作用域下的变量。后者在函数内部的变量就是局部变量

**注意**：函数的形参也可以看做是局部变量

从**执行效率**来看全局变量和局部变量

​	1、全局变量	只有浏览器关闭的时候才会销毁，比较占内存资源

​	2、局部变量	当我们程序执行完毕就会销毁，比较节约内存资源

##### 10.2.2全局变量

在全局作用域下声明的变量叫做**全局变量**（**在函数外部定义的变量**）。

+ 全局变量在代码的任何位置都可以使用
+ 在全局作用域下var声明的变量是全局变量
+ 特殊情况下，在函数内不使用var声明的变量也是全局变量（不建议使用）

##### 10.2.3局部变量

在局部作用域下声明的变量叫做**局部变量**（**在函数内部定义的变量**）

+ 局部变量只能在该函数**内部**使用
+ 在函数内部var声明的变量是局部变量
+ 函数的**形参**实际上就是局部变量

##### 10.2.4全局变量和局部变量的区别

+ 全局变量：在任何一个地方都可以使用，只有在浏览器关闭时才会被销毁，因此比较占内存
+ 局部变量：只能在函数内部使用，当其所在的代码块被执行时，会被初始化；当代码块运行结束后，就会被销毁，因此更节省内存空间

#### 10.3作用域链

##### 10.3.1概述

+ 只要是代码，就至少有一个作用域
+ 写在函数内部的局部作用域
+ 如果函数中还有函数，那么在这个作用域中就又可以诞生一个作用域
+ 根据在内部函数可以访问外部函数变量的这种机制，用链式查找决定哪些数据能被内部函数访问，就称为作用域链

##### 10.3.2-1案例：结果是几？

```js
  <script>
    function fn1() {
      var num = 123;
      function fn2() {
        console.log(num);
      }
      fn2();
    }
    var num = 456;
    fn1();    //print: 123
  </script>
```

##### 10.3.2-2案例：结果是几？

```js
  <script>
    var a = 1;
    function fn1() {
      var a = 2;
      var b = '22';
      fn2();
      function fn2() {
        var a = 3;
        fn3();
        function fn3() {
          var a = 4;
          console.log(a);         //print: 4
          console.log(typeof a);  //print: Number
          console.log(b);         //print: '22'
          console.log(typeof b);  //print: String
        }
      }
    }
    fn1();  //print: a: 4  b: '22'
  </script>
```

### 11.预解析

```js
  <script>
    // 1 问
    console.log(num);	//print: Uncaught ReferenceError: num is not defined
    // 2 问
    console.log(num); //print: undefined 坑 1
    var num = 20;
    // 3 问 
    fn();             //print: 11
    function fn() {
      console.log(11);
    }
    // 4 问
    fun();            //print: Uncaught TypeError: fun is not a function 坑 2
    var fun = function() {
      console.log(22)
    }
  </script>
```

#### 11.1预解析

JavaScript代码是由浏览器中的JavaScript解析器来执行的。JavaScript解析器在运行JavaScript代码的时候分为两步：预解析和代码执行

+ 预解析：js引擎会把js里面所有的 var 还有 function 提升到当前作用域的最前面
+ 代码执行：按照代码书写的顺序从上往下执行
+ 函数表达式    调用必须写在函数表达式的下面

#### 11.2变量预解析和函数预解析

预解析分为：变量预解析（变量提升）和	函数预解析（函数提升）

+ 变量提升：就是把所有的变量声明提升到当前的作用域最前面	不提升赋值操作	
+ 函数提升：就是把所有的函数声明提升到当前的作用域最前面    不调用函数

#### 11.3预解析案例

##### 11.3.1结果是几？

```js
  <script>
    var num = 10;
    fun();    //print: undefined
    function fun() {
      console.log(num);
      var num = 20;
    }
  </script>
```

##### 11.3.2结果是几？

```js
  <script>
    var num = 10;
    function fn() {
      console.log(num);   //print: undefined
      var num = 20;     
      console.log(num);   //print: 20
    }
    fn();
  </script>
```

##### 11.3.3结果是几？

```js
  <script>
    var a = 18;
    f1();
    function f1() {
      var b = 9;
      console.log(a);   //print: undefined
      console.log(b);   //print: 9
      var a = '123';
    }
  </script>
```

##### 11.3.4结果是几？

```js
  <script>
    f1();
    console.log(c);   //print: 9
    console.log(b);   //print: 9
    console.log(a);   //print: Uncaught ReferenceError: a is not defined
    function f1() {
      var a = b = c = 9; // 相当于 var a = 9; b = 9; c = 9; b 和 c 直接赋值 没有var声明 当全局变量看
      // 集体声明：var a = 9, b = 9, c = 9;
      console.log(a); //print: 9
      console.log(b); //print: 9
      console.log(c); //print: 9
    }
  </script>
```

### 12.对象

#### 12.1对象

##### 12.1.1什么是对象？

在JavaScript中，对象是一组无序的相关属性和方法的集合，所有的事物都是对象，例如字符串、数值、数组、函数等。

对象是由**属性**和**方法**构成的。

+ 属性：事物的**特征**，在对象中用**属性**来表示（常用名词）
+ 方法：事物的**行为**，在对象中用**方法**来表示（常用动词）

##### 12.1.2为什么需要对象？

保存一个值时，可以使用**变量**，保存多个值（一组值）时，可以使用**数组**。如果保存一个人的完整信息呢？

JS中的对象表达结构更清晰，更强大

#### 12.2创建对象的三种方式

在JavaScript中，现阶段我们可以采用三种方式创建对象（object）。

+ 利用**字面量**创建对象
+ 利用**new Object**创建对象
+ 利用**构造函数**创建对象

##### 12.2.1利用字面量创建对象

**对象字面量**：就是花括号{ }里面包含了表达这个具体事物（对象）的属性和方法。

语法结构：

```js
  <script>
    // var obj = {}; //创建一个空的对象
    var obj = {
      uname: '张三疯',
      age: 18,
      sex: '男',
      sayHi: function() {
        console.log('Hi~');
      }
    }
  </script>
```

+ 里面的属性或者方法我们采用键值对的形式		键（属性名）：值（属性值）
+ 多个属性或者方法中间用逗号隔开的
+ 方法冒号后面跟的是一个匿名函数

使用对象：

+ 1、调用对象的属性	我们采取对象名 . 属性名	. 我们理解为“的”

+ ```js
  	<script>
  		console.log(obj.uname);
  	</script>
  ```

+ 2、调用属性还有一种方法    对象名[ '属性名' ]

+ ```js
    <script>
      console.log(obj['uname']);
    </script>
  ```

+ 3、调用对象的方法    sayHi。  对象名 . 方法名( )    千万别忘记添加小括号

+ ```js
    <script>
      obj.sayHi();
    </script>
  ```

##### 12.2.2课堂案例：请按照要求写出对象。

请用对象字面量的形式创建一个名字为可可的狗对象。

具体信息如下：

+ 姓名：可可
+ 类型（type）：阿拉斯加犬
+ 年龄：5岁
+ 颜色：棕色
+ 技能：汪汪汪（bark），演电影（showFilm）

```js
  <script>
    var dog = {
      dogName: '可可',
      type: '阿拉斯加犬',
      age: 5,
      color: '棕色',
      bark: function() {
        console.log('汪汪汪');
      },
      showFilm: function() {
        console.log('演电影');
      } 
    }
    console.log(dog.dogName);
    console.log(dog.type);
    console.log(dog.age + '岁');
    console.log(dog.color);
    dog.bark();
    dog.showFilm();
  </script>
```

##### 12.2.4变量、属性、函数、方式总结（解惑）

变量和属性的相同点：

​		它们都是用来存储数据的

变量和属性的不同点：

​		变量：单独声明并赋值	使用的时候直接写变量名	单独存在

​		属性：在对象里面的不需要声明的	使用的时候必须是	对象 . 属性

函数和方法的相同点：

​		都是实现某种功能	做某件事

函数和方法的不同点：

​		函数：单独声明并调用	函数名( )	单独存在

​		方法：在对象里面	调用的时候	对象 . 方法名( )

##### 12.2.5利用new Object创建对象

跟我们之前学的new Array( ) 原理一致

语法结构：

```js
  <script>
    var obj = new Object(); // 创建了一个空的对象
    obj.uname = '张三疯';
    obj.age = 18;
    obj.sex = '男';
    obj.sayHi = function () {
      console.log('Hi~');
    };
    console.log(obj.uname);
    console.log(obj['sex']);
    obj.sayHi();
  </script>
```

+ 我们是利用	等号赋值的方法	添加对象的属性和方法
+ 每个属性和方法之间用    分号结束

##### 12.2.6课堂案例：请按照要求写出对象

请用new Object形式创建一个鸣人对象

具体信息如下：

+ 姓名：鸣人
+ 性别：男
+ 年龄：19岁
+ 技能（skill）：影分身术

```js
  <script>
    var person = new Object();
    person.uname = '鸣人';
    person.sex = '男';
    person.age = 19;
    person.skill = function() {
      console.log('影分身术');
    }
    console.log(person.uname);
    console.log(person.sex);
    console.log(person['age'] + '岁');
    person.skill();
  </script>
```

##### 12.2.7利用构造函数创建对象

我们为什么需要使用构造函数

就是因为我们前面两种创建对象的方式一次只能创建一个对象

因为我们一次创建一个对象，里面很多的属性和方法是大量相同的	我们只能复制

因此我们可以利用函数的方法	重复这些相同的代码	我们就把这个函数称为 构造函数

又因为这个函数不一样，里面封装的不是普通代码，而是	对象

构造函数	就是把我们对象里面一些相同的属性和方法抽象出来封装到函数里面

**构造函数**：是一种特殊的函数，主要用来初始化对象，即为对象成员变量赋初始值，它总与new运算符一起使用。我们可以把对象中一些公共的属性和方法抽取出来，然后封装到这个函数里面。

语法结构：

```js
  <script>
    function 构造函数名() {
      this.属性 = 值;
      this.方法 = function() {};
    }
    new 构造函数名();
  </script>
```

```js
  <script>
    // 我们需要创建四大天王的对象 相同的属性：名字  年龄  性别    相同的方法：唱歌
    // 构造函数：
    function Star(uname, age, sex) {
      this.name = uname;
      this.age = age;
      this.sex = sex;
      this.sing = function (song) {
        console.log(song);
      }
    }
		// 对象：
    var ldh = new Star('刘德华', 18, '男'); // 调用函数返回的是一个对象
    // console.log(typeof ldh);
    console.log(ldh.name);
    console.log(ldh['sex']);
    ldh.sing('冰雨');
    var zxy = new Star('张学友', 19, '男');
    console.log(zxy.name);
    console.log(zxy['age']);
  </script>
```

+ 构造函数的名字首字母要大写
+ 我们构造函数不需要return  就可以返回结果
+ 我们调用构造函数  必须使用 new
+ 我们只要new Star()  调用函数就创建一个对象  ldh  {}
+ 我们的属性和方法前面必须添加  this

##### 12.2.8课堂案例：请按照要求创建对象

利用构造函数创建两个英雄对象。函数中的公共部分包括：姓名属性(name)，类型属性(type)，血量属性(blood)和攻击属性(attack)。

英雄对象的信息如下：

+ 廉颇	力量型	500血量	攻击：近战
+ 后裔    射手型    100血量    攻击：远程

```js
  <script>
    function Hero(name, type, blood, attack) {
      this.name = name;
      this.type = type;
      this.blood = blood;
      this.attack = attack;
    }
    var lp = new Hero('廉颇', '力量型', 500, '近战');
    console.log(lp.name);
    console.log(lp.type);
    console.log(lp.blood + '血量');
    console.log(lp.attack);
    var hy = new Hero('后裔', '射手型', 100, '远程');
    console.log(hy.name);
    console.log(hy.type);
    console.log(hy.blood + '血量');
    console.log(hy.attack);
  </script>
```

##### 12.2.9构造函数和对象

+ 构造函数，如Stars()，抽象了对象的公共部分，封装到了函数里面，它泛指某一大类（class）
+ 创建对象，如new Stars()，特指某一个，通过new关键字创建对象的过程我们也称为对象实例化

构造函数：泛指的某一大类    它类似于java语言里面的类（class）

对象： 特指   是一个具体的事物。

我们利用构造函数创建对象的过程我们也称之为对象的实例化

#### 12.3new关键字

执行过程：

1、new构造函数可以在内存中创建一个空的对象

2、this就会指向刚才创建的空对象

3、执行构造函数里面的代码	给这个空对象添加属性和方法

4、返回这个对象（所以构造函数里面不需要return）

#### 12.4遍历对象属性

**for...in 语句**用于对数组或者对象的属性进行循环操作

语法结构：

```js
  <script>
    for (变量 in 对象) {
      
    }
  </script>
```

```js
  <script>
    var obj = {
      name: 'pink老师',
      age: 18,
      sex: '男',
      fn: function() {
        
      }
    }
    // console.log(obj);
    for (var k in obj) {
      console.log(k); // k 变量 输出  得到的是 属性名
      console.log(obj[k]);  // obj[k] 得到的是  属性值
    }
  </script>
```

我们使用for...in 里面的变量	我们喜欢写 k 或者 key

#### 12.5对象小结

1、对象可以让代码结构更清晰

2、对象复杂数据类型object

3、本质：对象就是一组无序的相关属性和方法的集合

4、构造函数泛指某一大类，比如苹果，不管是红苹果还是绿苹果，都统称为苹果

5、对象实例特指一个事物，比如这个苹果，正在给你们讲课的pink老师等

6、for...in 语句用于对对象的属性进行循环操作

#### 12.6作业

1、创建一个对象，该对象要有颜色、重量、品牌、型号，可以看电影、听音乐、打游戏和敲代码。

```js
  <script>
    function Obj(color, weight, brand, type) {
      this.color = color;
      this.weight = weight;
      this.brand = brand;
      this.type = type;
      this.showFilm = function() {
        console.log('看电影');
      };
      this.sing = function() {
        console.log('听音乐');
      };
      this.playGame = function() {
        console.log('打游戏');
      };
      this.typeCode = function() {
        console.log('敲代码');
      };
    };
    var obj = new Obj();
  </script>
```

2、创建一个按钮对象，该对象需要包含宽、高、背景颜色和点击行为。

```js
  <script>
    function Button(width, height, bgcolor) {
      this.width = width;
      this.height = height;
      this.bgcolor = bgcolor;
      this.onclick = function() {
        console.log('点击行为');
      };
    };
    var btn = new Button();
  </script>
```

3、创建一个车的对象，该对象要有重量、颜色、可以载人、拉货和耕田。

```js
  <script>
    function Car(weight, color) {
      this.weight = weight;
      this.color = color;
      this.Manned = function() {
        console.log('可载人');
      };
      this.pullgoods = function() {
        console.log('可拉货');
      };
      this.ploughing = function() {
        console.log('可耕田');
      };
    };
    var car = new Car();
  </script>
```

4、写一个函数，实现反转任意数组。

```js
  <script>
    function Reverse(arr) {
      var newArray = [];
      for (var i = arr.length - 1; i >= 0; i--) {
        newArray[newArray.length] = arr[i];
      }
      return newArray;
    }
    var arr = Reverse([1, 3, 2, 4, 5]);
    console.log(arr);
  </script>
```

5、写一个函数，实现对数字数组的排序

```js
  <script>
    function Sort(arr) {
      for (var i = 0; i < arr.length - 1; i++) {
        // console.log(arr);
        for (var j = i; j < arr.length - i - 1; j++) {
          if (arr[j] > arr[j + 1]) {
            var temp = arr[j];
            arr[j] = arr[j + 1];
            arr[j + 1] = temp;
          }
        }
      }      
      return arr;
    }
    var sort = Sort([1, 44, 3, 5]);
    console.log(sort);
  </script>
```

6、小组项目：做一个简易计算器

```js
  <script>
    var choose = parseInt(prompt('欢迎使用简易计算器：\n1.加法运算：\n2.减法运算：\n3.乘法运算：\n4.除法运算：\n5.退出：\n请输入您的选项：'));
    while (choose == 1) {
      var num1 = parseInt(prompt('请输入第一个数：'));
      var num2 = parseInt(prompt('请输入第二个数：'));
      var result = num1 + num2;
      alert(result);
      var choose = parseInt(prompt('欢迎使用简易计算器：\n1.加法运算：\n2.减法运算：\n3.乘法运算：\n4.除法运算：\n5.退出：\n请输入您的选项：'));
    }
    while (choose == 2) {
      var num1 = parseInt(prompt('请输入第一个数：'));
      var num2 = parseInt(prompt('请输入第二个数：'));
      var result = num1 - num2;
      alert(result);
      var choose = parseInt(prompt('欢迎使用简易计算器：\n1.加法运算：\n2.减法运算：\n3.乘法运算：\n4.除法运算：\n5.退出：\n请输入您的选项：'));
    }
    while (choose == 3) {
      var num1 = parseInt(prompt('请输入第一个数：'));
      var num2 = parseInt(prompt('请输入第二个数：'));
      var result = num1 * num2;
      alert(result);
      var choose = parseInt(prompt('欢迎使用简易计算器：\n1.加法运算：\n2.减法运算：\n3.乘法运算：\n4.除法运算：\n5.退出：\n请输入您的选项：'));
    }
    while (choose == 4) {
      var num1 = parseInt(prompt('请输入第一个数：'));
      var num2 = parseInt(prompt('请输入第二个数：'));
      var result = num1 / num2;
      alert(result);
      var choose = parseInt(prompt('欢迎使用简易计算器：\n1.加法运算：\n2.减法运算：\n3.乘法运算：\n4.除法运算：\n5.退出：\n请输入您的选项：'));
    }
    if (choose == 5) {
      alert('正在退出');
    }
  </script>
```

### 13.内置对象

#### 13.1内置对象

+ JavaScript中的对象分为3种：自定义对象、内置对象、浏览器对象

+ 前面两种对象是JS基础内容，属于ECMAScript；第三个浏览器对象属于我们JS独有的，我们 JS API讲解
+ **内置对象**就是指 JS语言自带的一些对象，这些对象供开发者使用，并提供了一些常用的或是最基本而必要的功能（属性和方法）

+ 内置对象最大的优点就是帮助我们快速开发
+ JavaScript提供了多个内置对象：Math、Date、Array、String等

#### 13.2查文档

##### 13.2.1 MDN

学习一个内置对象的使用，只要学会其常用成员的使用即可，我们可以通过查文档学习，可以通过MDN/W3C来查询

Mozilla开发者网络（MDN）提供了有关开放网络技术（Open Web）的信息，包括HTML、CSS和万维网及HTML5应用的API

MDN：https://developer.mozilla.org/zh-CN/

##### 13.2.2如何学习对象中的方法

1、查阅该方法的功能

2、查看里面参数的意义和类型

3、查看返回值的意义和类型

4、通过demo进行测试

#### 13.3Math对象

##### 13.3.1概述

Math数学对象	不是一个构造函数，所以我们不需要new来调用	而是直接使用里面的属性和方法即可

```js
  <script>
    console.log(Math.PI); // print: 3.141592653589793
    console.log(Math.max(1, 3, 5)); // print: 5
    console.log(Math.max(1, 3, 6, 'pink老师')); // print: NaN
    console.log(Math.max());  // print: -Infinity
  </script>
```

##### 13.3.2案例：封装自己的数学对象

利用对象封装自己的数学对象 里面有PI最大值和最小值

```js
  <script>
    var myMath = {
      PI: 3.141592653,
      max: function() {
        var max = arguments[0];
        for(var i = 1; i < arguments.length; i++) {
          if (arguments[i] > max) {
            max = arguments[i];
          }
        }
        return max;
      },
      min: function() {
        var min = arguments[0];
        for(var i = 1; i < arguments.length; i++) {
          if (arguments[i] < min) {
            min = arguments[i];
          }
        }
        return min;
      }
    }
    console.log(myMath.PI);
    console.log(myMath.max(1, 3));
    console.log(myMath.min(1, 3));
  </script>
```

##### 13.3.3 abs（绝对值）方法

```js
  <script>
    // 1、绝对值方法
    console.log(Math.abs(-1));  // print: 1
    console.log(Math.abs(1));  // print: 1
    console.log(Math.abs('-1'));  // print: 1   隐式转换  会把字符串型  -1  转换为数字型
    console.log(Math.abs('pink'));  // print: NaN
  </script>
```

##### 13.3.4 floor（向下取整）方法

```js
  <script>
    // 向下取整
    console.log(Math.floor(1.1)); // print: 1
    console.log(Math.floor(1.9)); // print: 1
  </script>
```

##### 13.3.5 ceil（向上取整）方法

```js
  <script>
    // 向上取整
    console.log(Math.ceil(1.1)); // print: 2
    console.log(Math.ceil(1.9)); // print: 2
  </script>
```

##### 13.3.6 round（四舍五入）方法	其他数字都是四舍五入，但是 .5 特殊	它往大了取

```js
  <script>
    // 向上取整
    console.log(Math.round(1.1)); // print: 1
    console.log(Math.round(1.5)); // print: 2
    console.log(Math.round(1.9)); // print: 2
		console.log(Math.round(-1.1)); // print: -1
		console.log(Math.round(-1.5)); // print: -1
  </script>
```

##### 13.3.7 random（随机数）方法

+ random()	返回一个随机的小数	0 <= x < 1

+ 这个方法里面不跟参数

+ 代码验证：

+ ```js
    <script>
      console.log(Math.random());
    </script>
  ```

+ 我们想要得到两个数之间的随机整数  并且  包含这2个整数

+ ```js
    <script>
      function getRandom(min, max) {
        return Math.floor(Math.random() * (max - min + 1)) + min;
      }
      console.log(getRandom(1, 10));
    </script>
  ```

案例：随机点名

```js
  <script>
    function getRandom(min, max) {
      return Math.floor(Math.random() * (max - min + 1)) + min;
    }
    // console.log(getRandom(1, 10));
    var arr = ['张三丰', '张三', '李四', 'pink老师', '王五'];
    console.log(arr[getRandom(0, arr.length - 1)]);
  </script>
```

##### 13.3.8案例：猜数字游戏

程序随机生成一个1～10之间的数字，并让用户输入一个数字

1、如果大于该数字，就提示，数字大了，继续猜；

2、如果小于该数字，就提示，数字小了，继续猜；

3、如果等于该数字，就提示，猜对了，结束程序。

```js
  <script>
    function getRandom(min, max) {
      return Math.floor(Math.random() * (max - min + 1)) + min;
    }
    var random = getRandom(1, 10);
    while (true) {
      var num = prompt('你来猜? 输入1～10之间的整数');
      if (num > random) {
        alert('数字大了，继续猜');
      } else if (num < random) {
        alert('数字小了，继续猜');
      } else {
        alert('你猜对了');
        break;
      }
    }
  </script>
```

##### 13.3.9课下作业：要求用户猜数字

要求用户猜1～50之间的一个数字，但是只有10次猜的机会

```js
  <script>
    function getRandom(min, max) {
      return Math.floor(Math.random() * (max - min + 1)) + min;
    }
    var random = getRandom(1, 50);
    var i;
    for (i = 1; i <= 10; i++) {
      var num = parseInt(prompt('你来猜? 输入1～50之间的整数'));
      if (num > random) {
        alert('数字大了，继续猜，你还有' + (10 - i) + '次机会');
      } else if (num < random) {
        alert('数字小了，继续猜，你还有' + (10 - i) + '次机会');
      } else {
        alert('你猜对了');
        break;
      }
    }
    if (i > 10) {
      alert('对不起，你10次机会已全部用光了');
    }
  </script>
```

#### 13.4日期对象

##### 13.4.1 Date() 概述

Date() 日期对象	是一个构造函数	必须使用new来调用创建我们的日期对象

1、使用Date

+ 如果没有参数	返回当前系统的当前时间

```js
  <script>
    var date = new Date();
    console.log(date);
  </script>
```

2、参数常用的写法：

+ 数字型	2019, 10, 01
+ 字符串型    '2019-10-1 8:8:8'

```js
  <script>
    var date1 = new Date(2019, 10, 01);
    console.log(date1); // 返回的是Nov（十一月）
    var date2 = new Date('2019-10-1 8:8:8')
    console.log(date2);
  </script>
```

##### 13.4.2日期格式化

需要获取日期指定的部分，所以我们要手动得到这种格式

| 方法名        | 说明                         | 代码               |
| ------------- | ---------------------------- | ------------------ |
| getFullYear() | 获取当年                     | dObj.getFullYear() |
| getMoth()     | 获取当月（0～11）            | dObj.getMonth()    |
| getDate()     | 获取当天日期                 | dObj.getDate()     |
| getDay()      | 获取星期几（周日0 到 周六6） | dObj.getDay()      |
| getHours()    | 获取当前小时                 | dObj.getHours()    |
| getMinutes()  | 获取当前分钟                 | dObj.getMinutes()  |
| getSeconds()  | 获取当前秒钟                 | dObj.getSeconds()  |

###### 13.4.2.1格式化日期	年月日

```js
<script>
    // 格式化日期	年月日
    var date = new Date();
    console.log(date.getFullYear());  // 返回当前日期的年
    console.log(date.getDate());       // 返回的是几号
    console.log(date.getMonth() + 1); // 返回的月份小一个月  记得月份加1
    console.log(date.getDay());       // 周一返回的是1  周六返回的是6 但是周日返回的是0
    // 我们写一个 2021年 7月 29日 星期三
    var year = date.getFullYear();
    var month = date.getMonth() + 1;
    var dates = date.getDate();
    var day = date.getDay();
    var arr = ['星期日', '星期一', '星期二', '星期三', '星期四', '星期五', '星期六',];
    console.log('今天是' + year + '年' + month + '月' + dates + '日' + arr[day]);  
  </script>
```

###### 13.4.2.2格式化日期	时分秒

```js
  <script>
    var date = new Date();
    console.log(date.getHours());   // 时
    console.log(date.getMinutes()); // 分
    console.log(date.getSeconds()); // 秒
    // 要求封装一个函数返回当前的时分秒 格式 08:08:08
    function getTimer() {
      var time = new Date();
      var h = time.getHours();
      var m = time.getMinutes();
      var s = time.getSeconds();
      h = h < 10 ? '0' + h : h;
      m = m < 10 ? '0' + m : m;
      s = s < 10 ? '0' + s : s;
      return h + ':' + m + ':' + s;
    }
    console.log(getTimer());
  </script>
```

##### 13.4.3获取日期的总的毫秒形式

Date对象是基于1970年1月1日（世界标准时间）起的毫秒数

为什么计算机起始时间从1970年开始？

我们经常利用总的毫秒数来计算时间，因为他更准确

```js
  <script>
    // 获得Date总的毫秒数（时间戳） 不是当前时间的毫秒数  而是距离1970年1月1号过了多少毫秒数
    // 1、通过valueOf() getTime()
    var date = new Date();
    console.log(date.valueOf());  // 就是 我们现在的时间 距离1970.1.1 总的毫秒数
    console.log(date.getTime());
    // 2、简单的写法
    var date1 = +new Date();  // +new Date() 返回的就是总的毫秒数
    console.log(date1);
    // 3、H5 新增的 获得总的毫秒数
    console.log(Date.now());
  </script>
```

##### 13.4.4案例：倒计时效果

做一个倒计时效果。

案例分析：

​	转换公式如下：

+ d = parseInt(总秒数/60/60/24);	//计算天数
+ h = parseInt(总秒数/60/60%24);	//计算小时
+ m = parseInt(总秒数/60%60);	//计算分数
+ s = parseInt(总秒数%60);	//计算当前秒数

```js
  <script>
    function countDown(time) {
      var nowTime = +new Date();  // 返回的是当前时间总的毫秒数
      var inputTime = +new Date(time);  // 返回的是用户输入时间总的毫秒数
      var times = (inputTime - nowTime) / 1000;  // times是剩余时间总的秒数
      var d = parseInt(times/60/60/24);
      d = d < 10 ? '0' + d : d;
      var h = parseInt(times/60/60%24);
      h = h < 10 ? '0' + h : h;
      var m = parseInt(times/60%60);
      m = m < 10 ? '0' + m : m;
      var s = parseInt(times%60);
      s = s < 10 ? '0' + s : s;
      return d + '天' + h + '时' + m + '分' + s + '秒';
    }
    console.log(countDown('2021-7-30 1:10:00'));
  </script>
```

#### 13.5数组对象

##### 13.5.1数组对象的创建

创建数组对象的两种方式：

+ 字面量方式
+ new Array()

```js
  <script>
    var arr1 = new Array(2);  // 这个2表示数组长度为2 里面有2个空的数组元素
    console.log(arr1);
    var arr2 = new Array(2, 3); // 等价于 [2, 3] 这样写表示 里面有2个数组元素 是 2和3
    console.log(arr2);
  </script>
```

##### 13.5.2检测是否为数组

###### 13.5.2-1 instanceof	运算符	他可以用来检测是否为数组

```js
  <script>
    var arr = [];
    var obj = {};
    console.log(arr instanceof Array);
    console.log(obj instanceof Object);
  </script>
```

```js
  <script>
    function reverse(arr) {
      if (arr instanceof Array) {
        var new_arr = [];
        for (var i = arr.length - 1; i >= 0; i--) {
          new_arr[new_arr.length] = arr[i];
        }
        return new_arr; 
      } else {
        return 'error 这个参数要求必须是数组格式 [1, 2, 3]';
      }
    }
    var arr1 = reverse([1, 2, 5, 6, 9]);
    console.log(arr1);
    var arr2 = reverse(1, 2, 3);
    console.log(arr2);
  </script>
```

###### 13.5.2-2 Array.isArray(参数);

```js
  <script>
    var arr = [];
    var obj = {};
    // Array.isArray(参数);  H5新增的方法   ie9以上才支持
    console.log(Array.isArray(arr));  // print: true
    console.log(Array.isArray(obj));  // print: false
  </script>
```

当检测Array实例时，Array.isArray优于instanceof，因为Array.isArray能检测iframes。

##### 13.5.3添加删除数组元素的方法

| 方法名            | 说明                                                   | 返回值               |
| ----------------- | ------------------------------------------------------ | -------------------- |
| push(参数1...)    | 末尾添加一个或多个元素，注意修改原数组                 | 并返回新的长度       |
| pop()             | 删除数组最后一个元素，把数组长度减1 无参数、修改原数组 | 返回它删除的元素的值 |
| unshift(参数1...) | 向数组的开头添加一个或更多元素，注意修改原数组         | 并返回新的长度       |
| shift()           | 删除数组的第一个元素，数组长度减1无参数、修改原数组    | 并返回第一个元素的值 |

###### 13.5.3-1 push() 

```js
  <script>
    var arr = [1, 2, 3];
    // arr.push(4, 'pink');
    console.log(arr);
    console.log(arr.push(4, 'pink'));
  </script>
```

+ push()  是可以给数组元素追加新的元素

+ push()  参数直接写，数组元素就可以了
+ push完毕之后，返回的结果是  新数组的长度
+ 原数组也会发生变化

###### 13.5.3-2 unshift()

```js
  <script>
    var arr = [1, 2, 3];
    // arr.unshift('red', 'purple');
    console.log(arr);
    console.log(arr.unshift('red', 'purple'));
  </script>
```

+ 在我们数组的开头，添加一个或者多个数组元素
+ unshift()  是可以给数组前面追加新的元素

+ unshift()  参数直接写，数组元素就可以了
+ unshift完毕之后，返回的结果是  新数组的长度
+ 原数组也会发生变化

###### 13.5.3-3 pop()

```js
  <script>
    var arr = [1, 2, 3];
    // arr.pop();
    console.log(arr);
    console.log(arr.pop());
  </script>
```

+ pop()  是可以删除数组的最后一个元素    记住一次只能删除一个元素

+ pop()  没有参数
+ pop完毕之后，返回的结果是  删除的那个元素
+ 原数组也会发生变化

###### 13.5.3-4 shift()

```js
  <script>  
		var arr = [1, 2, 3];
    // arr.shift();
    console.log(arr);
    console.log(arr.shift());
  </script>
```

+ shift()  是可以删除数组的第一个元素    记住一次只能删除一个元素

+ shift()  没有参数
+ shift完毕之后，返回的结果是  删除的那个元素
+ 原数组也会发生变化

##### 13.5.4案例：筛选数组

有一个包含工资的数组[1500, 1200, 2000, 2100, 1800]，要求把数组中工资超过2000的删除，剩余的放到新数组里面

```js
  <script>
    var arr = [1500, 1200, 2000, 2100, 1800];
    var newArr = [];
    for (var i = 0; i < arr.length; i++) {
      if (arr[i] < 2000) {
        newArr.push(arr[i]);
      }
    }
    console.log(newArr);
  </script>
```

##### 13.5.5数组排序

| 方法名    | 说明                         | 是否修改原数组                     |
| --------- | ---------------------------- | ---------------------------------- |
| reverse() | 颠倒数组中元素的顺序，无参数 | 该方法会改变原来的数组  返回新数组 |
| sort()    | 对数组的元素进行排序         | 该方法会改变原来的数组  返回新数组 |

###### 13.5.5-1 reverse()

```js
  <script>
    var arr = ['pink', 'red', 'blue'];
    arr.reverse();
    console.log(arr);
  </script>
```

###### 13.5.5-2 sort()

```js
  <script>
    var arr = [3, 4, 7, 1];
    arr.sort();
    console.log(arr); //print: [1, 3, 4, 7]
    var arr1 = [1, 3, 4, 13, 76, 7];
    arr1.sort();
    console.log(arr1);  // print: [1, 13, 3, 4, 7, 76]
    arr1.sort(function(a, b) {
      // return a - b;   // 升序的顺序排列
      return b - a;     // 降序的顺序排列
    });
    console.log(arr1);  // print: [76, 13, 7, 4, 3, 1]
  </script>
```

##### 13.5.6数组索引方法

| 方法名            | 说明                           | 返回值                                   |
| ----------------- | ------------------------------ | ---------------------------------------- |
| indexOf(数组元素) | 数组中查找给定元素的第一个索引 | 如果存在返回索引号  如果不存在，则返回-1 |
| lastIndexOf()     | 在数组中的最后一个的索引       | 如果存在返回索引号  如果不存在，则返回-1 |

###### 13.5.6-1 indexOf()

```js
  <script>
    // indexOf(数组元素)	作用：就是返回该数组元素的索引号	从前面开始查找
    // 它只返回第一个满足条件的索引号
    var arr = ['red', 'green', 'blue', 'pink', 'pink'];
    var arr1 = ['red', 'green', 'blue', 'pink', 'pink'];
    console.log(arr1.indexOf('pink'));  // print: 3
    console.log(arr.indexOf('black'));  // print: -1
  </script>
```

###### 13.5.6-2 lastIndexOf()

```js
  <script>
    // lastIndexOf(数组元素)	作用：就是返回该数组元素的索引号  从后面开始查找
    // 它只返回第一个满足条件的索引号
    var arr = ['red', 'green', 'blue', 'pink', 'pink'];
    var arr1 = ['red', 'green', 'blue', 'pink', 'pink'];
    console.log(arr.lastIndexOf('pink')); // print: 4
    console.log(arr.lastIndexOf('black')); // print: -1z
  </script>
```

##### 13.5.7案例：数组去重（重点案例）

有一个数组['c', 'a', 'z', 'a', 'x', 'a', 'x', 'c', 'b']，要求去除数组中重复的元素

```
  <script>
    function unique(arr) {
      var newArr = [];
      for (var i = 0; i < arr.length; i++) {
        if (newArr.indexOf(arr[i]) === -1 ) {
          newArr.push(arr[i]);
        }
      }
      return newArr;
    }
    var demo = unique(['c', 'a', 'z', 'a', 'x', 'a', 'x', 'c', 'b']);
    console.log(demo);
  </script>
```

##### 13.5.8数组转换为字符串

| 方法名         | 说明                                       | 返回值         |
| -------------- | ------------------------------------------ | -------------- |
| toString()     | 把数组转换成字符串，逗号分隔每一项         | 返回一个字符串 |
| join('分隔符') | 方法用于把数组中的所有元素转换为一个字符串 | 返回一个字符串 |

###### 13.5.8-1 toString()

```js
  <script>
    var arr = [1, 2, 3];
    console.log(arr.toString());  // print: 1,2,3
    console.log(typeof arr.toString()); // print: string
  </script>
```

###### 13.5.8-2 join('分隔符')

```js
  <script>
    var arr = ['green', 'blue', 'pink'];
    console.log(arr.join());  // print: green,blue,pink
    console.log(arr.join('-')); // print: green-blue-pink
    console.log(arr.join('&')); // print: green&blue&pink
  </script>
```

##### 13.5.9课下查询

| 方法名   | 说明                                   | 返回值                                         |
| -------- | -------------------------------------- | ---------------------------------------------- |
| concat() | 连接两个或多个数组，不影响原数组       | 返回一个新的数组                               |
| slice()  | 数组截取slice(begin, end)              | 返回被截取项目的新数组                         |
| splice() | 数组删除splice(第几个开始, 要删除个数) | 返回被删除项目的新数组  注意：这个会影响原数组 |

###### 13.5.9-1 concat()

```js
  <script>
    var arr = ['green', 'blue', 'pink'];
    console.log(arr.concat('black')); // print: ["green", "blue", "pink", "black"]
    console.log(arr.concat('black', 1)); // print: ["green", "blue", "pink", "black", 1]
    console.log(arr); // print: ["green", "blue", "pink"]
  </script>
```

###### 13.5.9-2 slice()

```js
  <script>
    var arr = ['green', 'blue', 'pink', 'black'];
    console.log(arr.slice(1, 2)); // print: ["blue"]
    console.log((arr.slice(0, 2))); // print: ["green", "blue"]
    console.log(arr.slice(1, 1));  // print: []
    console.log(arr.slice(3, 5)); // print: ["black"]
    console.log(arr.slice(5, 8)); // print: []
    console.log(arr); // print: ["green", "blue", "pink", "black"]
  </script>
```

###### 13.5.9-3 splice()  (重点掌握)

```js
  <script>
    var arr = ['green', 'blue', 'pink', 'black', 'yellow'];
    console.log(arr.splice(0, 2)); // print: ["green", "blue"]
    console.log(arr); // print: ["pink", "black", "yellow"]
    console.log(arr.splice(5, 2)); // print: []
    console.log(arr); // print: ["pink", "black", "yellow"]
    console.log(arr.splice(-1, 1)); // print: ["yellow"]
    console.log(arr); // print: ["pink", "black"]
    console.log(arr.splice(-1, 3)); // print: ["black"]
    console.log(arr); // print: ["pink"]
  </script>
```

#### 13.6字符串对象

##### 13.6.1基本包装类型

为了方便操作基本数据类型，JavaScript还提供了三种特殊的引用类型：String、Number和Boolean

**基本包装类型**就是把简单数据类型包装成为复杂数据类型，这样基本数据类型就有了属性和方法。

**执行过程**：

```js
var str = 'andy';
console.log(str.length);
```

对象才有属性和方法	复杂数据类型才有属性和方法

简单数据类型为什么会有length属性呢？

基本包装类型：就是把简单数据类型包装成为了复杂数据类型

（1）把简单数据类型包装成复杂数据类型

```js
var temp = new String('andy');
```

（2）把临时变量的值	给	str

```js
str = temp;
```

（3）销毁这个临时变量

```js
temp = null;
```

##### 13.6.2字符串的不可变

指的是里面的值不可变，虽然看上去可以改变内容，但其实是地址变了，内存中开辟了一个内存空间

字符串不可变，所以**不要大量拼接字符串**。

##### 13.6.3根据字符返回位置

字符串所有的方法，都不会修改字符串本身（字符串是不可变的），操作完成会返回一个新的字符串。

| 方法民                              | 说明                                                         |
| ----------------------------------- | ------------------------------------------------------------ |
| indexOf('要查找的字符', 开始的位置) | 返回指定内容在原字符串中的位置，如果找不到就返回-1，开始的位置是index索引号 |
| lastIndexOf()                       | 从后往前找，只找第一个匹配的                                 |

```js
  <script>
    var str = '改革春风吹满地，春天来了';
    console.log(str.indexOf('春')); // print: 2
    console.log(str.indexOf('春', 3)); // print: 8
    console.log(str.length); // print: 12
    console.log(str.lastIndexOf('春', 9));  // print: 8
    console.log(str.lastIndexOf('春', 8));  // print: 8
    console.log(str.lastIndexOf('春', 7));  // print: 2
  </script>
```

##### 13.6.4案例：返回字符位置

查找字符串"abcoefoxyozzopp"中所有o出现的位置以及次数

```js
  <script>
    var str = "abcoefoxyozzopp";
    var index = str.indexOf('o');
    var num = 0;
    while (index !== -1) {
      console.log(index);
      index = str.indexOf('o', index + 1);
      num++;
    }
    console.log(num);
  </script>
```

##### 13.6.5课后作业

有这样一个数组['red', 'blue', 'red', 'green', 'pink', 'red']，求这个red出现的位置和次数

```js
  <script>
    function getString(str) {
      var num = 0;
      var index = str.indexOf('red');
      while (index !== -1) {
        console.log(index);
        index = str.indexOf('red', index + 1);
        num++
      }
      console.log('red出现的次数：' + num);
    }
    var arr = ['red', 'blue', 'red', 'green', 'pink', 'red'];
    var str = arr.toString();
    console.log(str);
    getString(str);
  </script>
```

##### 13.6.6根据位置返回字符（重点）

| 方法名            | 说明                                     | 使用                          |
| ----------------- | ---------------------------------------- | ----------------------------- |
| charAt(index)     | 返回指定位置的字符(index字符串的索引号)  | str.charAt(0)                 |
| charCodeAt(index) | 获取指定位置的字符的ASCII码(index索引号) | str.charCodeAt(0)             |
| str[index]        | 获取指定位置的字符                       | HTML5, IE8+支持和charAt()等效 |

```js
  <script>
    var str = 'andy';
    console.log(str.charAt(3));   // print: y
    for (var i = 0; i < str.length; i++) {
      console.log(str.charAt(i));
    }
    console.log(str.charCodeAt(0));   // print: 97
    for (var i = 0; i < str.length; i++) {
      console.log(str.charCodeAt(i));
    }
    console.log(str[0]);    // print: a
    for (var i = 0; i < str.length; i++) {
      console.log(str[i]);
    }
  </script>
```

##### 13.6.7案例：返回字符位置

判断一个字符串'abcoefoxyozzopp'中出现次数最多的字符，并统计其次数。

1、核心算法：利用charAt()遍历这个字符串

2、把每个字符串存储给对象，如果对象没有该属性，就为1，如果存在就+1

3、遍历对象，得到最大值和该字符

```js
  <script>
    // 回顾小知识点
    // 有一个对象 来判断是否有该属性  对象 ['属性名']
    var obj = {
      age: 18
    }
    if (obj['sex']) {
      console.log('里面有该属性');
    } else {
      console.log('里面没有该属性');
    }
  </script>
```

```js
  <script>
    var str = 'abcoefoxyozzopp';
    var obj = {};
    for (var i = 0; i < str.length; i++) {
      var chars = str.charAt(i);
      if(obj[chars]) {
        obj[chars]++;
      } else {
        obj[chars] = 1;
      }
    }
    // console.log(obj);
    var max = 0;
    var ch = '';
    for (var k in obj) {
      // k 得到的是 属性名
      // o[k] 得到的是 属性值
      if (obj[k] > max) {
        max = obj[k];
        ch = k;
      }
    }
    console.log(ch);
    console.log(max);
  </script>
```

##### 13.6.8字符串操作方法（重点）

| 方法名                      | 说明                                                         |
| --------------------------- | ------------------------------------------------------------ |
| concat(str1, str2, str3...) | concat()方法用于连接两个或多个字符串。拼接字符串，等效于+，+更常用 |
| substr(start, length)       | 从start位置开始（索引号），length取的个数  **重点**记住这个  |
| slice(start, end)           | 从start位置开始，截取到end位置，end取不到（他两都是索引号）  |
| substring(start, end)       | 从start位置开始，截取到end位置，end取不到，基本和slice相同  但是不接受负值 |

```js
  <script>
    // concat()
    var str = 'andy';
    console.log(str.concat('red')); // print: andyred
		// substr()
    var str1 = '改革春风吹满地';
    console.log(str1.substr(2, 2)); // print: 春风
  </script>
```

##### 13.6.9替换字符串以及转换为数组

1、替换字符 replace('被替换的字符', '替换为的字符')	他只会替换满足条件的第一个字符

```js
  <script>
    var str = 'andyandy';
    console.log(str.replace('a', 'b')); // print: bndyandy
    // 有一个字符串 'abcoefoxyozzopp' 要求把里面所有的'o'替换为'*'
    var str1 = 'abcoefoxyozzopp';
    while (str1.indexOf('o') !== -1) {
      str1 = str1.replace('o', '*');
    }
    console.log(str1);
  </script>
```

2、字符转换为数组 split('分隔符')	前面我们学过 join 把数组转换为字符串

```js
  <script>
    var str = 'red, pink, blue';
    console.log(str.split(', '));
    var str1 = 'red&pink&blue';
    console.log(str1.split('&'));
  </script>
```

##### 13.6.10课下查询

+ toUpperCase()		转换大写

+ toLowerCase()        转换小写

```js
  <script>
    var str = 'I\'m Hero!';
    console.log(str.toUpperCase()); // print: I'M HERO!
    console.log(str.toLowerCase()); // print: i'm hero!
  </script>
```

### 14.简单和复杂数据类型

#### 14.1简单类型和复杂类型

简单类型又叫做基本数据类型或者**值类型**，复杂类型又叫做**引用类型**

+ 值类型：简单数据类型/基本数据类型，在存储时变量中存储的是值本身，因此叫做值类型

  string，number，boolean，undefined，null

```js
  <script>
    // 简单数据类型 null  返回的是一个空的对象  object
    var timer = null;
    console.log(typeof timer); // print: object
    // 如果有个变量我们以后打算存储为对象，暂时没想好放啥，这个时候就给null
  </script>
```

+ 引用类型：复杂数据类型，在存储时变量中存储的仅仅是地址（引用），因此叫做引用数据类型

  通过new关键字创建的对象（系统对象、自定义对象），如Object、Array、Date等

#### 14.2堆和栈

堆栈空间分配区别：

1、栈（操作系统）：由操作系统自动分配释放存放函数的参数值、局部变量的值等。其操作方式类似于数据结构中的栈；
	  **简单数据类型存放到栈里面**

2、堆（操作系统）：存储复杂类型（对象），一般由程序员分配释放，若程序员不释放，由垃圾回收机制回收。
	  **复杂数据类型存放在堆里面**

**注意：JavaScript中没有堆栈的概念，通过堆栈的方式，可以让大家更容易理解代码的一些执行方式，便于将来学习其他语言。**

#### 14.3简单类型的内存分配

+ 值类型（简单数据类型）：string，number，boolean，undefined，null
+ 值类型变量的数据直接存放在变量（栈空间）中

#### 14.4复杂类型的内存分配

+ 引用类型（复杂数据类型）：通过new关键字创建的对象（系统对象、自定义对象），如Object、Array、Date等
+ 引用类型变量（栈空间）里存放的是地址，真正的对象实例存放在堆空间中

#### 14.5简单类型传参

函数的形参也可以看作是一个变量，当我们把一个值类型变量作为参数传给函数的形参时，其实是把变量在栈空间里的值复制了一份给形参，那么在方法内部对形参做任何修改，都不会影响到的外部变量。

```js
  <script>
    function fn(a) {
      a++;
      console.log(a); // print: 11
    }
    var x = 10;
    fn(x);
    console.log(x); // print: 10
  </script>
```

#### 14.6复杂类型传参

函数的形参也可以看作是一个变量，当我们把引用类型变量传给形参时，其实是把变量在栈空间里保存的堆地址复制给了形参，形参和实参其实保存的是同一个堆地址，所以操作的是同一个对象。

```js
  <script>
    function Person(name) {
      this.name = name;
    }
    function f1(x) {        // x = p
      console.log(x.name);  // print: 刘德华
      x.name = '张学友';
      console.log(x.name);  // print: 张学友
    }
    var p = new Person('刘德华');
    console.log((p.name));  // print: 刘德华
    f1(p);
    console.log(p.name);    // print: 张学友
  </script>
```

