---
title: 前端练习Day6
date:  2020-07-26 13:39:05 +0800
category: Practise
tags: ["前端练习"]
excerpt: 打卡练习模式第六天
---



1. **找到字符串中最长的单词，并返回它的长度**

   我的答案：

   ```js
   function getLongestWordLen(str) {
     var tempArr = str.match(/\b[a-zA-Z]+\b/g);
     return tempArr.sort(function(a, b) {
       return b.length - a.length;
     })[0].length;
   }
   
   var input = 'GitHub is built for collaboration. Set up an organization to improve the way your team works together, and get access to more features.';
   var output = getLongestWordLen(input);
   
   log(output);
   ```

   

2. **写一个使两个整数进行交换的方法（不能使用临时变量）**

   我的答案：

   ```js
   var a = -20;
   var b = 15;
   
   a = b - a;
   b = b - a;
   a = a + b;
   
   log(a, b)
   ```

   网上看到的其他答案：

   ```js
   [a, b] = [b, a]
   ```

   ```js
   a ^= b;
   b ^= a;
   a ^= b;
   ```

   ```js
   b = a + 0 * (a = b)
   ```

   
   
3. **深度克隆对象的方法有哪些，并把你认为最好的写出来**

   这一题在js知识体系1-1-1中已经提到，这里再做下回顾

   我的答案：没有最好，只有最适合

   方法一：

   ```js
   var input = {
     num: 10,
     str: 'hello',
     bool: false,
     'null': null,
     'undefined': undefined,
     fn: function() {log('hi')},
     array1: [1,2,3,4],
     array2: [[1,2], [3,4], 5,6],
     obj1: {a:1, b: '2'},
     obj2: {c: 0, d: function(){log('emm')}} 
   }
   
   var output = {...input} // 利用ES6扩展运算符
   
   log(output, input===output, classOf(output))
   ```

   该方法优点方便，缺点兼容问题，并且用之前得明确数据类型

   方法二：

   ```js
   var output = JSON.parse(JSON.stringify(input));
   ```

   该方法同样是方便，并且不存在方法一的问题。但缺点是能力有限，不能识别函数，undefined以及symbol。

   方法三：

   ```js
   var output = $.extend(true, {}, input); // 利用jquery
   ```

   该方法不识别undefined，并且使用前需知道是数组还是对象。优点，无兼容问题，写法方便。

   方法四：

   ```js
   var output = Object.assign({}, input)
   ```

   该方法相对不推荐，不支持数组，兼容性问题，最大的问题是不能对属性值是对象的属性深拷贝。

   方法五：

   ```js
   function deepClone(obj) {
     var result;
   
     if (typeof obj !== 'object' || obj == null) {
       return obj;
     }
   
     if (obj instanceof Array) {
       result = [];
     } else {
       result = {};
     }
   
     for (var key in obj) {
       if ({}.hasOwnProperty.call(obj, key)) {
         result[key] = deepClone(obj[key]);
       }
     }
     return result;
   }
   
   var output = deepClone(input)
   ```

   不嫌麻烦那就自己写个深拷贝的方法好了。

   