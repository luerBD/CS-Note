# 1.Web前端介绍

web前端主要由三个部分组成：

- HTML:全称HyperTextMarkupLanguage超文本标记语言，用来搭建页面的结构

  - 超文本:超级文本，除了普通的文本文字以外，还能显示图片，音频，视频，超链接甚至应用程序等。

  - 标记语言:使用标签对文字进行标记，让普通的文本文字显示更加高级的效果。

  - HTML学习的内容就是标签的意义。

- CSS: 全称CascadingStyleSheet层叠样式表，用来对页面进行美化
  - 字体、背景、颜色、位置等属性

- JavaScript:用来和用户实现交互

  - ECMAScript: JS语法基础

  - DOM:文档对象模型,使用S代码操作页面上的标签(了解)

  - BOM:浏览器对象模型，使用JS代码操作浏览器上的功能(了解)

  - 基于JS的前端框架:

    - Vue前端页面渲染技术

    - axios异步网络请求

# 2.HTML

## 2.1 注释

```
<!-- -->
```

## 2.2 HTML介绍

```html
<!DOCTYPE html>  <!-- HTML5的文档类型声明，类似于JDK的版本 -->
<html lang="en">  <!-- HTML文档的根标签，一个HTML文档有且仅有一个根标签，所有的内容都要在这个根标签里 -->
<head>  <!-- 头标签，通常会设置字符集,标题,CSS,JS等 -->
    <meta charset="UTF-8">
    <title>hello</title>
</head>
<body>  <!-- 存放HTML的主体结构 -->
Hello world
<h1>我是一级标题</h1>
</body>
</html>
```

## 2.3 结构标签

这类标签一般对于文档的结构会有一定的影响，主要包含一下几个标签:

- h系列标签:用来显示一个标题。
- p标签:用来显示一个段落
- hr标签:用来显示一个分割线
- br标签:用来进行换行。
- div标签:无语义，块级元素，自己独占一行，配合CSS来进行界面布局。
- span标签:无语义，行内元素，自己不独占一行，配合CSS对指定的文字设置样式。

## 2.4 超链接和图片标签

### 2.4.1 超链接标签

```
<a href="http://www.baidu.com">百度一下</a>
```

- a是标签名

- href属性，用来表示a标签链接的地址
  - 可以链接到一个外部的地址，如果是一个外部地址，要写完成的URL路径 http://www.atguigu.com
  - 还可以是一个内部的文件
    - 如果href链接到的文件，浏览器认识，会直接显示；如果浏览器不认识，会下载
- target属性 用来表示超链接的打开方式
  - _self 表示在当前选显卡里打开链接(默认值)
  - _blank 开启一个新的选项卡显示页面

### 2.4.2 图片标签

img标签: 用来在页面上显示一张图片

- src 属性，用来表示图片的地址
- alt 属性，当图片加载失败时，显示的文字提示

## 2.5 列表标签

### 2.5.1 无序列表UnorderedList（掌握）

标签没有序号，通常用来表示没有逻辑先后顺序的列表

ul和ol里的列表项使用  li标签   ListItem

```
<ul>
  <li>啤酒</li>
  <li>咖啡</li>
  <li>可乐</li>
  <li>矿泉水</li>
  <li>雪碧</li>
</ul>
```

### 2.5.2 有序列表OrderedList（了解）

```
<ol type="1" start="5">
  <li>穿衣服</li>
  <li>洗漱</li>
  <li>吃早餐</li>
  <li>坐地铁</li>
</ol>
```

### 2.5.3 自定义列表DefinitionList（了解）

```
<dl>
  <dt>CPU</dt>
  <dd>中央处理器</dd>
</dl>
```

## 2.6 表格标签

使用table标签表示一个表格

使用 tr表示一行数据

th 表示表头

td 表示单元格里的数据

```
<table>
    <caption>成绩单</caption>

    <tr>
        <th>姓名</th>
        <th>性别</th>
        <th>年龄</th>
        <th>语文</th>
        <th>数学</th>
        <th>英语</th>
    </tr>

    <tr>
        <td>张三</td>
        <td rowspan="2">男</td>
        <td>18</td>
        <td>96</td>
        <td>98</td>
        <td>89</td>
    </tr>
    <tr>
        <td>jack</td>
        <td>19</td>
        <td>94</td>
        <td>99</td>
        <td>82</td>
    </tr>
    <tr>
        <td>merry</td>
        <td>女</td>
        <td>18</td>
        <td colspan="2">96</td>
        <td>95</td>
    </tr>


    <tr>
        <td>总分</td>
        <td></td>
        <td></td>
        <td>286</td>
        <td>290</td>
        <td>295</td>
    </tr>

</table>
```

## 2.7 表单相关标签

