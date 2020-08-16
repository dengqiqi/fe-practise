---
title: 前端练习Day1
date:  2020-07-21 19:47:16 +0800
category: Practise
tags: ["前端练习"]
excerpt: 打卡练习模式第一天
---



1. **这是一道大题目，把考点拆成4个小项；需要候选人用递归算法实现（限制15行代码以内实现；限制时间10分钟以内完成）**<br />
   **a)  创建一个长度为5的空数组arr**<br />
   **b)  生成一个（2~32）之间的随机整数rand**<br />
   **c)  把随机数rand放入到数组arr内，如果数组arr内已存在与rand相同的数字，则重新生成随机数rand并插入到arr内【需要用递归实现，不能使用for/while等循环】**<br />
   **d)  最终输出一个长度为5，且内容不重复的数组arr**

   我的答案：

   ```js
   function getRanderArray(len, min, max) {
     var arr = new Array(len);
     arr = insertRanderNum(min, max, arr);
     return arr;
   }
   
   function insertRanderNum(min, max, arr) {
     var rand = genRanderIntNum(min, max);
   
     if (arr[0] !== undefined) {
       return arr;
     } else {
       if (arr.indexOf(rand) === -1) {
         arr.push(rand);
         arr.shift();
       }
       return insertRanderNum(min, max, arr)
     }
   }
   
   function genRanderIntNum(min, max) {
     var rand = Math.random();
   
     if (max < min) {
       return new RangeError('RangeError: max is less than min');
     } else {
       rand = Math.round(min + (max - min)*Math.random());
     }
     return rand;
   }
   
   var result = getRanderArray(5, 2, 32);
   log(result)
   ```

2. **写一个方法去掉字符串中的空格，要求传入不同的类型分别能去掉前、后、前后、中间的空格**

   我的答案：

   ```js
   function removeSpaces(str, type) {
     var result = str;
     var len = str.length;
   
     switch (type) {
     case 'head':
       if (str.charAt(0) === ' ') {
         result = result.slice(1)
         result = removeSpaces(result, 'head');
       }
       break;
     case 'tail':
       if (str.charAt(len - 1) === ' ') {
         result = result.substr(0, len - 1)
         result = removeSpaces(result, 'tail');
       }
       break;
     case 'body':
       if (len > 2) {
         result = result.split(' ').map(function(item) {
           (item === '')  && (item = ' ');
           return item;
         }).join('');
       }
       break;
     case 'all':
       // result = result.replace(/ /g, ''); // 方法一
       result = result.split(' ').join(''); // 方法二
       break;
     default: // 默认去除头和尾
       // result = result.trim(); // 方法一：ES6
       result = removeSpaces(removeSpaces(result, 'head'), 'tail'); // 方法二
       break;
     }
     return result;
   }
   
   var testStr = '  hello world! I like you  ';
   var result = removeSpaces(testStr, 'body')
   log(result);
   ```

3. **去除字符串中最后一个指定的字符**

   我的答案：

   ```js
   function removeLastStr(str, targetStr) {
     if (!str || !targetStr) {
       return str;
     }
     var index = str.lastIndexOf(targetStr);
     var len = targetStr.length;
     return index !== -1 ?  str.slice(0, index) + str.slice(index + len) : str;
   }
   
   var testStr = 'dig big egg';
var result = removeLastStr(testStr, 'ig');
   log(result, result.length);
   ```
   
   

