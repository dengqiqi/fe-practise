---
title: 前端练习Day13
date:  2020-08-02 22:08:06 +0800
category: Practise
tags: ["前端练习"]
excerpt: 打卡练习模式第十三天
---

1. **请快速答出此题的答案并解释：var x, y = 1; x + y = ?**

   考查知识点：隐式转换、加法隐式转换规则

   我的答案：

   ```
   NaN
   ```

   两个不同的数据相加时，会发生隐式转换，转换规则如下：

   当两个数都是数值，执行常规的加法计算，然后根据下列规则返回结果：

   * 如果有一个操作数是NaN，则结果是NaN
   * Infinity加Infinity，结果是Infinity
   * -Infinity加-Infinity，结果是-Infinity
   * -Infinity加Infinity，结果是NaN，反之亦然
   * +0加+0得+0
   * -0加-0得-0
   * +0加-0得+0

   如果有一个操作符是字符串，应用一下规则

   * 如果两个数都是字符串，字符串拼接

   当A（一个数值或者一个字符串）和B（一个非数字并且非字符串的数据类型）相加时。

   B如果是基本类型，先做临时类型转换，转成相应的内置对象，然后调用其valueOf()方法，如果不存在valueOf()方法则会调用toString()方法。然后执行相加操作。

   B如果不是基本类型，就省去转换为内置对象这步，其他一样。

   <br />

2. **两种方法写乘法口诀表**

   我的答案:

   ```js
   // 方法一：双重for循环
   const MAX_WIDTH = 7
   let table = ''
   for (let rhs = 1; rhs <= 9; rhs++) {
       for (let lhs = 1; lhs <= 9; lhs++) {
           if (lhs <= rhs) table += `${lhs}*${rhs}=${lhs * rhs}`.padEnd(MAX_WIDTH)
       }
       table += '\n'
   }
   ```

   ```js
   // 方法二：递归
   function MultiplicationTips() {
     var MAX_WIDTH = 7;
     var result = '';
     var start = 1;
   
     for (var i = 1; i <= 9; i++) {
       start = 1;
       result += getRow() + '\n';
     }
     return result;
     function getRow(n) {
       var output = '';
   
       if (start < i) {
         output = `${start}*${i}=${start * i}`.padEnd(MAX_WIDTH);
         start++;
         return output += getRow();
       } else {
         return `${start}*${i}=${start * i}`.padEnd(MAX_WIDTH);
       }
     }
   }
   log(MultiplicationTips())
   ```

   