### 2.7.1 form标签

form表单用来向服务器提交一段数据,例如:注册表单，登录表单

- action属性: 表单提交的地址

- method属性: 请求的处理方式，常见的可选值 GET/POST  默认值是GET

- GET主要用来从服务器获取到数据;POST用来向服务器传入数据

### 2.7.2 label标签

和input标签配合使用，当点击label标签时，会选中对应的input标签

- for属性: 用来指定这个label标签和哪个input关联了

### 2.7.3 input标签

用来接收用户的输入

- name属性: 作用有两个
  - 当input标签是单选框时，设置相同的name属性，可以让单选框实现联动
  - 如果想要向服务器提交数据，必须要设置 name属性

- value属性:作用分为两种场景
  - 当input标签的显示效果是一个按钮时，value表示按钮上显示的内容
  - 如果input标签可以输入内容，value表示文本输入框里的内容
  - 当向服务器发送数据时，会以 name=value 形式的键值对将数据发送到服务器

- type属性:可选值很多

  - text: 用来显示一个普通的输入框

  - submit: 用来将form表单里的数据发送给服务器，只有input标签放在了form表单里才能提交表单

  - image: 使用一张图片作为 提交按钮

  - password: 显示一个密码输入框

  - number: 用来限制用户只能输入数字

  - radio: 显示一个单选框

  - checkbox:显示一个复选框

  - tel: 只在移动端有效，当点击input标签时，弹出拨号键盘

  - email: 当提交数据时，会判断数据是否是正确的邮箱格式

  - reset: 将form表单里的input标签设置为默认值

- form属性: 当 input标签不在form表单里，可以设置 form属性用来指定提交的表单

- alt属性: 当input标签的type属性值是image时，图片加载失败时显示的提示文字

- src属性: 当input标签的type属性值是 image时，src属性用来指定图片的路径

- min/max属性: 当type的值为number时，用来设定最小/最大值
- placeholder 属性: 用来设置输入框里的提示文字，如果指定了内容以后，提示文字就看不到了
- readonly属性: 标记值只读
- disabled属性: 禁用输入框,不能修改，不能点击，也不会向服务器提交
- required属性: 表示字段为必填项
- list属性: 用来和一个 datalist 的 id匹配，显示一个输入下拉框

### 2.7.4 其他标签

- select标签: 用来显示一个下拉选择框
- datalist标签: 需要配合 input标签的list属性共同使用
- option标签: 用在select或者datalist标签里，用来显示待选项
- selected属性用来设置选中

## 2.8 标签的属性

HTML学习的主要内容是标签，学习的标签名，标签属性名和标签的属性值

同一个标签，给它设置不同的属性，它的显示效果就可能会不同

例如: input标签的type属性不同，显示的效果也不同

### 2.8.1 全局属性

所有的标签都可以设置的属性，尽管有些设置以后没有效果

- id: 给标签添加一个唯一标识,在整个HTML页面里，id应该是唯一的
- class: 用来给标签分类，主要是配合CSS对页面设置样式
- title: 设置鼠标悬停时的实现文字
- style: 用来给标签设置CSS行内样式

### 2.8.2 标签特有的属性

- a标签的属性:
  - href属性: 用来设置链接的路径
  - target属性: 用来设置链接的打开方式
- img标签的属性:
  - src属性: 用来设置图片的路径
  - alt属性: 图片加载失败时显示文字
- ul/ol属性:
  - type属性: 用来显示有序/无序列表的显示方式
- form属性:
  - action属性: 用来表示提交的地址
  - method属性: 用来表示提交的方式
- input属性:
  - type属性...

### 2.8.3 自定义属性

可以给标签添加我们自定义的属性，作用是让其携带某些值，方便后期获取。

# 3.CSS

## 3.1 CSS的基本使用

- CSS全称CascadingStyleSheet层叠样式表,用来给标签设置样式

- CSS学习主要是两大内容:

  - 找到标签 - CSS选择器

  - 给标签设置样式 - CSS的属性

- CSS有三种使用方式:
    - 行内样式: 直接给标签添加 style 属性

    - 内部样式: 在 head标签里添加 style标签，在style标签里设置属性

    - 外部样式: 在 head标签里使用link标签，设置href属性引入一个外部的css文件

## 3.2 CSS基本选择器的使用

在内部样式或者外部样式里，如果想要给标签设置样式，第一步需要通过CSS选择器查找到这个标签

基本选择器:

通配符选择器(*) < 标签选择器(标签名)  < 类选择器(.类名) < id选择器(#id名) < 行内样式 < !important

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
    <style>
        div {
            color: red;
        }
        span {
            background-color: #0f0;
            color: yellow;
        }
        .marvel {
            color: blue !important;
        }
        #spider-man {
            font-size: 26px;
            color: red;
        }
        * {
            text-decoration: underline;
            color: cyan;
        }
    </style>
