# 1.Vue程序初体验

## 1.1 第一个Vue程序

### 1.1.1 安装Vue

```html
<head>
    <title>第一个Vue程序</title>
    <!-- 安装vue：当你使用script进行Vue安装之后，上下文中就注册了一个全局变量：Vue -->
    <script src="../js/vue.js"></script>
</head>
```

### 1.1.2 创建Vue实例

```
const myVue = new Vue({
	template : '<h1>Hello Vue!!!!!</h1>'
})
```

- 为什么要new Vue()，直接调用Vue()函数不行吗？

  - 不行，因为直接调用Vue()函数，不创建实例的话，会出现以下错误：

    ```
     Vue is a constructor and should be called with the `new` keyword
    ```

- 关于Vue构造函数的参数：options？
  - option翻译为选项，options翻译为多个选项；
  - Vue框架要求这个options参数必须是一个纯粹的JS对象：{}
  - 在{}对象中可以编写大量的key:value对。
  - 一个key:value对就是一个配置项。
  - 主要是通过options这个参数来给Vue实例指定多个配置项。

### 1.1.3 将Vue实例挂载到id='app'的元素位置

```html
<div id="app"></div>
<script>
    const myVue = new Vue({
        template : '<h1>Hello Vue!!!!!</h1>'
    });
	myVue.$mount('#app')
</script>
```

- Vue实例都有一个$mount()方法，这个方法的作用是什么？
  - 将Vue实例挂载到指定位置.
- #app 显然是ID选择器。这个语法借鉴了CSS。

## 1.2 模板语句的数据来源

```
 new Vue({
            template : `<h1>最近非常火爆的电视剧{{name}}，它的上映日期是{{releaseTime}}。主角是{{lead.name}}，年龄是{{lead.age}}岁。
                其他演员包括：{{actors[0].name}}({{actors[0].age}}岁)，{{actors[1].name}}({{actors[1].age}}岁)。{{a.b.c.d.e.name}}
                </h1>`,
            data : {
                name : '狂飙!!!',
                releaseTime : '2023年1月2日',
                lead : {
                    name : '高启强',
                    age : 41
                },
                actors : [
                    {
                        name : '安欣',
                        age : 41
                    },
                    {
                        name : '高启兰',
                        age : 29
                    }
                ]
            }
}).$mount('#app')
```

- 谁可以给模板语句提供数据支持呢？data选项。

- data选项的类型是什么？Object | Function （对象或者函数）

- data配置项的专业叫法：Vue 实例的数据对象.（data实际上是给整个Vue实例提供数据来源的。）

- 如果data是对象的话，对象必须是纯粹的对象 (含有零个或多个的 key/value 对)

- data数据如何插入到模板语句当中？

  - {{}} 这是Vue框架自己搞的一套语法，别的框架看不懂的，浏览器也是不能够识别的。

  - Vue框架自己是能够看懂的。这种语法在Vue框架中被称为：模板语法中的插值语法。（有的人把他叫做胡子语法。）

  - 怎么用？{{data的key}}

  - 插值语法的小细节：

    ```
    {这里不能有其它字符包括空格{
    }这里不能有其它字符包括空格}
    ```

## 1.3 template配置项详解

### 1.3.1 关于template配置项

- template后面指定的是模板语句，但是模板语句中只能有一个根节点。
- 只要data中的数据发生变化，模板语句一定会重新编译。（只要data变，template就会重新编译，重新渲染）
- 如果使用template配置项的话，指定挂载位置的元素会被替换。
- 好消息：目前我们可以不使用template来编写模板语句。这些模板语句可以直接写到html标签中。Vue框架能够找到并编译，然后渲染。

### 1.3.2 关于$mount('#app')

- 也可以不使用$mount('#app')的方式进行挂载了。
- 在Vue中有一个配置项：el
- el配置项的作用？
  - 告诉Vue实例去接管哪个容器。
  - el : '#app'，表示让Vue实例去接管id='app'的容器。
  - el其实是element的缩写。被翻译为元素。

```html
<div id="myapp">
    <h1>
        hello {{actor.name}}
    </h1>
</div>
    
<script>
    new Vue({            
        data:{
            actor:{
                name: 'Joker'
            }
        },
        el:'#myapp'
    })
</script>
```

