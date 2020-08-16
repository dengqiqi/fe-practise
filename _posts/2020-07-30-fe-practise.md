---
title: 前端练习Day10
date:  2020-07-30 19:40:48 +0800
category: Practise
tags: ["前端练习"]
excerpt: 打卡练习模式第十天
---



1. **请描述下ajax的请求都有哪些步骤？**

   我的答案：

   简单概括四个步骤：

   1. 创建 XMLHttpRequest 实例
   2. 发出 HTTP 请求
   3. 接收服务器传回的数据
   4. 更新网页数据

   具体操作：

   新建XMLHttpRequest实例

   ```js
   var xhr = new XMLHttpRequest();
   ```

   指定建立HTTP连接的一些细节

   ```js
   xhr.open('GET', 'url', true);
   ```

   open方法第一个参数表示请求方式，主要的请求方式有'GET'、"POST"、”DELETE“、”UPDATE“等。

   第二个参数是URL，一个URL包含协议、主机、端口（必需），请求内容和查询字符串（非必需）

   第三个参数表示是否异步。第一个和第二个参数是必需的，第三个参数是非必需的。

   然后指定回调函数，监听通信状态的变化（readyState）

   ```js
   xhr.onreadystatechange = handleStateChange;
   
   function handleStateChange() {
       
   }
   ```

   最后使用send()方法，实际发出请求。

   ```js
   xhr.send(null);
   ```

   send方法的参数为请求主体，对于GET请求，它只有请求头，绝对没有请求主体。所以这里指定null。

   服务端接收到请求后，会处理请求并发出响应。

   一个完整的HTTP响应由状态码、响应头集合和响应体组成。

   * xhr对象的status和statusText属性以数字和文本的形式返回HTTP状态码，如200表示请求成功。

   * 通过getResponseHeader()和getAllResponseHeader()能查询响应头。
   * 响应主体可以从responseText属性中得到文本形式的，从responseXML属性中得到Document形式的。

   接收到服务端的响应数据后，AJAX不会刷新整个网页，而是只更新网页中相关的部分。

   <br/>

2. **GET请求和POST请求的差别？**

   我的答案：

   HTTP中GET和POST除了语义上的不同，并无其它区分。

   GET请求用于获取指定的服务端资源；POST请求用于提交数据到服务端。（语义上）

   鉴于语义，GET请求的数据应当是可以缓存的，并且是无副作用并且幂等的。（即不会修改资源文件，多次请求资源状态始终一致）

   但是在WEB中事情就变得有些微妙了。在WEB中：

   **GET和POST数据传输形式不同**

   GET请求只有请求头，必定没有请求体，请求的数据通过与url拼接传递；POST请求通常会有请求体，传递的数据放在请求体中。

   由于浏览器和服务器对于URL长度有限制，所以GET请求的数据远小于POST请求；

   由于数据直观的展现在URL上，所以潜意识认为GET请求相对POST请求不安全；实际上，对于HTTP协议而言，数据报都是明文传输的，即在传输路径中他们都是不安全的，要确保安全需要使用HTTPS协议对数据进行加密。

   由于URL只支持ASCII编码，因此GET也只支持ASCII编码，而POST请求不限于此。

   **GET和POST数据传输过程不同**

   对于有一些浏览器而言，GET请求产生一个数据包，而POST会产生两个TCP数据包，在传输过程中先传递请求头，然后再传输请求体。

   