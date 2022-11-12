# typeof 与 instanceof 区别？

1. ### typeof

   ###### 返回一个字符串，表示未经计算的操作数的类型

   ~~~js
   typeof 1 // 'number'
   typeof '1' // 'string'
   typeof undefined // 'undefined'
   typeof true // 'boolean'
   typeof Symbol() // 'symbol'
   typeof null // 'object'
   typeof [] // 'object'
   typeof {} // 'object'
   typeof console // 'object'
   typeof console.log // 'function'
   ~~~

   如果我们想要判断一个变量是否存在，可以使用`typeof`：(不能使用`if(a)`， 若`a`未声明，则报错)

   ~~~js
   if(typeof a != 'undefined'){
       //变量存在
   }
   ~~~

   

2. ### instanceof

   ###### 用于检测构造函数的 `prototype` 属性是否出现在某个实例对象的原型链上

   构造函数通过`new`可以实例对象，`instanceof`能判断这个对象是否是之前那个构造函数生成的对象

   ~~~js
   // 定义构建函数
   let Car = function() {}
   let benz = new Car()
   benz instanceof Car // true
   let car = new String('xxx')
   car instanceof String // true
   let str = 'xxx'
   str instanceof String // false
   ~~~

3. ### 区别

   + `typeof` 会返回一个<font color="red">变量的基本类型</font>，`instanceof` 返回的是一个<font color="red">布尔值</font>
   + `instanceof` 可以准确地判断复杂引用数据类型，但是不能正确判断基础数据类型
   + 而`typeof` 也存在弊端，它虽然可以判断基础数据类型（`null` 除外），但是引用数据类型中，除了`function` 类型以外，其他的也无法判断

