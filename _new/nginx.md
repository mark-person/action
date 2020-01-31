
# nginx预安装
### 一. gcc 安装 yum install gcc-c++
### 二. PCRE pcre-devel 安装 yum install -y pcre pcre-devel
### 三. zlib 安装(gzip) yum install -y zlib zlib-devel
### 四. OpenSSL 安装 yum install -y openssl openssl-devel


# nginx安装
* wget -c https://nginx.org/download/nginx-1.16.1.tar.gz
* tar -zxvf nginx-1.16.1.tar.gz
* cd nginx-1.16.1/
* ./configure
* make
* make install

```shell
cd /usr/local/nginx/sbin/
./nginx 
./nginx -s stop
./nginx -s quit
./nginx -s reload
```

# 重新加载配置文件
./nginx -s reload

# 开机自启动
vi /etc/rc.local
增加一行 /usr/local/nginx/sbin/nginx
chmod 755 rc.local

# 文件夹
* /usr/local/nginx/conf/nginx.conf
* /usr/local/nginx/html





