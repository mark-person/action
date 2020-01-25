
curl -i --range 0-9 http://www.baidu.com/img/bdlogo.gif
上面是curl获取到的响应头信息，其中如果能够找到Content-Range则表明服务器支持断点续传，有些服务器还会返回Accept-Ranges



>>>> wget -S http://www.baidu.com/img/bdlogo.gif 2>&1 | grep 'Accept-Ranges'

如果能看到输出Accept-Ranges，则表明服务器支持断点续传，否则不支持。

Nginx服务器默认支持断点续传的，无须做任何额外配置。

