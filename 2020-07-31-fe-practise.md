---
title: 前端练习Day11
date:  2020-07-31 23:44:27 +0800
category: Practise
tags: ["前端练习"]
excerpt: 打卡练习模式第十一天
---

1. **写一个显示时间的程序**

   我的答案：

   ```js
   function displayTime() {
     var date = new Date();
     var year = date.getFullYear();
     var month = date.getMonth(); // 0~11 0表示一月 11 表示十二月
     var day =  date.getDate();
     var week = getWeek(date.getDay()); // 0~6 0表示周日 6表示周六
     var h = date.getHours();
     var m = date.getMinutes();
     var s = date.getSeconds();
     var clock = document.getElementById('clock');
     clock.innerHTML = year + '年' + (month+1) + '月' + day + '日 ' + week + '<br />'
      + checkTime(h) + ':' + checkTime(m) + ':' + checkTime(s);
     setTimeout(arguments.callee, 1000);
   }
   
   function checkTime(time) {
     if (time < 10) {
       time = '0' + time;
     }
     return time;
   }
   
   function getWeek(num) {
     var preFix = '星期';
     var weekArray = ['天', '一', '二', '三', '四', '五', '六'];
     return preFix + weekArray[num];
   }
   
   displayTime();
   ```

   <br />

2. **写一个新年倒计时**

   我的答案：

   ```js
   function countDown() {
     var isInit = true;
     var lastMoment = new Date();
     var excuteMoment = new Date();
     lastMoment.setHours(23, 59, 59);
   
     showDay();
     
     function showDay() {
       var timeGap = isInit ? lastMoment.getTime() - excuteMoment.getTime() + 1000 : 86400000;
       isInit = false;
       var targetDate = new Date();
       var curDate = new Date();
       targetDate.setFullYear(curDate.getFullYear() + 1, 0, 1);
       setTimeout(arguments.callee, timeGap);
       log(Math.ceil((targetDate.getTime() - curDate.getTime()) / 1000 / 60 / 60 / 24));
     }
   }
   countDown();
   ```

   

