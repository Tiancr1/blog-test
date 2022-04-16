# JS执行时机
## 一、为什么如下代码会打印出6个6？
```js
let i = 0
for(i=0;i<6;i++){
    setTimeout(()=>{
        console.log(i)
    },0)
}
```
### 因为setTimeout是指“过一会儿再执行”，什么是过一会儿？就是指在执行完for循环，再执行setTimeout中的console.log，此时for循环中最后停止时i的值是6，而且循环了6次，所以打印出的是六个6。

## 二、如何打印出0,1,2,3,4,5
```js
for(let i=0;i<6;i++){
    setTimeout(()=>{
        console.log(i)
    },0)
}
```
### 因为在循环中用let声明的i，使i是一个局部变量，只在这个循环中有效，所以每次循环的i都是一个新的变量并被存储下来。

## 三、可以使用立即执行函数的方法，让setTimeout立即被执行从而打印出0,1,2,3,4,5
```js
let i =0
for(i=0;i<6;i++){
    !function(i){
        setTimeout(()=>{
            console.log(i)
        },0)
    }(i);
}
```