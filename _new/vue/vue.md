

# location路由模式 /user
* nginx配置 try_files
```
location  / {
	root /~~~/ dist;
	# uri nginx变量
	try_files $uri /index.html 
}
```
* 用try_files 进行尝试,如果获取不到资源,加载index.htm


