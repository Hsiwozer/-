# ajax原理是什么？如何实现？

1. ### 是什么？

   AJAX 即异步的 `JavaScript` 和 `XML`，是一种创建交互式网页应用的网页开发技术，可以在<font color="red">不重新加载整个网页</font>的情况下，<font color="red">与服务器交换数据</font>，并且<font color="red">更新部分网页</font>。

   `Ajax` 的原理简单来说通过 `XmlHttpRequest` 对象来向服务器发<font color="red">异步请求</font>，从服务器获得数据，然后用 `JavaScript` 来操作 `DOM` 而更新页面。

2. ### 实现过程

   + **创建 XMLHttpRequest 对象**：创建 `Ajax`的核心对象 `XMLHttpRequest`对象

     ~~~js
     const xhr = new XMLHttpRequest();
     ~~~

     

   + **与服务器建立连接**：通过 `XMLHttpRequest` 对象的 `open()` 方法与服务端建立连接

     ~~~js
     xhr.open(method, url, [async][, user][, password])
     ~~~

     

   + **给服务端发送数据**：构建请求所需的数据内容，并通过`XMLHttpRequest` 对象的 `send()` 方法发送给服务器端

     ~~~js
     xhr.send([body])
     ~~~

     

   + **绑定 onreadystatechange 事件**：通过 `XMLHttpRequest` 对象提供的 `onreadystatechange` 事件监听服务器端的通信状态

     关于`XMLHttpRequest.readyState`属性有五个状态，如下图显示:

     |             值             |                   状态                    |                      描述                      |
     | :------------------------: | :---------------------------------------: | :--------------------------------------------: |
     |             0              |             UNSENT（未打开）              |              open()方法还未被调用              |
     |             1              |             OPENED（未发送）              |              send()方法还未被调用              |
     |             2              |     HEADERS_RECEIVED（已获取响应头）      | send()方法已经被调用，相应头和响应状态已经返回 |
     |             3              |         LOADING（正在下载响应体）         |  响应体下载中；responseText中已经获取部分数据  |
     | <font color="red">4</font> | <font color="red">DONE（请求完成）</font> |  <font color="red">整个请求过程已完毕</font>   |

     

     ~~~js
     const request = new XMLHttpRequest()
     request.onreadystatechange = function(e){
         if(request.readyState === 4){ // 整个请求过程完毕
             if(request.status >= 200 && request.status <= 300){
                 console.log(request.responseText) // 服务端返回的结果
             }else if(request.status >=400){
                 console.log("错误信息：" + request.status)
             }
         }
     }
     request.open('POST','http://xxxx')
     request.send()
     ~~~

     

   + 接受并处理服务端向客户端响应的数据结果

   + 将处理结果更新到 `HTML`页面中