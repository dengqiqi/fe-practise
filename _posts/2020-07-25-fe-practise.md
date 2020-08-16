---
title: 前端练习Day5
date:  2020-07-25 14:43:45 +0800
category: Practise
tags: ["前端练习"]
excerpt: 打卡练习模式第五天
---



1. **写一个获取数组的最大值、最小值的方法**

   我的答案：

   ```js
   var testArray = [11, 1, 4, 100, 76, -999, Infinity];
   var maxVal = Math.max.apply(Array, testArray);
   var minVal = Math.min.apply(Array, testArray);
   log(maxVal, minVal); // Infinity, -999
   ```

   

2. **写一个方法判断字符串是否为回文字符串**

   给定一个字符串，验证它是否是回文串，只考虑字母和数字字符，可以忽略字母的大小写。
   说明：本题中，我们将空字符串定义为有效的回文串。

   示例 1:

   输入: "A man, a plan, a canal: Panama"
   输出: true

   示例 2:

   输入: "race a car"
   输出: false

   我的答案：

   ```js
   function isPanlindrome(str) {
     if (typeof str !== 'string') {
       return false;
     }
     var temp = str.toLowerCase().split('').filter(function(item) {
         return item.match(/[0-9]|[a-z]/);
     }).join('');
   
     if (reverseString(temp) === temp) {
       return true;
     }
     return false;
   }
   
   function reverseString(str) {
     return str.split('').reverse().join('');
   }
   
   var testStr1 = "A man, a plan, a canal: Panama";
   var testStr2 = "race a car";
   
   var result1 = isPanlindrome(testStr1);
   var result2 = isPanlindrome(testStr2);
   
   log(result1, result2);
   ```

   

3. **写一个方法把0和1互转（0置1，1置0）**

   这一题出的过于笼统，将且认为是需要达到如下效果

   input: 1010001	output:  0101110

   input: '1010001'	output:  '0101110'

   input: 6120	output:  6021

   input: '6120'	output: '6021'

   我的答案：

   ```js
   function transfer01(data) {
     var dataType = typeof data;
   
     if (dataType !== 'string' && dataType !== 'number') {
       return data;
     }
     var result = [].slice.call(data.toString()).map(function(item) {
       return (item === '0' || item === '1') ? item ^ 1 : item
     }).join('');
     (dataType === 'number') && (result = parseInt(result));
     return result;
   }
   
   var input1 = 1010001;
   var input2 = '1010001';
   var input3 = 6120;
   var input4 = '6120.101';
   
   var outpue1 = transfer01(input1);
   var outpue2 = transfer01(input2);
   var outpue3 = transfer01(input3);
   var outpue4 = transfer01(input4);
   
   log(outpue1, outpue2, outpue3, outpue4);
   ```

   