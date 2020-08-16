---
title: 前端练习Day20
date:  2020-08-13 20:00:01 +0800
category: Practise
tags: ["前端练习"]
excerpt: 打卡练习模式第二十天
---

1. **对函数输入的参数求和**

   我的答案：

   方法一：

   ```js
   function sum() {
     let num = 0
     Array.prototype.forEach.call(arguments, item => {
       num += item * 1
     })
     return num
   }
   ```

   方法二：

   ```js
   function sum() {
     let num = 0
     Array.from(arguments).forEach(item => {
       num += item * 1
     })
     return num
   }
   ```

   方法三：

   ```js
   function sum(...nums) {
     let num = 0
     nums.forEach(item => {
       num += item * 1
     })
     return num
   }
   ```

   <br>

2. **输出字符串中所有最长无重复子串**

   我的答案：

   ```js
   let getLongestSubStr = str => {
     const len = str.length
     let maxLen = 0
     let map = new Map()
     let tempArr = []
   
     Array.prototype.forEach.call(str, (_, index) => {
       for (let i = index; i < len; i++) {
         let byte = str.charAt(i)
         if (tempArr.indexOf(byte) === -1) {
           tempArr.push(byte)
         } else {
           break;
         }
       }
       map.set(tempArr.join(''), tempArr.length)
       tempArr = []
     })
     maxLen = Math.max(...map.values())
   
     for (const [key, value] of map) {
       value === maxLen && tempArr.push(key)
     }
     return tempArr
   }
   ```

   

   

