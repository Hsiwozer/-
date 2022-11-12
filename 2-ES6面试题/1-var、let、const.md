# 说说var、let、const之间的区别

1. ### var

   + 在ES5中，顶层对象的属性和全局变量是等价的，用`var`声明的变量<font color="red">既是全局变量，也是顶层变量</font>
   + 使用`var`声明的变量<font color="red">存在变量提升</font>的情况
   + 使用`var`，我们能够对<font color="red">一个变量</font>进行<font color="red">多次声明</font>，后面声明的变量会<font color="red">覆盖</font>前面的变量声明
   + 在<font color="red">函数中</font>使用使用`var`声明变量时候，该变量是<font color="red">局部</font>的；而如果在函数内不使用`var`，该变量是全局的

2. ### let

   + 所声明的变量，只在`let`命令所在的<font color="red">代码块内有效</font>
   + <font color="red">不存在变量提升</font>
   + 只要块级作用域内存在`let`命令，这个区域就<font color="red">不再受外部影响</font>
   + `let`<font color="red">不允许</font>在相同作用域中<font color="red">重复声明</font>

3. ### const

   + `const`声明一个<font color="red">只读的常量</font>，一旦声明，常量的值就<font color="red">不能改变</font>。这意味着，`const`一旦声明变量，就<font color="red">必须立即初始化</font>，不能留到以后赋值
   + <font color="red">不存在变量提升</font>