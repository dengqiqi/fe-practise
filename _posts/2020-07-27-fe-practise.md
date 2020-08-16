---
title: 前端练习Day7
date:  2020-07-27 20:56:33 +0800
category: Practise
tags: ["前端练习"]
excerpt: 打卡练习模式第七天
---



1. **请你解释一个为什么10.toFixed(10)会报错？**

   我的答案：

   toFixed()是Number对象的一个方法，但我们知道一个基本的数字是一个基本类型，它不具备方法。

   然而

   ```js
   var number = 10;
   number.toFixed(10); // "10.0000000000"
   typeof number; // "number"
   ```

   上面的代码执行时，js引擎会将number转换成一个Number对象，这个转换是临时的。之后仍然不会改变它是基本类型的本质。

   但当我们直接这样写时

   ```js
   10.toFixed(10) // Uncaught SyntaxError: Invalid or unexpected token
   ```

   它会抛出一个语法错误，原因是因为编译器识别到小数点后认为这是一个小数，即小数点引发了歧义。

   以下场合不会引起歧义

   ```js
   10.0.toFixed(10)
   ```

   

   我们可以通过最上面的写法避免歧义。也可以通过()来避免歧义

   ```js
   (10).toFixed(10)
   ```

   

2. **说说你对IIFE的理解**

   我的答案：

    **IIFE** (Immediately Invoked Function Expression) 即立即执行函数表达式，写法如下：

   ```js
   (function() {
   	// do something...
   })();
   ```

   它的本质是让do something的代码处于一个独立的函数上下文中执行。

   这样做有哪些作用，

   一、可以用来模拟块级作用域

   ```js
   for (var i =0; i < 10; i++) {
     (function(i) {
       setTimeout(function() {
         log(i);
       }, 100)
     })(i)
   }
   ```

   二、可以实现模块

   ```js
   var module1 = (function() {
     var total = 10;
     var getNum = function() {
       log(total);
       return total;
     };
     var resetNum = function() {
       total = 0;
     };
     return {
       getNum: getNum,
       resetNum: resetNum
     };
   })();
   
   var module2 = (function() {
     var total = 40;
     var getNum = function() {
       log(total);
       return total;
     };
     var addNum = function() {
       total++;
     }
     return {
       getNum: getNum,
       addNum: addNum,
     }
   })();
   
   module1.resetNum();
   module1.getNum();
   
   module2.addNum();
   module2.getNum();
   ```

   模块中变量不会污染全局环境，上述两个模块中的total和getNum不会相互影响。并且对外隐藏掉了total这个变量，我们只能通过提供的接口getNum来获取到它。

   

3. **window对象和document对象有什么区别？**

   我的答案：

   window对象是BOM中的核心对象，它是一个窗口或者是一个框架的抽象。它是js运行时的全局对象。而document表示的是文档对象，它是window对象上的一个属性。

   ```js
   window.document === document // true
   ```

   document是DOM中的核心对象，是对结构化文本如（HTML和XML）的抽象。

