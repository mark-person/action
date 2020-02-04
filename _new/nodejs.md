

# nodejs
node --version #v12.14.1


# npm (Node.js Package Management)

# npm --save -g
* npm 加了--save 依赖模块的版本信息都会写入 package.json 中
这样每次换服务器部署的时候 直接 cp package 文件 执行 npm install 
就可以按照 package.json 中的信息（还原）部署好一样依赖运行环境
* -g 全局安装，在${user}/目录


# install express
$ npm install express --save


# NodeJs批量require文件夹中的所有文件
```
npm i require-all --save (cnpm i require-all)

const controllers = require('require-all')({
  dirname: __dirname + '/controllers',
})
console.log(controllers.user)
```
该模块还提供了一些额外参数：
```
const controllers = require('require-all')({
  dirname     :  __dirname + '/controllers',
  filter      :  /(.+Controller)\.js$/,
  resolve     : function (Controller) {
    return new Controller();
  }
});
```

# 淘宝镜像
1.安装npm淘宝镜像  cnpm
	npm install -g cnpm --registry=https://registry.npm.taobao.org

# nodejs vue
* cnpm install -g @vue/cli
* vue create myvue
选(空格选中)Babel和Router
* 启动
cd myvue
npm run serve
* 访问http://localhost:8080/
打包：npm run build.

# npm run build
发布生产：dist
Building for production...

# markdown
* npm install showdown --save

# markdown load
* cnpm i markdown-loader html-loader --save

# 只需要在marked的配置中添加highlight项即可（要先npm install highlight.js）

cnpm install highlight.js --save
cnpm install marked --save


# npm install github-markdown-css 或 cnpm install github-markdown-css复制代码
import 'github-markdown-css';复制代码
<div class="markdown-body"></div>









