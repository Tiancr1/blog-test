# JS对象基本用法
## 声明对象的两种语法
```js
let obj = {'name':'tian','age':18}
let obj = new Object({'name':'tian','age':18})
```
## 如何删除对象的属性
```js
delete obj.name
delete obj['name']   //同上写法一致
'name' in obj //该语句判断name是否还在obj中
obj.xxx === undefined // 不能通过该语句判断xxx是否在obj中，因为可能xxx的值为undefined，此时通过该语句进行判断是返回的也为true
```

## 如何查看对象的属性
```js
Object.keys(obj)//查看obj的keys
Object.values(obj)//查看obj的values
console.dir(obj)//查看自身+共有属性
obj.hasOwnProperty('name')//判断name是不是obj的自身属性

//简便查看属性的方法
obj['name']
obj.name//与第一种一致
obj.[name]//这里的name指的是变量name而非键name
```
## 如何修改或增加对象的属性
```js
let obj = {'job':'teacher'}//直接赋值进行修改obj的属性
obj.name = 'Bob'//直接赋值进行修改obj的属性
obj.['name'] = 'Alen'// 同上
obj.job = 'student'//直接在obj对象中增加job:'student'属性
Object.assign(obj,{age:18,gender:'man'})//批量赋值增加属性
```
## 如何修改或增加共有属性
1. 无法通过自身修改或增加共有属性
```js
let obj = {},obj2 = {}//obj和obj2共有toString属性
obj.toString = 'xxx'//只会在obj本身增加一个自身toSting属性
obj2.toString//仍在原型中
```
2. 执意修改或增加原型上的属性
```js
obj.__proto__.toString = 'xxx' //不推荐使用
Object.prototype.toString = 'xxx'//不建议直接修改原型，会引发很多问题
```
3. 修改隐藏属性
```js
//不推荐使用
let obj = {name:'Bob'}
let obj2 = {name:'Job'}
let common = {kind:'Human'}
obj.__proto__ = common
obj2.__proto__ = common
//推荐使用Object.create
let obj = Object.create(common)
obj.name = 'Bob'
let obj2 = Object.create(common)
obj2.name = 'jack'
```
## 'name' in obj 和 hasOwnProperty('name')的区别
```js
obj.hasOwnProperty('name')//判断name是不是obj的自身属性
'name' in obj //该语句判断name是否还在obj中
```