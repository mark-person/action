
# 钩子函数
* WINDOWS的钩子函数可以认为是WINDOWS的主要特性之一。利用它们，您可以捕捉您自己进程或其它进程发生的事件。
	通过“钩挂”，您可以给WINDOWS一个处理或过滤事件的回调函数，该函数也叫做“钩子函数”，当每次发生您感兴趣的事件时，WINDOWS都将调用该函数。
* 常见的钩子函数：react的生命周期函数、vue的生命周期函数等


# vue中提供了一种混合机制--mixins，用来更高效的实现组件内容的复用
* 组件在引用之后相当于在父组件内开辟了一块单独的空间，来根据父组件props过来的值进行相应的操作，单本质上两者还是泾渭分明，相对独立。
* 而mixins则是在引入组件之后，则是将组件内部的内容如data等方法、method等属性与父组件相应内容进行合并。相当于在引入后，父组件的各种属性方法都被扩充了。

* 单纯组件引用：父组件 + 子组件 >>> 父组件 + 子组件
* mixins: 父组件 + 子组件 >>> new父组件
# 作用:多个组件可以共享数据和方法
* 在使用mixin的组件中引入后，mixin中的方法和属性也就并入到该组件中，可以直接使用。
	钩子函数会两个都被调用，mixin中的钩子首先执行。


# 使用
* 1.定义一个 js 文件(mixin.js)
```
export default {
 data() {
  return {
   name: 'mixin'
  }
 },
 created() {
  console.log('mixin...', this.name);
 },
 mounted() {},
 methods: {}
}
```
* 2.在vue文件中使用mixin
```
import mixin from '@/mixin'; // 引入mixin文件
export default {
 mixins: [mixin]
}
```






