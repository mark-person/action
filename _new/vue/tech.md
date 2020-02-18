
# VUE 全局变量的几种实现方式
* 模块里的变量用export 暴露出去，当其它地方需要使用时，引入模块global便可。
* 1. 全局变量专用模块 Global.vue
```
export default
{
  colorList,
  colorListLength,
  getRandColor
}
```
* 需要使用全局变量的模块 html5.vue
```
import global_ from 'components/tool/Global'
...
global_.getRandColor

```
* 2. 全局变量模块挂载到Vue.prototype 里。
* Global.js同上，在程序入口的main.js里加下面代码
```
import global_ from './components/tool/Global'
Vue.prototype.GLOBAL = global_
```
* 挂载之后，在需要引用全局量的模块处，不需再导入全局量模块，直接用this就可以引用了
```
getColor: this.GLOBAL.getRandColor,
```





