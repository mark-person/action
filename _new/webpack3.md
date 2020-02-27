# 懒加载
* 懒加载或者按需加载，是一种很好的优化网页或应用的方式
* 这样加快了应用的初始加载速度，减轻了它的总体体积，因为某些代码块可能永远不会被加载。
```
+   // Note that because a network request is involved, some indication
+   // of loading would need to be shown in a production-level site/app.
+   button.onclick = e => import(/* webpackChunkName: "print" */ './print').then(module => {
+     var print = module.default;
+
+     print();
+   });
```
VUE
```
Vue.component("AsyncCmp", () => import("./AsyncCmp"));

new Vue({
  // ...
  components: {
    AsyncCmp: () => import("./AsyncCmp")
  }
})

// rooter
// Instead of: import Login from './login'
const Login = () => import("./login");

new VueRouter({
  routes: [{ path: "/login", component: Login }]
});

```
https://www.webpackjs.com/guides/code-splitting/

# 缓存
* 此指南的重点在于通过必要的配置，以确保 webpack 编译生成的文件能够被客户端缓存，而在文件内容变化后，能够请求到新的文件。
### 输出文件的文件名(Output Filenames)
* 通过使用 output.filename 进行文件名替换，可以确保浏览器获取到修改后的文件。
[hash] 替换可以用于在文件名中包含一个构建相关(build-specific)的 hash，但是更好的方式是使用 [chunkhash] 替换，
在文件名中包含一个 chunk 相关(chunk-specific)的哈希。
```
    output: {
-     filename: 'bundle.js',
+     filename: '[name].[chunkhash].js',
      path: path.resolve(__dirname, 'dist')
    }
```
### 提取模板(Extracting Boilerplate)
就像我们之前从代码分离了解到的，CommonsChunkPlugin 可以用于将模块分离到单独的文件中。
然而 CommonsChunkPlugin 有一个较少有人知道的功能是，能够在每次修改后的构建结果中，将 webpack 的样板(boilerplate)和 manifest 提取出来。通过指定 entry 配置中未用到的名称，
此插件会自动将我们需要的内容提取到单独的包中：

### 模块标识符(Module Identifiers)
第一个和最后一个都是符合预期的行为 -- 而 vendor 的 hash 发生变化是我们要修复的。幸运的是，
可以使用两个插件来解决这个问题。第一个插件是 NamedModulesPlugin，将使用模块的路径，而不是数字标识符。
虽然此插件有助于在开发过程中输出结果的可读性，然而执行时间会长一些。
第二个选择是使用 HashedModuleIdsPlugin，推荐用于生产环境构建：

### 创建 library
* 除了打包应用程序代码，webpack 还可以用于打包 JavaScript library。



































