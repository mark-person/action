
# Vuex 是一个专为 Vue.js 应用程序开发的状态管理模式
https://vuex.vuejs.org/zh/
* 它采用集中式存储管理应用的所有组件的状态，并以相应的规则保证状态以一种可预测的方式发生变化。
# 什么情况下我应该使用 Vuex？
* 如果您不打算开发大型单页应用，使用 Vuex 可能是繁琐冗余的。一个简单的 store 模式就足够您所需了。
如果您需要构建一个中大型单页应用，您很可能会考虑如何更好地在组件外部管理状态，Vuex 将会成为自然而然的选择。



# 状态管理
### 简单状态管理起步使用
* 直接使用共用变量方式

# store 模式：
```js
var store = {
  debug: true,
  state: {
    message: 'Hello!'
  },
  setMessageAction (newValue) {
    if (this.debug) console.log('setMessageAction triggered with', newValue)
    this.state.message = newValue
  },
  clearMessageAction () {
    if (this.debug) console.log('clearMessageAction triggered')
    this.state.message = ''
  }
}
```
* 这种集中式状态管理能够被更容易地理解哪种类型的 mutation 将会发生，以及它们是如何被触发。
当错误出现时，我们现在也会有一个 log 记录 bug 之前发生了什么。
* 此外，每个实例/组件仍然可以拥有和管理自己的私有状态：
```js
var vmA = new Vue({
  data: {
    privateState: {},
    sharedState: store.state
  }
})

var vmB = new Vue({
  data: {
    privateState: {},
    sharedState: store.state
  }
})
···
接着我们继续延伸约定，组件不允许直接修改属于 store 实例的 state，而应执行 action 来分发 (dispatch) 事件通知 store 去改变，
我们最终达成了 Flux 架构。这样约定的好处是，我们能够记录所有 store 中发生的 state 改变，
同时实现能做到记录变更 (mutation)、保存状态快照、历史回滚/时光旅行的先进的调试工具。

# Vuex
cnpm install vuex --save




































