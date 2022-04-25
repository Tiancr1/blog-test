# jQuery如何获取元素
```js
//id选择器、css选择器
$(document) //选择整个文档对象
$('#id') //选择ID为id的网页元素
$('div.myClass') // 选择class为myClass的div元素
$('input[name=first]') // 选择name属性等于first的input元素
//特有选择
$('a:first') //选择网页中第一个a元素
$('tr:odd') //选择表格的奇数行
$('#myForm :input') // 选择表单中的input元素
$('div:visible') //选择可见的div元素
$('div:gt(2)') // 选择所有的div元素，除了前三个
$('div:animated') // 选择当前处于动画状态的div元素

```
# jQuery的链式操作
```js
//最终选中网页元素以后，可对它进行一系列操作，并且所有操作可以连接在一起，以链条的形式写出来
$('div').find('h3').eq(2).html('Hello');
//分解
$('div') //找到div元素
 .find('h3') //选择其中的h3元素
 .eq(2) //选择第3个h3元素
 .html('Hello'); //将它的内容改为Hello

```

# jQuery如何创建元素
```js
//1、使用$函数创建新元素
var $newElement=$('<div><p>段落</p></div>');//创建元素,返回jQuery对象
//2、克隆已有的元素（通过克隆已有元素生成新元素）
//使用.clone()。
$('<p>Hello</p>');
$('<li class="new">new list item</li>');
$('ul').append('<li>list item</li>');
//扩展一下
/*
删除元素使用.remove()和.detach()。两者的区别在于，前者不保留被删除元素的事件，后者保留，有利于重新插入文档时使用。
清空元素内容（但是不删除该元素）使用.empty()。*/

```

# jQuery如何移动元素
```js
//第一种方法是使用.insertAfter()，把div元素移动p元素后面
$('div').insertAfter($('p'));
//第二种方法是使用.after()，把p元素加到div元素前面
$('p').after($('div'));
//这两种方法的效果是一样的，唯一的不同似乎只是操作视角的不同。但是实际上，它们有一个重大差别，那就是返回的元素不一样。第一种方法返回div元素，第二种方法返回p元素
//使用这种模式的操作方法，一共有四对
.insertAfter()和.after() //在现存元素的外部，从后面插入元素
.insertBefore()和.before() //在现存元素的外部，从前面插入元素
.appendTo()和.append() //在现存元素的内部，从后面插入元素
.prependTo()和.prepend() //在现存元素的内部，从前面插入元素
```

# jQuery如何修改元素属性
```js
//修改属性的值
$('h1').attr('title',"标题"); //对h1设置标题
.html() //取出或设置html内容
.text() //取出或设置text内容
.attr() //取出或设置某个属性的值
.width() //取出或设置某个元素的宽度
.height() //取出或设置某个元素的高度
.val() //取出某个表单元素的值
```
# jQuery的一些工具方法
```js
$.trim() //去除字符串两端的空格。
$.each() //遍历一个数组或对象。
$.inArray() //返回一个值在数组中的索引位置。如果该值不在数组中，则返回-1。
$.grep() //返回数组中符合某种标准的元素。
$.extend() //将多个对象，合并到第一个对象。
$.makeArray() //将对象转化为数组。
$.type() //判断对象的类别（函数对象、日期对象、数组对象、正则对象等等）。
$.isArray() //判断某个参数是否为数组。
$.isEmptyObject() //判断某个对象是否为空（不含有任何属性）。
$.isFunction() //判断某个参数是否为函数。
$.isPlainObject() //判断某个参数是否为用"{}"或"new Object"建立的对象。
$.support() //判断浏览器是否支持某个特性。
```
# jQuery的事件操作
```js
.blur() 表单元素失去焦点。
.change() 表单元素的值发生变化
.click() 鼠标单击
.dblclick() 鼠标双击
.focus() 表单元素获得焦点
.focusin() 子元素获得焦点
.focusout() 子元素失去焦点
.hover() 同时为mouseenter和mouseleave事件指定处理函数
.keydown() 按下键盘（长时间按键，只返回一个事件）
.keypress() 按下键盘（长时间按键，将返回多个事件）
.keyup() 松开键盘
.load() 元素加载完毕
.mousedown() 按下鼠标
.mouseenter() 鼠标进入（进入子元素不触发）
.mouseleave() 鼠标离开（离开子元素不触发）
.mousemove() 鼠标在元素内部移动
.mouseout() 鼠标离开（离开子元素也触发）
.mouseover() 鼠标进入（进入子元素也触发）
.mouseup() 松开鼠标
.ready() DOM加载完成
.resize() 浏览器窗口的大小发生改变
.scroll() 滚动条的位置发生变化
.select() 用户选中文本框中的内容
.submit() 用户递交表单
.toggle() 根据鼠标点击的次数，依次运行多个函数
.unload() 用户离开页面
```