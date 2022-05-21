# 什么是MVC
## 一、定义：
MVC模式（Model-View-Controller）是软件工程中的一种软件架构模式，把软件系统分为三个基本部分：数据模型（Model）、视图（View）、和控制器（Controller）。MVC不是一种技术，而是一种理念。
## 二、目的：
实现一种动态的程序设计，使后续对程序的修改和扩展简化，并使软件某一部分的重复利用成为可能。除此之外，此模式通过对复杂度的简化，使程序结构更加直观。
## 三、三个对象：
数据模型（Model）：模型持有所有的数据、状态和程序逻辑。用于封装与应用程序的业务逻辑相关的数据以及对数据的处理方法。

视图（View）：负责界面的布局和显示。处理控制器里的HTML资料并且将它们插入DOM中。能够实现数据有目的的显示。访问它监视的数据模型（Model）。

控制器（Controller）：负责模型和界面之间的交互。定义用户界面对用户输入的响应方式，起到不同层面间的组织作用，用于控制应用程序的流程和处理事件并做出响应。“事件”包括用户的行为和数据Model上的改变。
```js
/** 模拟 Model, View, Controller */

/** Model 负责存放数据资料 */
const Model = {
    data: {
      数据源
    },
    create: {
      增加数据
    },
    delete: {
      删除数据
    },
    update(data) {
      Object.assign(m.data, data) //用新数据替换旧数据 
      eventBus.trigger('m:update') //eventBus触发'm:update'信息，通知View刷新界面 
    },
    get: {
      获取数据
    }
  }
  /** View 负责将资料输出给用户*/
const View = {
    el: 要刷新的元素，
    html： '要显示在页面上的内容'
    init() {
      v.el: 需要刷新的元素
    }，
    render() {
      刷新页面
    }
  }
  /** Controller 作为连接 M 和 V 的桥梁 */

const Controller = {
    init() {
      v.init() //初始化View 
      v.render() //第一次渲染页面 
      c.autoBindEvents() //自动的事件绑定 
      eventBus.on('m:update', () => {
          v.render()
        } //当enentsBus触发'm:update'是View刷新 
      }，
      events: {
          事件以哈希表的方式记录存储
        },
        method() {
          data = 新数据
          m.update(data)
        },
        autoBindEvents() {
          自动绑定事件
        }
    }
```

# EventBus 有哪些 API，是做什么用的
事件总线是一种设计模式，可以用于简化不同组件之间的通信。它也可以被认为是发布/订阅。组件可以监听事件总线来知道什么时候做它们做的事情。
基本API有on（监听事件）、trigger（emit）（触发事件）、off（取消监听）方法。
```js
//EventBus.js 
class EventBus {
  constructor() {
    this._eventBus = $(window)
  }
  on(eventName, fn) {
    return this._eventBus.on(eventName, fn)
  }
  trigger(eventName, data) {
    return this._trigger.trigger(eventName, data)
  }
  off(eventName, fn) {
    return this._eventBus.off(eventName, fn)
  }
}
export default EventBus //new.js 
import EventBus from 'EventBus.js'
const e = new EventBus()
e.on()
e.trigger()
e.off()
```

# 表驱动编程
## 一、定义
表驱动方法是一种使你可以在表中查找信息，而不必用逻辑语句来把它们找出来的方法。事实上，凡是能通过逻辑语句来选择的事物，都可以通过查表来选择。对简单的情况而言，使用逻辑语句更为容易和直白。但随着逻辑链的越来越复杂，查表法也就愈发显得更具吸引力。
表驱动编程的意义在于逻辑与数据的分离。
## 二、优点
1. 提高了程序的可读性。
2. 减少了重复代码。
3. 可扩展性。
4. 程序有一个明显的主干。
5. 降低了复杂度。
```js
bindEvents(){
    v.el.on('click','#add1',()=>{
    m.data.n +=1
    v.render(m.data.n)
    })
    v.el.on('click','#minus1',()=>{
    m.data.n-=1
    v.render(m.data.n)
    })
    v.el.on('click','#mul2',()=>{
    m.data.n*=2
    v.render(m.data.n)
    })
    v.el.on('click','#divide2',()=>{
    m.data.n/=2
    v.render(m.data.n)
    })
}

使用表驱动取出一个时间的哈希表，清晰的分明了数据和逻辑。
events:{
    'click #aa1':'add',
    'click #minus1':'minus',
    'click #mul2':'mul',
    'click #divide2':'div'
},
add(){
    m.update( data: {n:m.data.n +1})
},
minus(){
    m.update( data:{n:m.data.n -1})
},
mul(){
    m.update( data: {n:m.data.n *2})
},
div(){
    m.update(data: {n:m.data.n /2})
}
```
# 什么是模块化编程
模块化是将代码封装起来放在独立的模块中，只留下必要的接口方便供给他人使用。
它的维护性高，它的每个封装模块都是独立的。
需要改编或提出其他需求，不会影响其他文件内容。
复用性高，一个封装的模块能够被多次调用，省去重复编写时间。