</head>
<body>
<!--
在内部样式或者外部样式里，如果想要给标签设置样式，第一步需要通过CSS选择器查找到这个标签
基本选择器:
通配符选择器(*) < 标签选择器(标签名)  < 类选择器(.类名) < id选择器(#id名) < 行内样式 < !important
-->
<div>我是一个div</div>
<span class="marvel">雷神</span>
<span class="dc">超人</span>
<span class="kenan">柯南</span>
<span class="marvel">钢铁侠</span>
<span class="dc">海王</span>
<span class="marvel" id="spider-man" style="color:purple">蜘蛛侠</span>
<span class="kenan">小兰</span>
<p>我是一个p</p>
<ul>
    <li>啤酒</li>
    <li>咖啡</li>
    <li>矿泉水</li>
</ul>
</body>
</html>
```

## 3.3 隐藏的样式

```css
.cityOfChina{
    display: block;
    /*display: none;*/
}
```

## 3.4 文本的装饰样式

```css
#text{
    /*text-decoration: underline;*/
    /*text-decoration: overline;*/
    text-decoration: line-through;
    text-decoration: none;
}
```

## 3.5 列表样式

```css
ul{
    /*list-style-type: none;*/
    /*list-style-type: circle;*/
    list-style-type: square;
}
```

## 3.6 设置鼠标悬停效果

hover是专门用来设置鼠标悬停效果的

注意：hover在使用的时候，这个冒号两边都是不允许有空格的。

```
span:hover{
	color:red;	
}
```

## 3.7 内外补丁

```
padding
margin
```

## 3.8 float浮动样式

```css
img{
	/*float:left;*/
	float:right;
}
```

## 3.9 定位

```
#div1{
    width:300px;
    height:300px;
    background-color: orange;
    position: absolute;
    top:30px;
    left:30px;
}
```

## 3.10 光标样式

```
div{
	cursor:pointer;
}
```

# 4.JS

## 4.1 概述

- JS是一种脚本语言（解释型语言），Java语言是一种非脚本语言，属于编译型语言。
- 脚本语言的特点：JavaScript 的“目标程序”是以普通文本的形式保存。用记事本是可以直接打开的。浏览器打开就直接解释执行了。

- JavaScript主要用来操作HTML中的节点，产生动态效果。
- JavaScript 和Java 的区别
  - JavaScript运行在浏览器当中，浏览器中有执行JS代码的内核。。
  - Java运行在JVM当中。JavaScript 和Java没有任何关系。。
  - Java语言是SUN公司开发的，JavaScript 这个名字是SUN公司给起的名。

## 4.2 JavaScript包括三块: ECMAScript、 DOM、BOM

- ECMAScript 是ECMA制定的262标准，JavaScript 和JScript都遵守这个标准，ECMAScript 是JavaScript核心语法
- DOM编程是通过JavaScript对HTML中的dom节点进行操作, DOM是有规范的, DOM规范是W3C制定的。(DocumentObject Model:文档对象模型)。
- BOM编程是对浏览器本身操作，例如:前进、后退、地址栏、关闭窗口、弹窗等。由于浏览器有不同的厂家制造，所以BOM缺少规范，一般只是有一个默认的行业规范。(Browser Object Model:浏览器对象模型)。

## 4.3 在HTML中嵌入JS代码的三种方式

### 4.3.1 方式1：行间事件

- JavaScript是一 种事件驱动型的编程语言，通常都是在发生某:个事件的时候，去执行某段代码。其中事件包括很多，例如:鼠标单击事件click，另外还有其它事件，例如: mouseover是鼠标经过事件等。并且在JavaScript当中任何一个事件都有对应的事件句柄。例如: click对应的事件句柄是onclick，mouseover对 应的事件句柄是onmouseover。

  - 所有的事件句柄都是以标签的属性形式存在。例如以下input button就有一个onclick这样属性。

    ```html
    <input type="button" onclick="注册在onclick事件句柄当中的JS代码"/>
    ```

  - 只要有用户点击了以下的这个按钮对象，此时按钮对象上发生了鼠标单击事件，那么注册在onclick事件句柄当中的JS代码会被执行! onclick后面代码实际上是浏览器负责执行的。

  - onclick="后面的代码"并不是在浏览器打开的时候执行，浏览器打开的时候，只是将这个代码注册给onclick事件句柄了。等待该按钮的click事件发生，只要发生，后面代码会被事件监听器调用。

- 怎么使用JS代码弹窗?

  - 在JS当中有一个内置的BOM对象：window，window可以直接拿来使用，全部小写。

  - 其中window对象有一个方法/函数叫做alert()，这个函数专门用来弹出对话框!

  - 弹窗的JS代码

    ```
    window.lert('hello world!'); 
    ```

    - 通过这个代码可以知道: JS中的字符串可以使用单引号括起来，也可以使用双引号。

      ```
      <input type="button" value="hello1" onclick="window.alert('hello world!')">
      <input type="button" value="hello2" onclick='window.alert("hello world!")'>
      ```

    - JS中的一条语句可以“;”结尾，也可以不以“;”结尾。

      ```
      <input type="button" value="hello1" onclick="window.alert('hello world!');">
      <input type="button" value="hello2" onclick='window.alert("hello world!");'>
      <input type="button" value="hello3" onclick="   window.alert('hello world1!')
                                                      window.alert('hello world2!')
                                                      window.alert('hello world3!')
                                                      window.alert('hello world4!')
      ">
      ```

      

### 4.3.2 方式2：页面script标签嵌入

script标签可以放在HTML页面的任意位置。

```
<script type="text/javascript">
    alert("hello");
    alert("world");
