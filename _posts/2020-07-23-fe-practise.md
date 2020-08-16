---
title: 前端练习Day3
date:  2020-07-23 18:56:59 +0800
category: Practise
tags: ["前端练习"]
excerpt: 打卡练习模式第三天
---

1. **写一个判断数据类型的方法**

   我的答案：

   ```js
   function classOf(data) {
     return {}.toString.call(data).slice(8, -1);
   }
   ```

2. **写一个数组去重的方法（支持多维数组）**

   考点：数组降维、一维数组去重

   我的答案：

   ```js
   // 数组降维
   function easyArray(arr) {
     var temp = [];
     loopHandle(arr);
     function loopHandle(arr) { // 这里利用了闭包特性
       arr.map(function(item){
         if (classOf(item) !== 'Array') {
           temp.push(item);
         } else {
           loopHandle(item)
         }
       });
     }
     return temp
   }
   // 数组去重
   function filterArray(arr) {
     if (classOf(arr) !== 'Array') {
       return arr;
     }
     var temp = [];
     easyArray(arr).map(function(item) {
       if (temp.indexOf(item) === -1) {
         temp.push(item);
       }
     })
     return temp;
   }
   var testArray = [2,5, [6, [5,6,7, [1,2,8]]], 1,2,3, [1,1,2,[3,4, [10], 11, [10, 12]]]];
   var result = filterArray(testArray);
   log(result);
   ```

3. **你对new操作符的理解是什么？手动实现一个new方法**

   本题考点：new的底层动作、原型和原型链

   我的答案：

   ```js
   // newNew(constructor)() 模拟 new Constructor();
   function newNew (constructor) {
     return function() {
       var instance = {}; // 先创建一个空对象
       instance.__proto__ = constructor.prototype; // 原型属性指向构造函数的原型
       constructor.apply(instance, arguments); // 调用构造函数并确定this指向
       return instance; // 返回实例对象
     }
   }
   
   Demo.prototype.sayHi = function() {log('hi')}
   function Demo(name) {
     this.name = name;
     this.age = 15;
   }
   
   var demo1 = newNew(Demo)('demo1');
   var demo2 = new Demo('demo2')
   log(demo1, demo2)
   ```

   