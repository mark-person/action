

# VUE CLI 3的webpack配置
* npm run serve和npm run build (package.json)
* npm run时会新建一个shell,他会node_modules/.bin加入path变量中.
```
"scripts": {
    "serve": "vue-cli-service serve",
    "build": "vue-cli-service build"
  },
```

### vue-cli3 项目配置 vue.config.js
* 之前的build和config文件夹不见了，那么应该如何像webpack那样
* 根目录创建vue.config.js
```
module.exports = {
	// 基本路径
	baseUrl: '/',
	outputDir: 'dist',
	
}

```

### webpack中loader的简单使用




