</script>
```

### 4.3.3 方式3：外部引入

- script标签可以放在HTML页面的任意位置。

  ```
  <script type="text/javascript" src="js/1.js"></script>
  ```

- 外部引入方式中，script这对标签中间写的代码不会执行，因此也不建议这样做。

  ```
  <script type="text/javascript" src="js/1.js">
  	//script这对标签中间写的代码不会执行，因此也不建议这样做
  </script>
  ```

## 4.4 标识符和关键字

- 标识符命名规则和规范按照java执行；
- 关键字不需要刻意记忆。

## 4.5 变量

### 4.5.1 变量的声明与赋值

- 声明

  ```
  var 变量名;
  var i;
  ```

- 赋值

  ```
  变量名 = 值;
  i = 100;
  ```

- 一行可声明多个变量

  ```
  var a, b, c = 300;
  
  //声明3个变量，a b c,并且c赋值300，其中a和b变量没有赋值，系统默认赋值undefined
  //undefined在JS中一个具体的值，这个值就是undefined
  ```

- 注意

  - JS语言是一种弱类型语言，没有编译阶段，直接浏览器打开解释执行，在JS中声明变量时不需要指定变量的数据类型，程序在运行过程当中，赋什么类型的值，变量就是什么数据类型，并且变量的数据类型是可变的。

    ```
    var i;
    i = 100; //到这里i是整数型
    i = false; //到这里i就是布尔类型了
    ```

  - 变量声明了，但是没有手动赋值，系统默认赋值undefined。

  - 变量没有声明，直接访问，这个时候会报错。（用F12可以查看控制台的错误信息）

### 4.5.2 函数的定义与调用

- 定义方式1

  ```
  // 方式1
  function fun1(a, b){
  	return a + b;
  }
  alert(fun1(3, 4));
  ```

- 定义方式2

  ```
  // 方式2
  var fun2 = function (a, b){
  	return a + b;
  }
  alert(fun2(3, 4));
  ```

- 注意：

  - 以下方式也可以，因为函数声明的优先级比较高，打开网页的时候，网页中所有的函数先进行声明。

    ```
    fun();
    var fun = function (){ // 函数声明
    	alert("hello");
    }
    ```

  - 在JS中的函数是不能重载的，也不存在重载机制

    - JS中的函数只要出现同名函数,之前的函数就消失了。
    - 注意在JS中编写函数名的时候，谨慎一些 ,以防将其他函数干掉!

### 4.5.3 全局和局部变量

- 全局变量:

  - 在函数体之外声明的变量，叫做全局变量。

  - 全局变量在浏览器打开的时候分配空间，直到浏览器关闭的时候才会销毁。

  - 注意

    在javascript当中，如果一个变量声明的时候没有使用var关键字的话，这个变量不管是在哪里声明的，都是全局变量。这种全局变量在声明的时候必须手动赋值，不能采用系统默认值。

- 局部变量:

  - 在函数体当中声明的变量，叫做局部变量。
  - 局部变量在函数被调用的时候分配空间，函数执行结束之后，内存释放。

### 4.5.4 数据类型

- ES6之前的数据类型包括6种

  ```
  原始类型（或基本数据类型）
      Undefined
      Number
      String
      Boolean
      Null
      
  引用数据类型（或对象类型）
  	Object
  ```

- ES6之后引入了其他的类型（知道就行）

  ```
  Symbol
  BigInt
  ```

- 注意：ES6之后是8种类型，ES6之前是6种类型；

- typeof运算符：获取变量数据类型

  ```
  typeof 变量名
  ```

  - typeof的运算结果为以下6个字符串之一（都是小写）

    ```
    "undefined"
    "number"
    "string"
    "boolean"
    "object"
    "function"
    ```

- 在JS种判断两个字符串是否相等，应该使用“==”，JS中没有equals函数；

- 原始类型（或基本数据类型）

  - Undefined

    - 只有一个值：undefined
    - 当一个变量声明之后没有手动赋值，系统赋默认值undefined

  - Null

    - 只有一个值：null
    - 注意：`typeof null`运算结果是`object`

  - Number

    - 值：整数、小数、NaN、Infinity

    - NaN详解

      - Not a Number，表示不是一个数字。

      - 但NaN是一个值，它属于Number类型

      - 什么情况下结果是一个NaN？

        - 当一个数学表达式的运算结果本应该返回一个数字，但是最终结果无法返回一个数字的时候，结果是NaN。

      - isNaN()函数

        ```
        isNaN(数据)
        ```

        - 返回布尔类型，true表示是不是一个数字，false表示是一个数字
        - 特点：首先尝试将“数据”转换成数字，如果转换失败，结果就是true。如果转换成功，结果就是false。

    - Infinity详解

      - 表示无穷大
      - 当除数是0的时候，最终计算结果是无穷大。

    - Number()函数

      ```
      Number(数据)
      ```

      - 将`不是数字类型的数据`转换成`数字类型的数据`

    - parseInt()函数

      ```
      parseInt("字符串数字")
      ```

      - 将字符串数字转换成数字，并且向下取整；

    - Math.ceil()函数

      ```
      Math.ceil(数字)
      ```

      - 向上取整

  - Boolean

    - 只有两个值：true、false；

    - Boolean()函数

      ```
      Boolean(非布尔类型的数据)
      ```

      - 将非布尔类型的数据转换成布尔类型
      - 该函数我们一般不手动调用，它会在if(`Boolean(非布尔类型的数据`))隐式调用，侧面说明if语句中只能是true或false
  
  - String
  
    - JS中定义字符串的两种方式
  
      ```
      var s = "字符串";	// typeof s 为 String
      var s = new String("字符串");	// typeof s 为 Object
      ```
  
    - String当中的常用属性和方法
  
      - 常用属性
  
        ```
        length属性：获取字符串长度
        ```
  
      - 常用方法
  
        ```
        charAt()：获取指定下标位置的字符
        concat()：连接字符串
        indexof()：获取某个字符串在当前字符串中第一次出现处的索引
        lastIndexOf()：获取某个字符串在当前字符串中最后一次出现处的索引
        replace()：替换
        split()：拆分字符串
        substr(startIndex, length)：截取字符串，从几取几
        substring(startIndex, endIndex)：截取字符串，不包括结束下标所指向的
        toLowerCase()：转小写
        toUpperCase()：转大写
        ```

- 引用数据类型（或对象类型）
  - Object
    - 在JS当中内置了一个类型object，可以将object类型看做是所有对象的超类/基类。
    - 在JS当中默认定义的类型，没有特殊说明的话，默认继承object.
    - object类型中有哪些通用属性和方法呢?
      - 属性
        - prototype
        - constructor
      - 方法
        - toLocaleString()
        - toString()
        - valueOf()
      - 重点掌握：prototype属性
        - prototype翻译为原型，该属性可以给对象动态扩展属性和方法。

## 4.6 类

### 4.6.1 类的定义

- 方式1

  ```
  function 类名(形式参数列表){
  	this.属性名 = 参数;
  	this.属性名 = 参数;
  	
  	this.方法名 = function(){
  	
  	}
  }
  ```

  ```
  	// 类的定义方式1
      // function Emp(name, age, sal){
      //     this.name = name;
      //     this.age = age;
      //     this.sal = sal;
      //     this.showInfo = function (){
      //         console.log(this.name + ", " + this.age + ", " + this.sal);
      //     }
      // }
  ```

  

- 方式2

  ```
  类名 = function(形式参数列表){
  	this.属性名 = 参数;
  	this.属性名 = 参数;
  	
  	this.方法名 = function(){
  	
  	}
  }
  ```

  ```
      //类的定义方式2
      Emp = function (name, age, sal){
          this.name = name;
          this.age = age;
          this.sal = sal;
          this.showInfo = function (){
              console.log(this.name + ", " + this.age + ", " + this.sal);
          }
      }
  ```

  

### 4.6.2 对象的创建

```

    
    //对象的创建
    var emp = new Emp("joker", 18, 2000);
    
    //属性的访问方式1
    // console.log(emp.name);
    // console.log(emp.age);
    // console.log(emp.sal);

    //属性的访问方式1
    console.log(emp["name"]);
    console.log(emp["age"]);
    console.log(emp["sal"]);

    //方法的调用
    emp.showInfo();
```

## 4.7 null、undefined和NaN区别

### 4.7.1 `==` 和 `===` 的区别

- `==`等同运算符：只比较值是否相等。
- `===`全等运算符：既比较值是否相等，同时又比较数据类型是否相同。

### 4.7.2 null、undefined和NaN区别

- 类型都是不一样的
- null和undefined是等同关系

## 4.8 JS中的事件

### 4.8.1 常用事件

(1) blur失去焦点
(5) focus获得焦点
(3) click鼠标单击
(4) dblclick鼠标双击
(6) keydown键盘按下
(7) keyup键盘弹起
(9) mousedown鼠标按下
(10) mouseover鼠标经过
(11) mousemove鼠标移动
( 12) mouseout 鼠标离开
(13) mouseup 鼠标弹起
(16) submit表单提交
(14) reset表单重置
(15) select文本被选定
(2) change下拉列表选中项改变，或文本框内容改变
(8) 1oad页面加载完毕

### 4.8.2 注册事件的两种方式

在HTML中根据id获取节点

```
var v = document.getElementById("id名");
```

- 注册事件的第一种方式：在标签中使用“事件句柄”，在事件句柄后面编写JS代码
  - 当这个事件句柄对应的事件发生之后，“注册"在事件句柄当中的这个代码被监听器调用。
- 注册事件的第二种方式：在页面加载完毕后使用JS代码给元素绑定事件

### 4.8.3 代码的执行顺序

页面加载过程中，实际上是各种事件的绑定，把相应的回调函数绑定到该事件对应的事件句柄上。

等这些事件一个一个发生后，回调函数统一都是由监听器来负责调用的。

load事件，当页面所有元素加载完毕后触发该事件。

以后代码写成以下形式：

```html
<script type="text/javascript">

    window.onload = function (){
        document.getElementById("btn1").onclick = function (){
            console.log("按钮1的单击事件执行了！");
        }
        document.getElementById("btn2").onclick = function (){
            console.log("按钮2的单击事件执行了！");
        }
    }

</script>
```



### 4.8.4 通过keydown事件演示回车键13，ESC键27

我们在匿名函数中写一个obj，obj表示事件对象（绑定了该事件的控件对象），我们通过事件对象可以获取键盘按键的ascii码；

```
    window.onload = function (){
        document.getElementById("txt").onkeydown=function (obj){
            if(obj.keyCode == 13){
                console.log("登录,正在进行身份认证，请稍后！");
            }else if(obj.keyCode == 27){
                console.log("安全退出系统了！");
            }
        }
    }
```

## 4.9 JS运算符之void

如果我们想点击一个超链接，并且不希望这个超链接发生跳转，那么写如下代码：

```
<a href="javascript:void(0)">超链接</a>
```

## 4.10 JS内置对象

### 4.10.1 Array

- 创建数组

  - 方式1

    ```
    var arr2 = [11, 22, 33, 44, true, false];
    ```

  - 方式2

    ```
    var arr3 = new Array(11, 22, 33, 44, true, false);
    ```

- 遍历数组

  ```
  for (var i = 0; i < arr3.length; i++) {
  	console.log(arr3[i]);
  }
  ```

- 修改数组中某个元素

  ```
  arr3[2] = 99;
  ```

- 读取数组中某个元素

  ```
  console.log(arr3[2]);
  ```

- Array对象中的常用函数

  - push()

  - pop()

  - join("$")

    ```
    将数组中的每一个元素和“$”连接，最后返回一个字符串
    ```

  - reverse()

### 4.10.2 Date

```
new Date()：获取当前系统时间
new Date().getTime()：获取时间戳（自“1970年1月1日 00:00:00 000”到系统当前时间的总毫秒数）

new Date().getFullYear()：获取年份
new Date().getMonth()：获取月份，要加1
new Date().getDate()：获取日
```

## 4.11 DOM

### 4.11.1 DOM和BOM的关系

BOM(Browser Object Model) 包含 DOM(Document Object Model)

```
document.getElementById()完整的写法是window.document.getElementById()
```



### 4.11.2 DOM编程案例

- 案例1：操作div和span，设置div和span标签中的内容

  ```
  <script type="text/javascript">
    window.onload = function (){
      document.getElementById("btn").onclick = function (){
        var div1 = document.getElementById("div1");
        // div1.innerHTML = "<a href='http://www.baidu.com'>百度</a>";
        div1.innerText = "<a href='http://www.baidu.com'>百度</a>";
  
      }
  
    }
  
  </script>
  <div id="div1"></div>
  <input type="button" value="操作div1" id="btn">
  ```

  - innerHTML和innerText的区别
    - innerHTML属性会将后面的字符串当作一段HTML代码解释并执行
    - innerText后面的字符串即使是一个HTML代码，也不会当作HTML执行，只是看作普通文本。

- 案例2：复选框全选和取消全选

  ```
  <script type="text/javascript">
      window.onload = function (){
          var ckFirst = document.getElementById("first")
          var hobbies = document.getElementsByName("hobbies");
          ckFirst.onclick = function (){
              for(var i = 0; i < hobbies.length; i++){
                  hobbies[i].checked = ckFirst.checked;
              }
          }
  
          for (var i = 0; i < hobbies.length; i++) {
  
              hobbies[i].onclick = function (){
                  var checkedCount = 0;
                  for(var i = 0; i < hobbies.length; i++){
                      if(hobbies[i].checked){
                          checkedCount++;
                      }
                  }
                  ckFirst.checked = (hobbies.length == checkedCount);
              }
          }
      }
  
  </script>
  
  <input type="checkbox" id="first"><br>
  <input type="checkbox" name="hobbies">抽烟 <br>
  <input type="checkbox" name="hobbies">喝酒 <br>
  <input type="checkbox" name="hobbies">烫头 <br>
  ```

- 案例3：获取一个文本框的value

  ```
  <script type="text/javascript">
      window.onload = function (){
          document.getElementById("btn").onclick = function (){
              var txt = document.getElementById("txt");
              alert(txt.value);
          }
      }
  </script>
  <input type="text" id="txt"><br>
  <input type="button" value="获取value" id="btn">
  ```

- 案例4：获取下拉列表选项中的value

  ```
  <script type="text/javascript">
      window.onload = function (){
          var province = document.getElementById("province");
          province.onchange = function (){
              console.log(this.value);
              //这里的this代表的就是当前发生change事件的这个节点对象。
          }
      }
  </script>
  <select name="" id="province">
      <option value="">--请选择--</option>
      <option value="001">河北省</option>
      <option value="002">江苏省</option>
      <option value="003">山东省</option>
      <option value="004">甘肃省</option>
  </select>
  ```

- 案例5：显示网页时钟

  ```
  <script type="text/javascript">
      window.onload = function(){
          document.getElementById("displayTimeBtn").onclick = function (){
              // 每隔1s调用一次displayTime()函数（设置周期性调用）
              // 返回值是一个可以取消周期性调用的value
              v = window.setInterval("displayTime()", 1000);
          }
          document.getElementById("stopTimeBtn").onclick = function (){
              // 停止周期性的调用
              window.clearInterval(v);
          }
      }
      function displayTime(){
          var div = document.getElementById("div");
          div.innerHTML = new Date().toLocaleString();
      }
  </script>
  <input type="button" value="显示网页时钟" id="displayTimeBtn">
  <input type="button" value="停止网页时钟" id="stopTimeBtn">
  <div id="div"></div>
  ```

### 4.11.3 BOM编程案例

- window.open()和window.close()

  ```
  <script type="text/javascript">
      window.onload = function (){
          document.getElementById("openBtn").onclick = function (){
              window.open("016.test.html", "_blank")
          }
      }
  </script>
  <input type="button" value="打开窗口" id="openBtn">
  ```

  016.test.html

  ```
  <script type="text/javascript">
    window.onload = function (){
      document.getElementById("closeBtn").onclick = function (){
        window.close();
      }
    }
  </script>
  
  
  这是一个待关闭的窗口 <br>
  <input type="button" value="关闭窗口" id="closeBtn">
  ```

- window.alert()和window.confirm()

  ```
  <script type="text/javascript">
    window.onload = function (){
      document.getElementById("delBtn").onclick = function (){
        // confirm返回一个布尔值
        if(confirm("确认删除？")){
          alert("正在删除中，请稍后！");
        }
      }
    }
  </script>
  <input type="button" value="删除" id="delBtn">
  ```

- 如果当前窗口不是顶级窗口，则将当前窗口设置为顶级窗口

  ```
  if(window.top != window.self){
  	window.top.location = window.self.location;
  }
  ```

- 历史记录

  - 后退

    ```
    window.history.back();
    ```

  - 前进

    ```
    window.history.go(1);
    ```

- 通过浏览器向服务器发送请求，通常是以上的五种方式

  - 方式1：直接在浏览器地址栏上写URL（重点）

  - 方式2：可以点击超链接（重点）

  - 方式3：提交表单（重点）

  - 方式4：window.open(url, target)（了解）

  - 方式5：js代码（重点）

    ```
    window.location.href
    window.location
    document.location.href
    document.location
    ```

## 4.12 JSON

### 4.12.1 eval()函数

可以将一个字符串当做一段JS代码解释执行

```
window.eval("var i = 100");
```

### 4.12.2 怎么创建JSON对象以及访问JSON对象的属性

- 什么是JSON?

  - JavaScript object Notation (JavaScript标记对象)，简称JSON。

  - JSON是一种轻量级的数据交换格式。

    - 什么是轻量级:
      - 体现在JSON的体积小。 虽然一个小的体积可能表示的数据很多。

    - 什么是数据交换: 

      - C语言和Java语言之间交换数据，python和Java语言之间交换数据，javascript和java之间交换数据。

      - 透露一下:在现代的开发中，能够做数据交换的，包括两个:

        - 第一个: JSON

        - 第二个: XML

          ```
          <?xml version="1.0" encoding= ="gbk"?>
          <students>
              <student>
                  <name> zhangsan </name>
                  <age>20</age>
              </student>
              <student>
                  <name> lisi </name>
                  <age>21</age>
              </student>
              <student>
              	<name>wangwu<name>
              	<age>22 </age>
              </student>
          </students>
          c语言查询数据库之后，拼接了以上的-一个xM格式的字符串。
          C语言通过网络的方式传给了Java.
          Java语言接收到这个XM字符串之后，开始解析XML，获取xML中的数据。
          这样c语言和Java语言就完成了数据的交换。
          这就是数据交换。
          而xML是一种国际上邇用的数据交换格式。
          java和c语言之间可以使用xmL交换。
          java和C++语言之间同样可以使用xML交换。
          
          XML语法严格。体积大，解析难度大。
          JSON是-一种轻量级的数据交换格式。
          C++查询数据库之后可以拼接一一个JSON格式的字符串,
          然后把JSON格式的字符串传给Java, java语 言接收到
          这个JSON格式的字符串，解析JSON取数据，这样C++
          和Java就完成了数据的交换。
          JSON同样也是一种国际化的标准的数据交换格式。
          javascript和java之间交换数据就可以使用JSON格式。
          c和Java之间交换数据同样也可以采用JSON格式。
          JSON体积小，解析方便。
          
          ```

- 在JavaScript当中，json是以对象的形式存在的。

- JSON对象的创建和使用

  - 创建

    - 语法格式

      ```
      var jsonObj = {
          "属性名" : 属性值,
          "属性名" : 属性值,
          "属性名" : 属性值,
          "属性名" : 属性值, 
          "属性名" : 属性值
      };
      ```

      - 注意：属性值可以是任意类型。
        - JSON是一种无类型的对象，直接一个大括号包起来就是一个JSON对象了。

    - 例

      ```
      var student = {
          "no" : "1001",
          "name" : "张三",
          "age" : 18,
          "gender" : true,
          "hobbies" : ["抽烟", "喝酒", "烫头"]
      };
      ```

      

  - 使用

    - 方式1

      ```
      console.log(student.no);
      console.log(student.name);
      console.log(student.age);
      console.log(student.gender);
      ```

    - 方式2

      ```
      console.log(student["no"]);
      console.log(student["name"]);
      console.log(student["age"]);
      console.log(student["gender"]);
      var hobbies = student["hobbies"];
      for(var i = 0; i < hobbies.length; i++){
      	console.log(hobbies[i]);
      }
      ```

- 注意：在JS中[]和{}有什么区别？

  - []是数组对象
  - {}是JSON对象

- JSON对象的属性也可以是JSON对象

  ```
  var student = {
      "no" : "1001",
      "name" : "joker",
      "age" : 18,
      "addr" : {"city" : "Beijing", "street" : "daxin"}
  };
  ```

  - 设计一个JSON格式的数据可以表示全班人数和每个学生信息

    ```
      var studentInfo = {
          "total" : 3,
          "data" : [{"no" : "1001", "name" : "Tom", "age" : 18}, {"no" : "1002", "name" : "Joker", "age" : 20}, {"no" : "1003", "name" : "Peter", "age" : 12}]
      }
      console.log("总人数：" + studentInfo.total);
      var data = studentInfo.data;
      for (var i = 0; i < data.length; i++) {
          console.log(data[i].no + "," + data[i].name + "," + data[i].age)
      }
    ```

    

### 4.12.3 JSON在开发中有什么用

```
// 双引号当中的是-个普通的不能再普通的字符串，这个字符串是java给我们浏览器的.
var fromJavaJSON = "{\"name\" : \"zhangsan\", \"age\" : 20}"; //这个不是json对象，是一个字符串

// 你需要将JSON格式的字符串转换成JSON对象
// eval函数的作用是：将后面的字符串当做一段JS代码解释并执行
window.eval("var stu = " + fromJavaJSON);

// 上面的代码执行结束后，等同于这里创建了一个JSON对象
/*
var stu = {
	"name" : "zhangsan",
	"age" : 20
};
*/

// 转换成JSON对象的目的是为了取数据。（这样javascript和java之间两个不同的编程语言就完成了数据的交换！）
console.log(stu.name + "," + stu.age);

```

