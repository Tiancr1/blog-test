# 一、介绍一下闭包
## 1. 什么是闭包？
如果一个函数用到了外部的变量，那么这个函数加这个变量就叫闭包.下方中的a和f3组成了闭包。
```js
    function f2(){
        let a = 2
        function f3(){
            console.log(a)
        }
        return f3
    }
```

## 2. 闭包的用途？
1. 不会造成全局变量的污染
2. 可以在函数的外部访问到函数内部的局部变量（实现所谓的变量‘公有化’）
3. 让这些变量始终保存在内存中，不会随着函数的结束而自动销毁

## 3. 闭包的缺点？
闭包使用不当会导致作用域链不释放，造成内存溢出，占用内存空间

# 二、call、apply、bind的用法分别是什么
## 1. call()
call()方法使用一个指定的this值和单独给出的一个或多个参数来调用一个函数。
```js
function add(c, d) {
  return this.a + this.b + c + d;
}

var o = {a: 1, b: 3};
add.call(o,2,3);   //结果为9
```
## 2. apply()
apply()方法使用一个指定的this值和一个以数组的形式提供的参数
```js
function add(c, d) {
  return this.a + this.b + c + d;
}

var o = {a: 1, b: 3};
add.call(o,[2,3]);   //结果为9
```
## 3. bind()
bind() 方法创建一个新的函数，在 bind() 被调用时，这个新函数的 this 被指定为 bind() 的第一个参数，而其余参数将作为新函数的参数，供调用时使用。
```js
this.x = 9;
var module = {
  x: 81,
  getX: function() { return this.x; }
};

module.getX(); // 81

var retrieveX = module.getX;
retrieveX(); //9
var boundGetX = retrieveX.bind(module);
boundGetX(); // 81
```

# 三、HTTP状态码及其意义
1. 200 OK（请求成功）
2. 201 Created（请求成功）
3. 204 NoContent（请求成功，对于该请求没有的内容可发送，但是头部字段可能有用）
4. 301 Moved Permanently（请求资源的URL已经永久更改，在响应中给出了新的URL）
5. 303 See Other（服务器发送此响应，以指客户端通过一个GET请求在另一个URI中获取所请求的资源）
6. 400 Unauthorized（客户端错误，错误的请求语法、无效的请求消息或欺骗性的请求路由，服务器无法处理该请求）
7. 403 Forbidden（客户端没有访问内容的权限；也就是说他是未经授权的，因此服务器拒绝提供请求的资源）
8. 404 NotFound（服务器找不到请求的资源，在浏览器中，这意味着无法识别URL。）
9. 500 Internal Server Error（服务器遇到了不知道如何处理的情况）
10. 503 Service Unavailable（服务器没有准备好处理请求。常见原因是服务器因维护或重载而停机）

# 四、如何实现数组去重？
假设有数组 array = [1,5,2,3,4,2,3,1,3,4]
你要写一个函数 unique，使得
unique(array) 的值为 [1,5,2,3,4]
也就是把重复的值都去掉，只保留不重复的值。
## 方法一：使用Set方法实现
```js
let array = [1,5,2,3,4,2,3,1,3,4]
function unique(array){
    return Array.from(new Set(array))
}
console.log(unique(array))
//缺点：Set去重不适用于含对象的数组，因为Set的去重参照的是（===），数组中的元素对象，虽然可能数值相等，但是地址不相等。
```
## 方法二：使用循环遍历的方法实现
```js
let arr = [1,5,2,3,4,2,3,1,3,4]
function unique(array){
    let res = []
    for(let i=0;i<array.length;i++){
        for(var j=0;j<res.length;j++){
            if(array[i]===res[j]){
                break;
            }
        }
        if(j===res.length){
            res.push(array[i])
        }
    }
    return res;
}
console.log(unique(arr))
//该方案使用循环嵌套，兼容性好。缺点：代码的复杂度太高

```

