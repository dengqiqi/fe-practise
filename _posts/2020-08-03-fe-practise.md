---
title: 前端练习Day14
date:  2020-08-03 19:36:20 +0800
category: Practise
tags: ["前端练习"]
excerpt: 打卡练习模式第十四天
---



1. **分析`('b' + 'a' + +'a' + 'a').toLowerCase()`返回的结果**

   考查知识点：运算符优先级、隐式转换规则

   我的答案：

   ```js
   banana
   ```

   一元加法优先级高于加法，所以先计算+'a'，根据隐式转换得到NaN

   然后字符串拼接，得到baNaNa，最后转成小写，得到了香蕉。

   运算符优先级顺序可查看[汇总表](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Operators/Operator_Precedence)
   <br>

2. **写一个字符串重复的repeat函数**

   我的答案：

   ```js
   function repeat(str, num) {
     if (typeof str !== 'string') {
       return new TypeError('Arg[0] is not a string!');
     }
     if (num === 1) {
       return str;
     } else {
       return str + repeat(str, --num);
     }
   }
   var input = 'hi';
   var output = repeat(input, 10);
   log(output);
   ```

   <br>

3. **请实现一个flattenDeep函数，把多维数组扁平化**

   我的答案：

   在Day3时我写了这样的一个方法

   ```js
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
   ```

   用ES6快速实现如下：

   ```js
   testArray.flat(Infinity)
   ```

   

