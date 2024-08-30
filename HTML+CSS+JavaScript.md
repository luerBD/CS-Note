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

## 4.1 基础

```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>01.javascript是一门弱类型的脚本语言</title>
    <script language="JavaScript">
        //javascript是一门弱类型的运行在客户端的解释型的语言
        //java:
        /*
        String str = "hello world";
        Integer num = 0 ;
        num ="hello";//编译报错，因为num是Integer类型，不能赋值字符串
        //因此，java是强类型语言
        */
        var str = "hello world" ;       //var表示准备定义一个变量  variable：变量
        alert(typeof(str));             //alert表示弹出一个对话框  , typeof表示返回变量的数据类型
        str = 99 ;
        alert(typeof(str));             //弹出了number，表示str又变成了数值类型
        str=true;
        alert(typeof(str));             //弹出了boolean,表示str又变成了布尔类型
        //因此，我们知道，js是弱类型语言。
        //变量的数据类型由赋的值来决定
    </script>
</head>
<body>

</body>
</html>
```

## 4.2 方法

```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>02.javascript中的方法</title>
    <script language="JavaScript">
        //javascript和java没有关系。一个是客户端脚本语言，一个是服务器端编译型语言
        //但是又感觉有点关系，因为两者的API非常相似。

        /*
        //java中定义方法
        public String sayHello(String name){
            if("jim".equals(name)){
                return "hello to " + name ;
            }else{
                System.out.println("hi");//有问题，这个路径没有return
            }
        }
        访问修饰符  返回值类型  方法名(参数签名){
            方法主体
        }
        方法调用时，有参数必须传参，而且要求严格：个数、类型必须匹配
                   有返回值，那么定义时，必须有return，而且是所有的路径都必须有
        */
        /*
        //js中定义方法
        function是一个关键字，表示开始定义方法
        sayHello是方法名,name是形参
         */
        function sayHello(name){
            return "hello to " + name;
        }

        //方法调用
        //var str = sayHello("jim")
        //var str = sayHello();
        //var str = sayHello("jim","tom");
        //alert(str);

        function sayHello2(num1 , num2){
            if(num1>num2){
                return 99;
            }else{
                alert("hello world!");
            }
        }

        //sayHello2(1,2);
        alert(sayHello2(2,1));


    </script>
</head>
<body>

</body>
</html>
```

## 4.3 事件

```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>03.javascript中的事件</title>
    <script language="JavaScript">
        //事件：event
        //事件源：事件发生在哪个对象上
        //常见的事件：点击事件、鼠标悬浮事件、键盘摁下事件等等
        function hello(){
            alert('hello world!');
        }
    </script>
</head>
<body>
    <input type="button" value="HELLO" onclick="hello()"/>  <!--onclick:当点击时 -->
</body>
</html>
```

## 4.4 JS中if条件为什么值时表示true，if条件为什么值时表示false

- Java语言中，if(flag)，要求flag时布尔类型

- 在JS语言中，if(flag)

  - flag为null、0，表示false
  - flag不为null、非0，表示true

  ```
  // 如果event不为null（也就是说存在），而且事件源存在，而且事件源是TD
  if(event && event.srcElement && event.srcElement.tagName=="TD"){
  
  }
  ```

  
