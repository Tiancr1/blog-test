# JS的基本语法

## 表达式和语句
1. 表达式一般都有值，语句可能有也可能没有
2. 语句一般会改变环境（声明，赋值）
``` js
var a = 1;  //是一个语句
1+2 = 3 //是一个表达式
console.log //是一个表达式
```
## 标识符的规则
### 一、规则
1. 第一个字符可以使Unicode字母或$或_或中文
2. 标识符不能以数字开头
3. 后面的字符，除了上面所说，还可以有数字
4. 标识符不能是ES关键字或保留字
5. 标识符一般采用驼峰命名方法，例如：helloWorld
### 二、举例
``` js
var _ = 1
var $ = 1
var 你好 = ‘hi’
var hi123 = 567
var helloWord = 1
```

## if else语句
### 一、语法
if(表达式){
    语句1   
}else{
        语句2
    }
### 二、变态情况
1. 语句1可以嵌套if else语句
2. 语句2可以嵌套if else语句
3. 可以省略{}直接用缩进表示关系
### 三、举例
```js
a = 1
if (a === 2)
    console.log('a')
    console.log('a等于2')
//打印出的结果应该是“a等于2”，因为第一个语句是跟if走的，第二个语句相当于是else

//推荐使用写法
a = 1
if (a === 1){
    console.log('a')
}else{
    console.log('a等于2')
}
//次推荐使用写法
function max(a,b){
    if(a>b)return a;
    else return b;
}
```
### 四、switch语句
```js
a = 1
switch(a){
    case 1:
    case 3:
        console.log('单数');
        break;
    case 2:
    case 4:
        console.log('双数');
        break
}
```
### 五、简单表达式（问号冒号表达式）
```js
function max(a,b){
    return a<b ? a: b;
}
```
### 六、短路逻辑&&和||
1. a&&b 表示如果a是ture则取b的值，如果a是false则返回a的值
2. a||b 表示如果a是ture则取a的值，如果a是false则返回b的值

### 七、总结几种条件语句
1. if...else...
2. switch
3. A?B:C
4. A&&B
5. A||B
6. A=A||B
## while for语句
### 一、语法
while(表达式){语句}

1. 判断表达式的真假
2. 表达式为真则执行语句，执行完再判断表达式的真假
3. 表达式为假，执行后面的语句
```js
var i= 1
while (i<10){
    console.log(i)
    i = i + 1
}
```

### 二、for循环
for是while循环的方便写法

for（语句1；表达式2；语句3）{
    循环体
}

1. 先执行语句1
2. 然后判断表达式2
3. 如果为真，执行循环体，再执行语句3
4. 如果为假，直接退出循环，执行后面的语句
```js
for (var i = 1;i<5;i++){
    console.log(i)
}
```
## breake continue
```js
for(var i=1;i<10;i++){
    if(i=1){
        break;
    }
}
```
```js
for (var i = 1;i < 10;i++){
    if(i % 2 === 1){
        continue
    }else{
        console.log(i)
    }
}
```

## labal
```js
//a是标签，语句是1
{
    a:1
}