### 1.3.3 Vue实例和容器的一夫一妻制

验证：一个Vue实例可以接管多个容器吗？

不能，一个Vue实例只能接管一个容器，一旦接管到容器之后，即使后面有相同的容器，Vue也是不管的，因为Vue实例已经“取到媳妇”了。

```
<div class="myapp">{{msg}}</div>
<div class="myapp">{{msg}}</div>
<script>
        new Vue({
            el : '.myapp',
            data : {
                msg : 'hello'
            }
        });
</script>
```

这个Vue实例想去接管id=‘myapp’的容器，但是这个容器已经被上面哪个Vue接管了，他只能“打光棍了”。

```
    <div id="myapp">
        <h1>
            {{msg}}
        </h1>
    </div>
    <script>
        new Vue({
            el : '#myapp',
            data : {
                msg : 'hello'
            }
        });
        new Vue({
            el : '#myapp',
            data : {
                msg : 'joker'
            }
        });
    </script>
```



# 2.Vue核心技术

## 2.1 模板语法之插值

- 主要研究：{{这里可以写什么}}

  - 在data中声明的变量、函数等都可以。

  - 常量都可以。

  - 只要是合法的javascript表达式，都可以。

  - 模板表达式都被放在沙盒中，只能访问全局变量的一个白名单，如 Math 和 Date 等。

    ```
    'Infinity,undefined,NaN,isFinite,isNaN,' 
        'parseFloat,parseInt,decodeURI,decodeURIComponent,encodeURI,encodeURIComponent,' 
        'Math,Number,Date,Array,Object,Boolean,String,RegExp,Map,Set,JSON,Intl,' 
    'require'
    ```


## 2.2 模板语法之指令语法

- 什么是指令？有什么作用？

  - 指令的职责是，当表达式的值改变时，将其产生的连带影响，响应式地作用于 DOM。

- Vue框架中的所有指令的名字都以“v-”开始。

- 插值是写在标签体当中的，那么指令写在哪里呢？

  - Vue框架中所有的指令都是以HTML标签的属性形式存在的，例如：

    - ```
      <span 指令是写在这里的>{{这里是插值语法的位置}}</span>
      ```

    - 注意：虽然指令是写在标签的属性位置上，但是这个指令浏览器是无法直接看懂的。是需要先让Vue框架进行编译的，编译之后的内容浏览器是可以看懂的。

- 指令的语法规则：

  - 指令的一个完整的语法格式：

    - ```
      <HTML标签 v-指令名:参数="javascript表达式"></HTML标签>
      ```

    - 表达式：

      - 之前在插值语法中{{这里可以写什么}}，那么指令中的表达式就可以写什么。实际上是一样的。
      - 但是需要注意的是：在指令中的表达式位置不能外层再添加一个{{}}

    - 不是所有的指令都有参数和表达式：

      - 有的指令，不需要参数，也不需要表达式，例如：v-once
      - 有的指令，不需要参数，但是需要表达式，例如：v-if="表达式"
      - 有的指令，既需要参数，又需要表达式，例如：v-bind:参数="表达式"

- v-once 指令

  - 作用：只渲染元素一次。随后的重新渲染，元素及其所有的子节点将被视为静态内容并跳过。这可以用于优化更新性能。

- v-if="表达式" 指令

  - 作用：表达式的执行结果需要是一个布尔类型的数据：true或者false
    - true：这个指令所在的标签，会被渲染到浏览器当中。
    - false：这个指令所在的标签，不会被渲染到浏览器当中。

