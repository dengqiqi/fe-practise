---
title: 前端练习Day2
date:  2020-07-22 19:10:23 +0800
category: Practise
tags: ["前端练习"]
excerpt: 打卡练习模式第二天
---



1. **写一个方法把下划线命名转成小驼峰命名**

   我的答案：

   ```js
   function convertName(str) {
     var result = str.toLowerCase();
   
     if (result.indexOf('_') !== -1) {
       result = result.split('_').filter(function(item) {
         return item !== '';
       }).map(function(item, index) {
         if (index > 0) {
           return item.charAt(0).toUpperCase() + item.slice(1);
         }
         return item;
       }).join('');
     }
     return result;
   }
   
   var testStr = '__HELLO_world_i_like_you__';
   var result = convertName(testStr);
   log(result);
   ```

2. **写一个把字符串大小写切换的方法**

   我的答案：

   ```js
   function convertCase(str) {
     var result = str;
     var temp = result.toLowerCase();
   
     return result.split('').map(function(item, index) {
       if (item !== temp.charAt(index)) {
         return item.toLowerCase();
       } else {
         return item.toUpperCase();
       }
     }).join('')
   }
   
   var testStr1 = '';
   var testStr2 = ' A a _ 1 k';
   var testStr3 = 'AaBbCcDdEe';
   
   var result1 = convertCase(testStr1);
   var result2 = convertCase(testStr2);
   var result3 = convertCase(testStr3);
   log(result1, result2, result3)
   ```

3. **统计某一字符或字符串在另一个字符串中出现的次数**

   我的答案：

   ```js
   function getStrNum(targetStr, searchStr) {
     var result;
   
     if (targetStr && searchStr) {
       result = targetStr.split('').filter(function(item) {
         return item === searchStr;
       }).length;
     }
     return result || 0;
   }
   
   var targetStr = ' \\\ \\n\\t\t \\\ta\\n \\\n';
   var searchStr = '\t'
   var result = getStrNum(targetStr, searchStr);
   log(result);
   ```



