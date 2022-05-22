#  vue两个版本对应的文件名
## 一、Vue完整版
文件名：vue.js

优点：含有编译器，可以将视图直接写入html

缺点：文件体积较大，用户要下载很大的文件，体检较差

## 二、Vue非完整版
文件名：vue.runtime.js

优点：文件体积小，用户加载很快，体验较好

缺点：没有编译器，无法将html编译成视图，开发时需要将视图写到render函数里，对开发者来说不直观，体验较差

#  template和render的使用

## 一、template
template：视图写在html或者vue中，使用方法为：
```js
template: `

<div>Hello</div>

`
```
## 一、render
render：视图写在render函数里创建标签使用方法为：
```js
new Vue({

 render (h) {

   return h('div', this.hi)

  }

})
```

# 如何用 codesandbox.io 写 Vue 代码
使用在线沙盒网站：https://codesandbox.io/

注意，使用时不要登录，因为登录后只能创建50个应用，但是不登录可以创建无数个

在沙盒中可以很快速地创建一个VUE应用，开发完成后可以导出到本地。
