---
title: 前端练习Day9
date:  2020-07-29 20:54:40 +0800
category: Practise
tags: ["前端练习"]
excerpt: 打卡练习模式第九天
---

1. **实现一个打点计时器，要求**<br>
   **1、从 start 到 end（包含 start 和 end），每隔 100 毫秒 console.log 一个数字，每次数字增幅为 1**<br>
   **2、返回的对象中需要包含一个 cancel 方法，用于停止定时操作**<br>
   **3、第一个数需要立即输出<br>**

   我的答案：

   ```js
   function count(start, end) {
     var num = start;
     var timer = setInterval(() => {
       if (num >= end) {
         clearInterval(timer);
       } else {
         console.log(++num);
       }
     }, 100);
     console.log(num);
     
     return {
       cancel: function() {
         clearInterval(timer);
       }
     }
   }
   ```

   

2. **实现 fizzBuzz 函数，参数 num 与返回值的关系如下：**<br>
   **1、如果 num 能同时被 3 和 5 整除，返回字符串 fizzbuzz**<br>
   **2、如果 num 能被 3 整除，返回字符串 fizz**<br>
   **3、如果 num 能被 5 整除，返回字符串 buzz**<br>
   **4、如果参数为空或者不是 Number 类型，返回 false**<br>
   **5、其余情况，返回参数 num**<br>

   我的答案：

   ```js
   function fizzBuzz(num) {
     if (typeof num !== 'number') {
       return false;
     }
   
     if (num % 15 === 0) {
       return 'fizzbuzz';
     } else if (num % 5 === 0) {
       return 'buzz';
     } else if (num % 3 === 0) {
       return 'fizz'
     }
     return num;
   }
   ```

   

3. **实现函数 makeClosures，调用之后满足如下条件：**<br>
   **1、返回一个函数数组 result，长度与 arr 相同**<br>
   **2、运行 result 中第 i 个函数，即 result[i]()，结果与 fn(arr[i]) 相同**<br>

   我的答案：

   ```js
   function makeClosures(arr, fn) {
     var result = [];
   
     result = arr.map(function(item) {
       return function() {
         return fn.call(this, item);
       }
     });
     return result;
   }
   
   var arr = [1,2,3];
   var fn = function (x) {
     return x * x;
   }
   var output1 = makeClosures(arr, fn)[1]();
   var output2 = fn(arr[1]);
   log(output1, output2);
   ```

   