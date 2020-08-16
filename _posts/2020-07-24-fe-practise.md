---
title: 前端练习Day4
date:  2020-07-24 19:16:02 +0800
category: Practise
tags: ["前端练习"]
excerpt: 打卡练习模式第四天
---

1. **如何快速让一个数组乱序，写出来**

   考查知识点：洗牌算法

   

   我的答案：

   ```js
   function swap(arr, a, b) {
     var temp;
     temp = arr[a];
     arr[a] = arr[b];
     arr[b] = temp;
   }
   
   function shuffle(arr) {
     if (classOf(arr) !== 'Array' && arr.length <= 0) {
       return arr;
     }
     var times = arr.length;
   
     return loopShuffle(arr);
   
     function loopShuffle(arr) {
       if (times === 1) {
         return arr;
       } else {
         var rand = Math.round(Math.random()*(times - 2));
         swap(arr, rand, times - 1);
         times--;
         return loopShuffle(arr);
       }
     }
   }
   
   var testArr = [];
   
   for (var i = 0; i < 54; i++) {testArr.push(i)}
   
   var result = shuffle(testArr);
   log(result);
   ```

2. **写一个判断设备来源的方法**

   考查知识点：Navigator对象、正则表达式

   

   答案如下：（该方法摘自犀牛书，用于检测浏览器内核和版本号）

   ```js
   var browser = (function() {
     var s = navigator.userAgent.toLowerCase();
     var match = /(webkit)[ \/]([\w.]+)/.exec(s) ||
     /(opera)(?:.*version)?[ \/]([\w.]+)/.exec(s) ||
     /(msie) ([\w.]+)/.exec(s) ||
     !/compatible/.test(s) && /(mozilla)(?:.*? rv:([\w.]+))?/.exec(s) || [];
     return {name: match[1] || '', version: match[2] || '0'};
   })();
   
   log(browser)
   ```

3. **说说bind、call、apply的区别？并手写实现一个bind的方法**

   考查知识点：bind、call和apply的用法；this；**原型和原型链**；**new操作符**（隐藏考查点）

   

   我的答案：

   bind、call和apply都是函数原型上的方法，用来改变this的指向。

   call的用法

   ```js
   // targetFun函数调用, this指向newContext, 函数参数为arg1,arg2,...argN
   targetFun.call(newContext, arg1, arg2, ...argN) 
   ```

   apply的用法

   ```js
   // targetFun函数调用, this指向newContext, 函数参数为arg1,arg2,...argN
   targetFun.call(newContext, [arg1, arg2, ...argN]) 
   ```

   bind的用法

   ```js
   // 返回新的函数， 新函数this指向newContext, 函数参数为arg1,arg2,...argN
   targetFun.bind(newContext, arg1, arg2, ...argN)
   
   // 调用时
   targetFun.bind(newContex, arg1, arg2, ...argN)(argN1, argN2, ...argNM);
   // 效果上相当于
   targetFun.call(newContext, arg1, arg2, ...argN, argN1, argN2, ...argNM); 
   ```

   

   手写bind函数

   ```js
   Function.prototype.bind = null; // 开关注释，然后对比效果以测试
   
   Function.prototype.bind ||
   (Function.prototype.bind = function(newContext) {
     if (typeof this !== 'function') {
       return;
     }
     var that = this;
     var args = [].slice.call(arguments, 1);
     var fnAgent = function() {};
     var newFn = function() {
       var _this = this instanceof that ? this : newContext;
       return that.apply(_this, args.concat([].slice.call(arguments)));
     }
   
     if (this.prototype) {
       fnAgent.prototype = this.prototype;
     }
     newFn.prototype = new fnAgent();
     return newFn;
   })
   
   
   // 测试用例
   var splitLine = '---------------------';
   var testObj = {
     name: 'testObj',
     sayName: function(a, b, c) {
       this.name = 'instance';
       this.a = a;
       log(
         'My Name is ' + this.name,
         'This is ' + this, 
         a, b, c
       );
       return a + b + c;
     }
   }
   testObj.sayName.prototype.print = function() {'打印成功!'}
   var name = 'window';
   
   // 测试1
   var bindDemo = testObj.sayName.bind(this, 1, 2);
   // log('bindDemo(3) 输出结果: ' + bindDemo(3))
   
   log(splitLine)
   
   // 测试2
   var instance = new bindDemo(3)
   log(instance)
   
   ```

   

