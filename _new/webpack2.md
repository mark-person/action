
# 生产环境构建
* 开发环境(development)和生产环境(production)的构建目标差异很大
开发：我们需要具有强大的、具有实时重新加载(live reloading)或热模块替换(hot module replacement)能力的 source map 和 localhost server。
生产：关注更小的 bundle，更轻量的 source map，以及更优化的资源，以改善加载时间

* 建议：每个环境编写特此独立的webpack配置
遵循不重复原则(Don't repeat yourself - DRY)，保留一个“通用”配置。

* webpack-merg 
>> 为了将这些配置合并在一起，我们将使用一个名为 webpack-merge 的工具。
通过“通用”配置，我们不必在环境特定(environment-specific)的配置中重复代码。
```
npm install --save-dev webpack-merge
```

### source map
鼓励你在生产环境中启用 source map，因为它们对调试源码(debug)和运行基准测试(benchmark tests)很有帮助
* 对于本指南，我们将在生产环境中使用 source-map 选项，而不是我们在开发环境中用到的 inline-source-map：

* 避免在生产中使用 inline-*** 和 eval-***，因为它们可以增加 bundle 大小，并降低整体性能。

### 指定环境
许多 library 将通过与 process.env.NODE_ENV 环境变量关联，以决定 library 中应该引用哪些内容。例‘
```
+     }),
+     new webpack.DefinePlugin({
+       'process.env.NODE_ENV': JSON.stringify('production')
+     })

// 引用
+ if (process.env.NODE_ENV !== 'production') {
+   console.log('Looks like we are in development mode!');
+ }

```

### Split CSS
正如在管理资源中最后的 加载 CSS 小节中所提到的，通常最好的做法是使用 ExtractTextPlugin 将 CSS 分离成单独的文件。
在插件文档中有一些很好的实现例子。disable 选项可以和 --env 标记结合使用，以允许在开发中进行内联加载，推荐用于热模块替换和构建速度。

### CLI 替代选项
以上描述也可以通过命令行实现。例如，--optimize-minimize 标记将在后台引用 UglifyJSPlugin。和以上描述的 DefinePlugin 实例相同，--define process.env.NODE_ENV="'production'" 也会做同样的事情。并且，webpack -p 将自动地调用上述这些标记，从而调用需要引入的插件。


### 代码分离
* 代码分离是 webpack 中最引人注目的特性之一。此特性能够把代码分离到不同的 bundle 中，然后可以按需加载或并行加载这些文件。
代码分离可以用于获取更小的 bundle，以及控制资源加载优先级，如果使用合理，会极大影响加载时间。

#### 有三种常用的代码分离方法：
* 入口起点：使用 entry 配置手动地分离代码。
* 防止重复：使用 CommonsChunkPlugin 去重和分离 chunk。
* 动态导入：通过模块的内联函数调用来分离代码。

https://www.webpackjs.com/guides/code-splitting/

代码分离是webpack中最引人注目的特性之一。此特性能够把代码分离到不同的 bundle 中，然后可以按需加载或并行加载这些文件。
代码分离可以用于获取更小的 bundle，以及控制资源加载优先级，如果使用合理，会极大影响加载时间。

* 入口起点:entry points(最简单、最直观的分离代码的方式)
>> * 分动配置较多，并有一些陷阱
```
|- /src
  |- index.js
+ |- another-module.js

entry: {
    index: './src/index.js',
    another: './src/another-module.js'
}

// another-module.js
import _ from 'lodash';

console.log(
  _.join(['Another', 'module', 'loaded!'], ' ')
);

```
* 正如前面提到的，这种方法存在一些问题:
>> * 如果入口chunks之间包含重复的模块，那些重复模块都会被引入到各个bundle中。
>> * 这种方法不够灵活，并且不能将核心应用逻辑进行动态拆分代码。

##### 防止重复(prevent duplication)
CommonsChunkPlugin 插件可以将公共的依赖模块提取到已有的入口 chunk 中，或者提取到一个新生成的 chunk。
```
plugins: [

+     }),
+     new webpack.optimize.CommonsChunkPlugin({
+       name: 'common' // 指定公共 bundle 的名称。
+     })
```
* 这里我们使用 CommonsChunkPlugin 之后，现在应该可以看出，index.bundle.js 中已经移除了重复的依赖模块

#### 动态导入(dynamic imports)
* 当涉及到动态代码拆分时，webpack提供了两个类似的技术.
>> * 第一种，也是优先选择的方式是，使用符合ECMAScript提案的import()语法。
>> * 第二种，则是使用webpack特定的require.ensure.

```
+     chunkFilename: '[name].bundle.js',

```















 


















