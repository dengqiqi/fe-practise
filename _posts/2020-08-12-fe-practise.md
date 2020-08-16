---
title: 前端练习Day19
date:  2020-08-12 21:19:31 +0800
category: Practise
tags: ["前端练习"]
excerpt: 打卡练习模式第十九天
---



1. **var、let和const的区别**

   我的答案：

   * var声明的变量存在变量提升，let不存在变量提升

   * let声明的变量具有块级作用域，var声明的变量不具有

   * var声明的变量在非严格模式下，能作为window的属性访问到，let声明的变量则不行；

   * var 声明的变量可以重复定义，let声明的变量不可重复定义

   const具有所有上述所有let的特点。除此之外

   * const可以定义常量，const定义的基本类型数据不可被修改，引用类型数据可以被修改

   * const必须声明时赋值

   <br>

2. **解析Url参数为js对象**

   我的答案：

   ```js
   function parseUrl() {
     const result = {}
     const searchStr = location.search.substr(1);
     searchStr.split('&').forEach(item => {
       const arr = item.split('=')
       const key = arr[0]
       const val = arr[1]
       result[key] = val
     })
     return result
   }
   ```

   <br>

3. **实现一个数组，奇数在右边，偶数在左边，不能使用额外空间**

   我的答案：

   ```js
   const arr = [1,2,3,4,5,6,7,8,9,10];
   arr.sort((a, b) => -b % 2)
   log(arr)
   ```

   