# 五、DOM事件相关
## 1. 什么是事件委托
在JavaScript中，添加到页面上的事件处理程序数量将直接关系到页面的整体运行性能。导致这一问题的原因是多方面的。首先，每个函数都是对象，都会占用内存；内存中的对象越多，性能就越差。其次，必须事先指定所有事件处理程序而导致的DOM访问次数，会延迟整个页面的交互就绪时间。
捕获和冒泡允许我们实现一种被称为 事件委托 的强大的事件处理模式。对事件处理程序过多问题的解决方案就是事件委托。事件委托利用了事件冒泡，只指定一个事件处理程序，就可以管理某一类型的所有事件。这个想法是，如果我们有许多以类似方式处理的元素，那么就不必为每个元素分配一个处理程序 —— 而是将单个处理程序放在它们的共同祖先上。例如，click事件会一直冒泡到document层次。也就是说，我们可以为整个页面指定一个onclick事件处理程序，而不必给每个可单击的元素分别添加事件处理程序 — —简而言之，把本该这个元素做的事情，全部委托给共同祖先，让祖上处理。
优点：提高页面性能，可以监听动态元素。
在处理程序中，我们获取 event.target 以查看事件实际发生的位置并进行处理。
## 2. 如何阻止默认动作
有一些html元素默认的行为，比如说a标签，点击后有跳转动作；form表单中的submit类型的input有一个默认提交跳转事件；reset类型的input有重置表单行为。
如果你想阻止这些浏览器默认行为，JavaScript为你提供了方法。
如下代码：
```js
var $a = document.getElementsByTagName("a")[0];
$a.onclick = function(e){
alert("跳转动作被我阻止了")
e.preventDefault();
//return false;//也可以
}
默认事件没有了。
```
既然return false 和 e.preventDefault()都是一样的效果，那它们有区别吗？当然有。 仅仅是在HTML事件属性和DOM0级事件处理方法中，才能通过返回 return false 的形式组织事件宿主的默认行为。
## 3. 如何阻止事件冒泡
w3c 的方法是 e.stopPropagation()，IE 则是使用 e.cancelBubble = true
```js
```handlebars
function stopBubble(e){
    if(e&&e.stopPropagation){//非IE
        e.stopPropagation();
    }
    else{//IE
        window.event.cancelBubble=true;
    }
}
```
在支持 addEventListener() 的浏览器中，可以调用事件对象的一个 stopPropagation()
方法已阻止事件的继续传播。如果在同一对象上定义了其他处理程序，剩下的处理程序将依旧被调用，但调用 stopPropagation()
方法可以在事件传播期间的任何时间调用，它能工作在捕获阶段、事件目标本身中和冒泡阶段。
IE9 之前的IE不支持 stopPropagation() 方法。相反，IE事件对象有一个 cancleBubble 属性，设置这个属性为
true 能阻止事件进一步传播。（ IE8 及之前版本不支持事件传播的捕获阶段，所以冒泡是唯一待取消的事件传播。）
当前的 DOM 事件规范草案在 Event 对象上定义了另一个方法，命名为stopImmediatePropagation()。类似
stopPropagation(),这个方法组织了任何其他对象的事件传播，但也阻止了在相同对象上注册的任何其他事件处理程序的调用。

# 六、JS继承
## 1.基于原型的继承：将父类的实例赋值给子类的原型。这种继承方式的缺点：子类的实例可以访问父类的私有属性，子类的实例还可以更改该属性，这样不安全。
```js
// 父类
 function Staff() {    
   this.company = 'tianchuang';
   this.list = [];
 }
 // 父类的原型
 Staff.prototype.getComName = function() {
  return this.company;
 };

// 子类
     function Coder(name, skill) {
       this.name = name;
       this.skill = skill;
     }

// 继承 Staff
     Coder.prototype = new Staff();

 // 因为子类原型的指向已经变了，所以需要把子类原型的co         ntructor指向子类本身
     Coder.prototype.constructor = Coder;

// 给子类原型添加属性
     Coder.prototype.getInfo = function() {
       return {
         name: this.name,
        skill: this.skill
       };
     };

     let coder = new Coder('小明', 'javascript');

     coder.getInfo(); // {name: '小明', skill: 'javascript'}
     coder.getComName(); // 'tianchuang'
```

## 2.基于class的继承：ES6 中有了类的概念，可以通过 class 声明一个类，通过 extends 关键字来实现继承关系。 class 与 ES5构造函数的主要区别：class 只能通过 new 来调用，而构造函数则可以直接调用； class内部所有定义的方法，都是不可枚举的（non-enumerable）
```js
class Parent {
  constructor(name) {
    this.name = name;
  }
  static say() {
    return 'hello';
  }
}

class Child extends Parent {
  constructor(name, age) {
    super(name); // 调用父类的 constructor(name)
    this.age = age;
  }
}

var child1 = new Child('kevin', '18');

console.log(child1);
```

# 七、数组排序
给出正整数数组 array = [2,1,5,3,8,4,9,5]
请写出一个函数 sort，使得 sort(array) 得到从小到大排好序的数组 [1,2,3,4,5,5,8,9]
新的数组可以是在 array 自身上改的，也可以是完全新开辟的内存。不得使用 JS 内置的 sort API
```js
const arr = [2, 1, 5, 3, 8, 4, 9, 5];
function sort(arr) {
    if (arr.length <= 1) {
        return arr;
    } else if (arr.length > 2) {
        let minIndex = 0;
        let min = arr[minIndex];
        for (let i = 1; i < arr.length; i++) {
            if (arr[i] < arr[minIndex]) {
                minIndex = i;
                min = arr[minIndex]
            }
        }
        arr.splice(minIndex, 1);
        return [min].concat(sort(arr))
    } else {
        return arr[0] > arr[1] ? arr.reverse() : arr;
    }
}

