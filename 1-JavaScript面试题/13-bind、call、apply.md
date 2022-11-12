# bind、call、apply 区别？如何实现一个bind?

1. ### 作用

   改变函数执行时的上下文，简而言之就是改变函数运行时的`this`指向。

2. ### 区别

   + #### apply

     接收两个参数，第一个参数是`this`的指向，第二个参数是函数接受的参数，以<u>数组的形式</u>传入

     改变`this`指向后原函数会<font color="red">立即执行</font>，且此方法只是<font color="red">临时改变`this`指向一次</font>

     当第一个参数为`null`、`undefined`的时候，默认指向`window`(在浏览器中)

   + #### call

     接收两个参数，第一个参数也是`this`的指向，后面传入的是一个<u>参数列表</u>

     改变`this`指向后原函数会<font color="red">立即执行</font>，且此方法只是<font color="red">临时改变`this`指向一次</font>

     当第一个参数为`null`、`undefined`的时候，默认指向`window`(在浏览器中)

   + #### bind

     接收两个参数，第一参数也是`this`的指向，后面传入的也是一个<u>参数列表(但是这个参数列表可以分多次传入)</u>

     改变`this`指向后<font color="red">不会立即执行</font>，而是返回一个<font color="red">永久改变`this`指向的函数</font>，即<font color="red">返回绑定this之后的函数</font>

     当第一个参数为`null`、`undefined`的时候，默认指向`window`(在浏览器中)

3. ### 如何实现 bind

   ~~~js
   Function.prototype.myBind = function (context) {
       // 判断调用对象是否为函数
       if (typeof this !== "function") {
           throw new TypeError("Error");
       }
   
       // 获取参数
       const args = [...arguments].slice(1),
             fn = this;
   
       return function Fn() {
   
           // 根据调用方式，传入不同绑定值
           return fn.apply(this instanceof Fn ? new fn(...arguments) : context, args.concat(...arguments)); 
       }
   }
   ~~~

   

