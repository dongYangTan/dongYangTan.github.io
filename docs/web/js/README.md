<!--
 * @Date: 2024-01-16 14:36:46
 * @LastEditors: tandongyang =
 * @LastEditTime: 2024-01-16 18:09:46
 * @FilePath: /dongYangTan.github.io/docs/web/js/README.md
-->

## 数组splice
splice(start, deleteCount, item1, item2, itemN)  **会对原数组修改**  
splice(开始位置, 要删除的长度, 要添加的元素)  
slice(包含该索引位置的元素, 结束提取元素的索引位置（不包含该索引位置的元素）)  **生成新数组**  
 ```
 const myFish = ["angel", "clown", "mandarin", "sturgeon"];
 const removed = myFish.splice(2, 0, "drum", "guitar"); 
 myFish ： ["angel", "clown", "drum", "guitar", "mandarin", "sturgeon"]
 ------
 let fruits = ['apple', 'banana', 'cherry', 'date'];
 let subArray = fruits.slice(1, 3);
 console.log(subArray); // 输出: ['banana', 'cherry']


 ```
## es5和es6区别  
ES5和ES6都是JavaScript语言的版本，ES5在2009年发布，ES6在2015年发布，两者之间有以下的区别：   
1、变量声明方式不同：ES5使用var关键字进行变量声明，而ES6则引入了let和const关键字来声明变量。  
2、块级作用域：在ES5中，只存在全局作用域和函数作用域，而ES6中增加了块级作用域，对于if、for、switch等代码块内部所声明的变量，在外部是不可见的。  
3、箭头函数：ES6中新增了箭头函数，可以更为简洁地定义函数，同时箭头函数没有自己的this，它的this绑定在父级作用域的this上。  
4、字符串模板：ES6中新增了字符串模板功能，可以使用反引号（`）来定义多行文本和嵌入表达式。  
5、类和继承：ES6中引入了class关键字来实现类和继承，使得面向对象编程更加方便。  
6、模块化：ES6中引入了模块化的概念，通过export和import关键字来实现模块的导出和引入。  
7、解构赋值：ES6中引入了解构赋值语法，可以方便地从数组或对象中提取值并赋给变量。  
8、Promise对象：ES6中引入了Promise对象，可以更加优雅地处理异步操作。  
9、其他：ES6还新增了一些新的数据结构和方法，如Set、Map、Symbol等。同时对于函数参数的默认值、rest参数等也进行了增强和优化。  
总之，ES6相对于ES5来说是一个更加完善和现代化的JavaScript版本，提供了更多方便的语法和功能特性，能够使得开发者更加高效和舒适地进行开发工作。  
 