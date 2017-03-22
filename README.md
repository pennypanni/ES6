## ECMAScript 6 

### 参考文档
- [React速学教程(下)中的ES6](http://blog.csdn.net/fengyuzhengfan/article/details/52233582)
- [ES6入门-阮一峰](http://es6.ruanyifeng.com/#docs/let)



**模块**

在ES6中，模块的功能主要由 export 和 import 组成。每一个模块都有自己单独的作用域，模块之间的相互调用关系是通过 export 来规定模块对外暴露的接口，通过import来引用其它模块提供的接口。同时还为模块创造了命名空间，防止函数的命名冲突。

**箭头函数**

`=>`不只是关键字function的简写，它还带来了其它好处。箭头函数与包围它的代码共享同一个`this`,能帮你很好的解决this的指向问题。有经验的JavaScript开发者都熟悉诸如`var self = this`;或`var that = this`这种引用外围this的模式。但借助=>，就不需要这种模式了。

箭头函数的箭头=>之前是一个空括号、单个的参数名、或用括号括起的多个参数名，而箭头之后可以是一个表达式（作为函数的返回值），或者是用花括号括起的函数体（需要自行通过return来返回值，否则返回的是undefined）。

```javascript
// 箭头函数的例子
()=>1
v=>v+1
(a,b)=>a+b
()=>{
    alert("foo");
}
e=>{
    if (e == 0){
        return 0;
    }
    return 1000/e;
}
```

### ES5与ES6在导入与导出组件上的不同

`ES5`通过`require`导入

```javascript
var React = require("react");
```

`ES6`通过`import`导入

```javascript
import React from 'react';
```

另外，ES6支持将组件导入作为一个对象，使用`* as`修饰即可。

```javascript
//引入app目录下AboutPage组件作为一个对象，接下来就可使用“AboutPage.”来调用AboutPage的方法及属性了。  
import  * as AboutPage from './app/AboutPage' 
```

<br>
<br>

`ES5`要导出一个类给别的模块用，一般通过`module.exports`来导出

```javascript
var MyComponent = React.createClass({
    ...
});
module.exports = MyComponent;
```

`ES6`通常用`export default`来导出类

```javascript
export default class MyComponent extends Component{
    ...
}
```

### let命令

ES6新增了`let`命令，用来声明变量。它所声明的变量，只在let命令所在的代码块内有效。

for循环的循环语句部分是一个父作用域，而循环体内部是一个单独的子作用域。

```javascript
for (let i = 0; i < 3; i++) {
  let i = 'abc';
  console.log(i);
}
// abc
// abc
// abc
```
上面代码输出了3次abc，这表明函数内部的变量i和外部的变量i是分离的。

ES6明确规定，如果区块中存在`let`和`const`命令，这个区块对这些命令声明的变量，从一开始就形成了封闭作用域。凡是在声明之前就使用这些变量，就会报错。

`let不允许在相同作用域内，重复声明同一个变量。`

### const命令
const声明一个只读的常量。一旦声明，常量的值就不能改变。const一旦声明变量，就必须立即初始化，不能留到以后赋值。

const的作用域与let命令相同：只在声明所在的块级作用域内有效。