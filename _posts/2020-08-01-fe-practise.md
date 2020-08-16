---
title: 前端练习Day12
date:  2020-08-01 23:20:03 +0800
category: Practise
tags: ["前端练习", “专项练习”]
excerpt: 打卡练习模式第十二天 （正则表达式）
---

前言

本篇练习为正则表达式专项练习篇，不定期更新



1. **正则表达式常规练习**

   ```js
   // 匹配数字
   /\d+/
   /[0-9]+/
   
   // 至少N位的数字
   /\d{N,}/
   
   // 非0开头的最多带两位小数的数字
   /^([1-9][0-9]*)+(.[0-9]{1,2})?$/
       
   // 带1到2位小数的正数或者负数
   /^(\-)?\d+(\.\d{1,2})?$/
       
   // 汉字
   /^[\u4e00-\u9fa5]{0,}$/
       
   // 英文和数字
   /^[A-Za-z0-9]+$/
   
   
   ```

   <br>

2. **正则表达式初级应用**

   * 手机号

     规则： 以1开头第二位为3、5、7、8且长度为11位的数字组合

     ```js
     /^1[3578]\d{9}$/
     ```

   * 字符串提取

     提取字符串中的数字

     ```js
     /-?\d+(\.\d+)?/g
     ```

   * 使用正则去掉html中标签与标签之间的空格

     ```js
     var input = `<!DOCTYPE html>
     <html lang="en">
     <head>
       <meta charset="UTF-8">
       <meta name="viewport" content="width=device-width, initial-scale=1.0">
       <title>Document</title>
     </head>
     <body>
       <!-- Hello -->
     </body>
     </html>`;
     
     var patt = />\s+</g;
     
     var output = input.replace(patt, '><');
     log(output)
     ```

     

   <br>

3. **正则表达式进阶应用**

   * 

     

