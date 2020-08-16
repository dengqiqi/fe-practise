---
title: 前端练习Day18
date:  2020-08-11 18:57:29 +0800
category: Practise
tags: ["前端练习"]
excerpt: 打卡练习模式第十八天
---



1. **数组slice和splice的区别**

   我的答案：

   **功能区别：**

   slice为切片，splice为剪接。

   **参数区别：**

   slice接收两个可选的参数，分别为开始索引和结束索引。start默认为1，end默认为数组长度

   返回start开始到end结束但不包含end的元素所组成的数组。

   splice第一个参数是必需参数，表示开始索引，后面的参数都是可选参数，第二个参数表示需要剪切的个数，默认为0，为负数时也是按0处理，小数时向下取整。后面的参数均会拼接到索引位置。

   该方法返回被删除的元素组成的数组。

   **是否纯函数：**

   slice是纯函数，它不会改变原数组；splice非纯函数，它会改变原数组。

   <br />

2. **[10, 20, 30].map(parseInt)的返回结果是什么？**

   我的答案：

   ```js
   [10, NaN, NaN]
   ```

   上面的代码相当于如下

   ```js
   [10, 20, 30].map((item, index)=>{
     parseInt(item, index);
   });
   ```

   parseInt接收两个参数，第一个参数表示一个数字或字符串，第二个参数是解析的基数，即转成几进制的数。

   范围为2到36，默认为0表示10进制，其他范围外的数都返回NaN。并且数字可能会被截断解析，看下面例子

   ```js
   [9, 10, 11, 2131].map((item, index)=>{
     return parseInt(item, index);
   });
   ```

   ```
   [9, NaN, 3, 7]
   ```

   <br />

3. **document load和ready的区别**

   我的答案：

   DOM文档解析过程如下：

   1. 解析html结构
   2. 加载脚本和样式文件
   3. 解析并执行脚本
   4. 构造html的DOM模型    //ready
   5. 加载图片等外部资源文件
   6. 页面加载完毕        //load

   ```js
   window.addEventListener('load', function() {
     // 页面的全部资源加载完才会执行，包含图片、视频等
   });
   
   document.addEventListener('DOMContentLoaded', function() {
     // DOM 渲染完即可执行，此时图片、视频还可能没有加载完
   });
   ```

   

