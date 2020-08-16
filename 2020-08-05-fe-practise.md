---
title: 前端练习Day16
date:  2020-08-05 20:25:19 +0800
category: Practise
tags: ["前端练习"]
excerpt: 打卡练习模式第十六天
---

1. **手写一个find函数**

   我的答案：

   ```js
   Array.prototype.find = null;
   Array.prototype.find || 
   (Array.prototype.find = function(func, thisValue) {
     log('山寨find')
     
     if (typeof func !== 'function') {
       return new TypeError(func, ' is not a function');
     }
   
     if (this.length === 0) {
       return undefined;
     }
   
     var i;
     var len = this.length;
     var result;
   
     for (i = 0; i < len; i++) {
       result = func.call(thisValue, this[i], i, this);
   
       if (result) {
         return this[i];
       }
     }
     return undefined;
   });
   
   var input = [1,2,3,4,5,6];
   var output = input.find(function(item, index, arr) {
     return item % 2 === 0;
   })
   log(output);
   ```

   <br>

2. **列举强制类型转换和隐式类型转换**

   我的答案：

   **强制类型转换：** parseInt、parseFloat和toString

   **隐式类型转换：** if、逻辑运算、==、+运算符

   <br>

3. **手写深度比较函数**

   我的答案：

   ```js
   function isObject(obj) {
     return typeof obj === 'object' && obj !== null;
   }
   
   function isEqual(obj1, obj2) {
     if (!isObject(obj1) || !isObject(obj2)) {
       return obj1 === obj2;
     }
   
     if (obj1 === obj2) return true;
     
     var obj1Keys = Object.keys(obj1);
     var obj2Keys = Object.keys(obj2); 
   
     if (obj1Keys.length !== obj2Keys.length) {
       return false;
     }
   
     for (let key in obj1) {
       const result = isEqual(obj1[key], obj2[key]);
   
       if (!result) {
         return false;
       }
     }
     return true;
   }
   
   ```

   