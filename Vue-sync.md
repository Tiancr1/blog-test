#  Vue 中的 .sync 修饰符有什么用
Vue 中的.sync 修饰符的功能是 : 当一个子组件改变了一个 prop 的值时，这个变化也会同步到父组件中所绑定。

我们通过一个场景来辅助理解一下。

场景描述
爸爸给儿子打钱，儿子要花钱怎么办?
答 : 儿子打电话（触发事件）向爸爸要钱
示例 :

## App.vue
```js
<template>
  <div class="app">
    App.vue 我现在有 {{total}}
    <hr>
    <Child :money.sync="total"/>
  </div>
</template>

<script>
import Child from "./Child.vue";
export default {
  data() {
    return { total: 10000 };
  },
  components: { Child: Child }
};
</script>
```
## Child.vue
```js
<template>
  <div class="child">
    {{money}}
    <button @click="$emit('update:money', money-100)">
      <span>花钱</span>
    </button>
  </div>
</template>

<script>
export default {
  props: ["money"]
};
</script>
```
其中：
```v
:money.sync="total"
```
等价于
```v
:money="total" v-on:update:money="total=$event"
```

## 注意
1. Vue规则 : 组件不能修改props外部数据
2. Vue规则 : this.$event可以触发事件，并传参
3. Vue规则 : $event可以获取$emit的参数