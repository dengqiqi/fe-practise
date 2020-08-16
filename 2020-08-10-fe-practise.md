---
title: 前端练习Day17
date:  2020-08-10 19:36:20 +0800
category: Practise
tags: ["前端练习"]
excerpt: 打卡练习模式第十七天
---



1. **手写一个防抖方法**

   我的答案：

   场景再现，代码如下：

   ```html
   <input type="text" id="search" />
   ```

   ```js
   var search = document.getElementById('search');
   search.addEventListener('keyup', function () {
     log(search.value);
   });
   ```

   如上，input中持续输入内容时会持续触发keyup事件的处理函数，这种情况就叫作抖动。

   **防抖的思路是当持续触发事件时，一定时间内没有再触发事件，事件处理函数才被执行。**

   防抖的实现如下：

   ```js
   var search = document.getElementById('search');
      
   function debounce(fn, timeGap = 500) {
     var timer;
      
     return function() {
       if (timer) {
         clearTimeout(timer);
       }
       var args = arguments;
       timer = setTimeout(function() {
         fn.apply(this, args);
       }, timeGap)
     }
   }
   search.addEventListener('keyup', debounce(function(e){
     log(search.value, e);
   }));
   ```

   <br />

2. **手写一个节流方法**

   我的答案：

   场景再现，代码如下：

   ```js
   var box = document.getElementById('box');
   box.addEventListener('drag', function(e) {
     log(e.offsetX, e.offsetY);
   });
   ```

   如上，我们在拖拽box的时候会不停的触发拖拽事件。

   **节流的思路是事件持续触发时，一段事件只处理一次事件处理函数。**

   节流的实现如下：

   ```js
   var box = document.getElementById('box');
   
   function throttle(fn, timeGap = 200) {
     var timer;
   
     return function() {
       if (timer) {
         return;
       }
       var args = arguments;
       timer = setTimeout(function() {
         fn.apply(this, args);
         timer = null;
       }, timeGap);
     }
   }
   box.addEventListener('drag', throttle(function(e) {
     log(e.offsetX, e.offsetY);
   }));
   ```

   

