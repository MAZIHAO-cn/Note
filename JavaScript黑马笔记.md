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
