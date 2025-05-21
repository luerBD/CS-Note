# 1.ES6的变量和模板字符串

## 1.1 使用let和const声明变量

- let和var的区别
  - let不能重复声明；
  - let有块级作用域，非函数的花括号遇见let会有块级作用域（即只能在花括号里面访问）；
  - let不会预解析进行变量提升；
  - let定义的全局变量不会作为window的属性；

## 1.2 模板字符串

- 格式

  ```
  let str = `模板字符串`;
  
  let msg = 'hello';
  let str2 = `${msg}world`;
  ```

# 2.ES6的解构表达式

- 结构数组

  ```javascript
  let arr = [10, 20, 30, 40];
  let [a, b, c, d] = arr;
  console.log(a); //10
  console.log(b); //20
  console.log(c); //30
  console.log(d); //40
  ```

- 解构对象

  ```javascript
  let obj = {name:'joker', gender:'male', age:'18'};
  let {name, gender, age} = obj;
  console.log(name); // joker
  console.log(gender); // male
  console.log(age); // 18
  ```

- 方法的参数列表中可以使用解构表达式

  ```javascript
  let arr = [10, 20, 30, 40];    
  function showArr([a, b, c, d = 10]){
      console.log(a); //10
      console.log(b); //20
      console.log(c); //30
      console.log(d); //40
  }
  showArr(arr);
  
  let obj = {name:'joker', gender:'male', age:'18'};
  function showObj({name, gender, age}){
      console.log(name); // joker
      console.log(gender); // male
      console.log(age); // 18
  }
  showObj(obj);
  ```


# 3.ES6的箭头函数

- 无参数，多行代码

  - ```
    ()=>{
    	code;
    	code;
    }
    ```

- 无参数，一行代码

  - ```
    ()=>code;
    ```

- 多个参数，多行代码

  - ```
    (a, b, c)=>{
    	code;
    	code;
    }
    ```

- 多个参数，一行代码

  - ```
    (a, b, c)=>code;
    ```

- 一个参数，一行代码

  - ```
    a=>code;
    ```

    
