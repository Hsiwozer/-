# 你是怎么理解ES6中 Promise的？使用场景？

1. ### 什么是 Promise？

   ###### Promise 是异步编程的一种解决方案，比传统的使用回调函数方案来的更加强大并合理。

   Promise 有三种状态：

   + <font color="red">**pending**</font>（进行中）
   + <font color="red">**fulfilled**</font>（已成功）
   + <font color="red">**rejected**</font>（已失败）

2. ### 用法

   Promise 构造函数接收一个<font color="red">函数</font>作为参数。同时，该函数接收两个参数，分别是：<font color="red">resolve</font> 和 <font color="red">reject</font>。

   - `resolve`函数的作用是，将`Promise`对象的状态从“未完成”变为“成功”
   - `reject`函数的作用是，将`Promise`对象的状态从“未完成”变为“失败”

3. ### 实例方法

   Promise 实例有三个方法：

   + ##### then()

     `then`是实例状态发生改变时的回调函数，第一个参数是`resolved`状态的回调函数，第二个参数是`rejected`状态的回调函数。

     ##### `then`方法返回的是一个新的`Promise`实例，也就是`promise`能链式书写的原因。（所以Promise 能够有效解决回调地狱的问题。）

   + ##### catch()

     用于指定发生错误时的回调函数，是`.then(null, rejection)`或`.then(undefined, rejection)`的别名。

   + ##### finally()

     `finally()`方法用于指定不管 Promise 对象最后状态如何，都会执行的操作。

   ~~~js
   promise
   .then(result => {···})
   .catch(error => {···})
   .finally(() => {···});
   ~~~

   

4. ### 使用场景

   + 将图片的加载写成一个`Promise`，一旦加载完成，`Promise`的状态就发生变化
   + 通过链式操作，将多个渲染数据分别给个`then`，让其各司其职。或当下个异步请求依赖上个请求结果的时候，我们也能够通过链式操作友好解决问题
   + 通过`all()`实现多个请求合并在一起，汇总所有请求结果，只需设置一个`loading`即可
   + 通过`race`可以设置图片请求超时