- v-bind指令详解

  - 这个指令是干啥的？

    - 它可以让HTML标签的某个属性的值产生动态的效果。

  - v-bind指令的语法格式：

    - ```
      <HTML标签 v-bind:参数="表达式"></HTML标签>
      ```

  - v-bind指令的编译原理？

    - 编译前：

      ```
      <HTML标签 v-bind:参数="表达式"></HTML标签>
      ```

    - 编译后：

      ```
      <HTML标签 参数="表达式的执行结果"></HTML标签>
      ```

    - 注意两项：
      - 第一：在编译的时候v-bind后面的“参数名”会被编译为HTML标签的“属性名”
      - 第二：表达式会关联data，当data发生改变之后，表达式的执行结果就会发生变化。所以，连带的就会产生动态效果。

  - v-bind因为很常用，所以Vue框架对该指令提供了一种简写方式：

    - 只是针对v-bind提供了以下简写方式：

      ```
      <img :src="imgPath">
      ```

  - 什么时候使用插值语法？什么时候使用指令？
    - 凡是标签体当中的内容要想动态，需要使用插值语法。
    - 只要向让HTML标签的属性动态，需要使用指令语法。

- v-bind和v-model的区别和联系

  - v-bind和v-model这两个指令都可以完成数据绑定。

  - v-bind是单向数据绑定。

    - data ===> 视图

  - v-model是双向数据绑定。

    - data <===> 视图

  - v-bind可以使用在任何HTML标签当中。v-model只能使用在表单类元素上，例如：

    - input标签、select标签、textarea标签。
    - 为什么v-model的使用会有这个限制呢？
      - 因为表单类的元素才能给用户提供交互输入的界面。

    - v-model指令通常也是用在value属性上面的。

  - v-bind和v-model都有简写方式：

    - v-bind简写方式：

      - ```
        v-bind:参数="表达式"    简写为      :参数="表达式"
        ```

    - 
      v-model简写方式：

      - ```
        v-model:value="表达式"  简写为      v-model="表达式"
        ```


## 2.3 初识MVVM分层思想

- MVVM是什么？
  - M：Model（模型/数据）
  - V：View（视图）
  - VM：ViewModel（视图模型）：VM是MVVM中的核心部分。（它起到一个核心的非常重要的作用。）
  - MVVM是目前前端开发领域当中非常流行的开发思想。(一种架构模式。)
  - 目前前端的大部分主流框架都实现了这个MVVM思想，例如Vue，React等。
- Vue框架遵循MVVM吗？
  - 虽然没有完全遵循 MVVM 模型，但是 Vue 的设计也受到了它的启发。
  - Vue框架基本上也是符合MVVM思想的。
- MVVM模型当中倡导了Model和View进行了分离，为什么要分离？
  - 假如Model和View不分离，使用最原始的原生的javascript代码写项目：
  - 如果数据发生任意的改动，接下来我们需要编写大篇幅的操作DOM元素的JS代码。
  - 将Model和View分离之后，出现了一个VM核心，这个VM把所有的脏活累活给做了，也就是说，当Model发生改变之后，VM自动去更新View。当View发生改动之后，VM自动去更新Model。我们再也不需要编写操作DOM的JS代码了。开发效率提高了很多。

## 2.4 通过vm可以访问哪些属性？

- 通过Vue实例都可以访问哪些属性？(通过vm都可以vm. 什么。)
  - Vue实例中的属性很多，有的以 $ 开始，有的以 _ 开始。
  - 所有以 $ 开始的属性，可以看做是公开的属性，这些属性是供程序员使用的。
  - 所有以 _ 开始的属性，可以看做是私有的属性，这些属性是Vue框架底层使用的。一般我们程序员很少使用。
  - 通过vm也可以访问Vue实例对象的原型对象上的属性，例如：vm.$delete...

## 2.5 Object.defineProperty()

- 这个方法是ES5新增的。

- 这个方法的作用是：给对象新增属性，或者设置对象原有的属性。

- 怎么用？

  - ```
    Object.defineProperty(给哪个对象新增属性, '新增的这个属性名叫啥', {给新增的属性设置相关的配置项key:value对})
    ```

- 第三个参数是属性相关的配置项，配置项都有哪些？每个配置项的作用是啥？
  - value 配置项：给属性指定值
  - writable 配置项：设置该属性的值是否可以被修改。true表示可以修改。false表示不能修改。
  - getter方法 配置项：不需要我们手动调用的。当读取属性值的时候，getter方法被自动调用。
    - getter方法的返回值非常重要，这个返回值就代表这个属性它的值。
  - setter方法 配置项：不需要我们手动调用的。当修改属性值的时候，setter方法被自动调用。
    - setter方法上是有一个参数的，这个参数可以接收传过来的值。
  - 注意：当配置项当中有setter和getter的时候，value和writable配置项都不能存在。

