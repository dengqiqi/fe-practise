---
title: 前端练习Day8
date:  2020-07-28 19:06:32 +0800
category: Practise
tags: ["前端练习"]
excerpt: 打卡练习模式第八天
---

1. **请写出一个函数求出N的阶乘（即N!）**

   我的答案:

   ```js
   function factorial(n) {
     if (n <= 1) {
       return 1;
     }
     return arguments.callee(n-1)*n;
   }
   
   var output = factorial(10);
   log(output)
   ```

   

2. **移除数组 arr 中的所有值与 item 相等的元素。不要直接修改数组 arr，结果返回新的数组**

   我的答案：

   ```js
   function remove(arr, item) {
     var temp = [];
     arr.map(function(ele) {
       (ele !== item) && temp.push(ele);
     })
     return temp;
   }
   var input = [1,2,3,4,2];
   var output = remove(input, 2);
   log(output)
   ```

   

3. **找出数组 arr 中重复出现过的元素**

   我的答案：

   ```js
   function duplicates(arr) {
     var temp = [];
     arr.map(function(item, index) {
       (arr.indexOf(item, index + 1) !== -1 && temp.indexOf(item) === -1) && temp.push(item);
     });
     return temp;
   }
   var input = [1, 2, 4, 4, 3, 3, 1, 5, 3];
   var output = duplicates(input);
   log(output)
   ```

   

