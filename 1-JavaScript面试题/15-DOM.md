# DOM常见的操作有哪些？

1. ### 什么是 DOM？

   + 文档对象模型
   + DOM 就是把「<font color="red">文档</font>」当对一个「<font color="red">对象</font>」来看待
   + DOM 的顶级对象是 <font color="red">**document**</font>
   + DOM 主要学习的是操作页面元素
   + DOM 是 W3C 标准规范

2. ### 创建节点

   + **createElement**	创建新元素，接受一个参数，即要创建元素的<font color="red">标签名</font>。
   + **createTextNode**	创建一个<font color="red">文本节点</font>。
   + **createDocumentFragment**	用来创建一个<font color="red">文档碎片</font>，它表示一种轻量级的文档，主要是用来<font color="red">存储临时节点</font>，然后把文档碎片的内容一次性添加到`DOM`中。
   + **createAttribute**	创建<font color="red">属性节点</font>，可以是<font color="red">自定义属性</font>。

3. ### 查询节点

   + **querySelector**	传入<font color="red">任何有效的`css` 选择器</font>，即可选中<font color="red">单个 `DOM`元素（首个）</font>。如果页面上没有指定的元素时，返回 `null`。

   + **querySelectorAll**	返回一个包含节点子树内<font color="red">所有</font>与之相匹配的`Element`节点列表，如果没有相匹配的，则返回一个空节点列表。

   + **其他**

     ~~~js
     document.getElementById('id属性值');	//返回拥有指定id的对象的引用
     document.getElementsByClassName('class属性值');	//返回拥有指定class的对象集合
     document.getElementsByTagName('标签名');	//返回拥有指定标签名的对象集合
     document.getElementsByName('name属性值'); 	//返回拥有指定名称的对象结合
     document/element.querySelector('CSS选择器');  //仅返回第一个匹配的元素
     document/element.querySelectorAll('CSS选择器');   //返回所有匹配的元素
     document.documentElement;  //获取页面中的HTML标签
     document.body; 	//获取页面中的BODY标签
     document.all[''];  	//获取页面中的所有元素节点的对象集合型
     ~~~

     

4. ### 更新节点

   + **innerHTML**	不但可以修改一个`DOM`节点的<font color="red">文本内容</font>，还可以直接通过<font color="red">`HTML`片段</font>修改`DOM`节点内部的子树。
   + **innerText、textContent**	自动对<font color="red">字符串</font>进行`HTML`编码，保证无法设置任何`HTML`标签。两者的区别在于读取属性时，`innerText`不返回隐藏元素的文本，而`textContent`返回所有文本。
   + **style**	`DOM`节点的`style`属性对应所有的`CSS`，可以直接获取或设置。<font color="red">遇到`-`需要转化为驼峰命名</font>。

5. ### 添加节点

   + **innerHTML**	如果这个<font color="red">DOM节点是空的</font>，例如，`<div></div>`，那么，直接使用`innerHTML = '<span>child</span>'`就可以<font color="red">修改`DOM`节点的内容</font>，相当于添加了新的`DOM`节点。如果这个<font color="red">DOM节点不是空的</font>，那就不能这么做，因为`innerHTML`会<font color="red">直接替换掉原来的所有子节点</font>。
   + **appendChild**	把一个子节点添加到<font color="red">父节点的最后一个子节点</font>。
   + **insertBefore**	把子节点插入到<font color="red">指定的位置</font>。
   + **setAttribute**	在指定元素中<font color="red">添加一个属性节点</font>，如果元素中已有该属性<font color="red">改变属性值</font>。

6. ### 删除节点

   + **removeChild**	删除一个节点，首先要获得该节点本身以及它的父节点，然后调用该方法。删除后的节点虽然不在文档树中了，但其实它还在内存中，可以随时再次被添加到别的位置。