## 2.6 数据代理机制

- 什么是数据代理机制？

  - 通过访问 代理对象的属性 来间接访问 目标对象的属性。
  - 数据代理机制的实现需要依靠：Object.defineProperty()方法。

- ES6新特性：

  - 在对象中的函数/方法 :function 是可以省略的。

- Vue数据代理机制对属性名的要求

  - Vue实例不会给以_和$开始的属性名做数据代理。

  - 为什么？

    - 如果允许给_或$开始的属性名做数据代理的话。

      ```
      vm这个Vue实例上可能会出现_xxx或$xxx属性，
      而这个属性名可能会和Vue框架自身的属性名冲突。
      ```

  - 在Vue当中，给data对象的属性名命名的时候，不能以_或$开始。

- data可以是一个函数

  - ```javascript
    const vm = new Vue({
        el : '#app',
        data : function(){
            return {
            	msg : "hello vue!"
            };
        }
    })
    
    //: function()可以省略
    const vm = new Vue({
        el : '#app',
        data(){
            return {
            	msg : "hello vue!"
            };
        }
    })
    ```


## 2.7 Vue的事件绑定

- 回顾：指令的语法格式

  - ```
    <标签 v-指令名:参数名="表达式">{{插值语法}}</标签>
    ```

  - 表达式”位置都可以写什么？常量、JS表达式、Vue实例所管理的XXX

- 在Vue当中完成事件绑定需要哪个指令呢？v-on指令。

  - 语法格式：

    - ```
      v-on:事件名="表达式"
      ```

  - 例如：

    - ```
      v-on:click="表达式" 表示当发生鼠标单击事件之后，执行表达式。
      v-on:keydown="表达式" 表示当发生键盘按下事件之后，执行表达式。
      ```

- 在Vue当中，所有事件所关联的回调函数，需要在Vue实例的配置项methods中进行定义。

  - methods是一个对象：{}
  - 在这个methods对象中可以定义多个回调函数。

- v-on指令也有简写形式

  - v-on:click 简写为 @click
  - v-on:keydown 简写为 @keydown
  - v-on:mouseover 简写为 @mouseover

- 绑定的回调函数，如果函数调用时不需要传递任何参数，小括号()可以省略。

- Vue在调用回调函数的时候，会自动给回调函数传递一个对象，这个对象是：当前发生的事件对象。

- 在绑定回调函数的时候，可以在回调函数的参数上使用 `$event` 占位符，Vue框架看到这个 `$event` 占位符之后，会自动将当前事件以对象的形式传过去。

- 事件回调函数中的this为Vue实例vm

- methods对象中的方法可以通过vm去访问

## 2.8 事件修饰符

```
.prevent：等同于 event.preventDefault() 阻止事件的默认行为。
.stop：停止事件冒泡，等同于 event.stopPropagation()。
.once：事件只发生一次
```

## 2.9 按键修饰符

-  9个比较常用的按键修饰符：

  - ```
    .enter
    .tab （必须配合keydown事件使用。）
    .delete (捕获“删除”和“退格”键)
    .esc
    .space
    .up
    .down
    .left
    .right
    ```

- 怎么获取某个键的按键修饰符？
  - 第一步：通过event.key获取这个键的真实名字。
  - 第二步：将这个真实名字以kebab-case风格进行命名。
- 按键修饰符是可以自定义的？
  - 通过Vue的全局配置对象config来进行按键修饰符的自定义。
  - 语法规则： Vue.config.keyCodes.按键修饰符的名字 = 键值
- 系统修饰键：4个比较特殊的键ctrl、alt、shift、meta
  - 对于keydown事件来说：只要按下ctrl键，keydown事件就会触发。
  - 对于keyup事件来说：需要按下ctrl键，并且加上按下组合键，然后松开组合键之后，keyup事件才能触发。

# 3.Vue组件化

# 4.Vue与Ajax

# 5.Vuex

# 6.路由route

# 7.Vue3

###### 