console.log(sort(arr));
```

# 八、你对 Promise 的了解？
## 1. Promise 的用途
Promise对象是JavaScript的异步操作解决方案，为异步操作提供统一接口，可以让异步操作写起来就像再写同步操作的流程，不必一层层的嵌套回调地狱，让回调地狱变得可控。
## 2. 如何创建一个 new Promise（课堂里让大家背过）
```js
new Promise( (resolve, reject) => {} )
```
## 3. 如何使用 Promise.prototype.then（可查 MDN）

```js
const p1 = new Promise( (resolve,reject) => {
  resolve('success!')
} )

p1.then(value => {
  console.log(value)
}, reason => {
  console.error(reason)
})
```
## 4. 如何使用 Promise.all（可查 MDN）
```js
var p = Promise.all([1,2,3,Promise.resolve(444)]);
console.log(p); // Promise { <state>: "fulfilled", <value>: Array[4] }

var p2 = Promise.all([1,2,3,Promise.reject(555)]);
console.log(p2); // Promise { <state>: "rejected", <reason>: 555 }
```
## 5. 如何使用 Promise.race（可查 MDN）
使用Promise.race: Promise.race()方法返回一个 promise，一旦迭代器中的某个promise解决或拒绝，返回的 promise就会解决或拒绝。
```js
var p1 = new Promise( (resolve,reject) => {
  setTimeout(resolve,500,"one");
} )
var p2 = new Promise(() => {
  setTimeout(resolve,200,"two")
})

Promise.all([p1,p2]).then((value) => {
  console.log(value);
},（reason) => {
  console.log(reason)
}) //"two" 两个都完成，但是p2更快

var p3 = new Promise((resolve, reject) => {
  setTimeout(reject,100,"three")
})

Promise.all([p3,p2]).then((value) => {
  console.log(value);
},（reason) => {
  console.log(reason)
}) // three 因为p3更快，所以失败了
```
# 九、跨域
## 1. 什么是同源
浏览器出于安全考虑，只允许与同源的接口交互，不同源的客户端脚本在没有明确授权的情况下不能读写对方的资源。
所谓同源即为 协议，域名和端口都相同。例如:
```js
https://abc.com/a
https://abc.com/b
http://abc.com/c
//1,2同源（协议域名端口都相同）
//3与1，2都不同源（因为协议不同）
```
## 2. 什么是跨域
跨域即为 不同源的两个源相互访问数据的时候受到浏览器的阻止，这就发生了跨域。
## 3. JSONP 跨域
我们在跨域的时候由于当前浏览器不支持cors或者其他某些原因不支持cors，我们必须使用另外一种方法跨域，于是我们就请求一个js文件 ，利用script标签的src请求，这个js文件会执行一个回调，这个回调里面就有我们的数据。回调名字可 以随机形成，以callback参数传递后台，后台一函数执行的形式返回。

优点：兼容ie；可以跨域；

缺点：由于他是script标签，所以无法读取到ajax那么精确的状态（状态吗、响应头），只知道成功和失败；只能发送get请求，不支持post；
## 4. CORS 跨域
当两个不同源的源相互访问数据的时候，需要在被访问的源的响应头里面提前声明可以访问的源，告知浏览器那些源是可以访问自己的。

具体即设置Access-Control-Allow-Origin属性。例如Access-Control-Allow-Origin：http://foo.example.

遗憾的是ie9以下不支持这种做法，因此就有了上面的JSONP跨域。

# 十、对前端的理解
1. 前端即网站前台部分，运行在PC端，移动端等浏览器上展现给用户浏览的网页。随着互联网技术的发展，HTML5，CSS3，前端框架的应用，跨平台响应式网页设计能够适应各种屏幕分辨率，合适的动效设计，给用户带来极高的用户体验。
2. 核心技术：html、css、javascript
3. 前端能干什么？前端工程师通过前端技术完成界面设计,界面制作布局，用户交互，网站维护、网站优化等等。通俗点讲，可以设计、制作网页，给网页加上各种各样的特效和功能。前端干的工作是用户可以直接看得见的。前端主要是考虑怎样能让用户觉得用起来更舒服，考虑界面布局、交互效果、页面加载速度等等，主要是偏向用户看得见的部分，客户端（pc、手机、pad）上浏览web。网站的“前端”是与用户直接交互的部分，包括你在浏览网页时接触的所有视觉内容--从字体到颜色，以及下拉菜单和侧边栏。这些视觉内容，都是由浏览器解析、处理、渲染相关HTML、CSS、Java 文件后呈现而来。
