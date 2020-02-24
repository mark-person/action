

# npm install webpack webpack-cli --save-dev
https://www.webpackjs.com/guides/asset-management/

# asset-management
* webpack最出色的功能之一就是，除了JavaScript， 还可以通过loader引入任何其它类型的文件。
### 加载CSS
准备: npm install --save-dev style-loader css-loader

* 请注意，在多数情况下，你也可以进行 CSS 分离，以便在生产环境中节省加载时间。
最重要的是，现有的 loader 可以支持任何你可以想到的 CSS 处理器风格 - postcss, sass 和 less 等。

### 加载图片
* 使用 file-loader，我们可以轻松地将这些内容混合到 CSS 中：
* 合乎逻辑下一步是，压缩和优化你的图像。查看 image-webpack-loader 和 url-loader。

### 加载数据
* JSON 支持实际上是内置的, 要导入 CSV、TSV 和 XML，你可以使用 csv-loader 和 xml-loader。

### 全局资源
* 你可以以更直观的方式将模块和资源组合在一起， 因为现有的统一放置的方式会造成所有资源紧密耦合在一起
* - |- /assets
+ |– /components
+ |  |– /my-component
+ |  |  |– index.jsx
+ |  |  |– index.css
+ |  |  |– icon.svg
+ |  |  |– img.png

### 管理输出
```
cnpm install --save-dev html-webpack-plugin
```
*  HtmlWebpackPlugin作用
> * 为html文件中引入的外部资源如scipt、link动态添加每次compile后的hash,
	防止引用缓存的外部文件问题
> * 可以生成创建html入口文件，比如单页面可以生成一个html文件入口，配置N个
	html-webpack-plugin可以生成N个页面入口
* clean-webpack-plugin
```
npm install clean-webpack-plugin --save-dev
```



### 开发
为了更容易地追踪错误和警告，JavaScript提供了source map功能，将编译后的代码映射回原始源代码。
inline-source-map选项（不要用于生产环境）

* +   devtool: 'inline-source-map',
我们可以看到，此错误包含有发生错误的文件（print.js）和行号（2）的引用。
这是非常有帮助的，因为现在我们知道了，所要解决的问题的确切位置。

#### 选择一个开发工具

* webpack 中有几个不同的选项，可以帮助你在代码发生变化后自动编译代码：
>> * webpack's Watch Mode
>> * webpack-dev-server
>> * webpack-dev-middleware



多数场景中，你可能需要使用 webpack-dev-server
```
      "test": "echo \"Error: no test specified\" && exit 1",
+     "watch": "webpack --watch",
      "build": "webpack"
npm run watch 
# 缺点需要刷新代码	  
```


```
devtool: 'inline-source-map',
+   devServer: {
+     contentBase: './dist'
+   },

npm install --save-dev webpack-dev-server

+     "start": "webpack-dev-server --open",

```


##　模块热替换（HMR 不适用于生产环境，这意味着它应当只在开发环境使用）
模块热替换(Hot Module Replacement 或 HMR)是 webpack 提供的最有用的功能之一。它允许在运行时更新各种模块，而无需进行完全刷新。


# tree shaking
* tree shaking 是一个术语，通常用于描述移除 JavaScript 上下文中的未引用代码(dead-code)。

```
export function square(x) {
  return x * x;
}

export function cube(x) {
  return x * x * x;
}

# 只import了cube
import { cube } from './math.js';

# square叫 这个功能是所谓的“未引用代码(dead code)”，

```







