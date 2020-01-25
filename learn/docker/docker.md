
#  https://www.runoob.com/docker/centos-docker-install.html

# docker run [OPTIONS] IMGAGE [COMMANDD] [ARG...]
Run a command in a new container
-d --detach=false 前台还是后台
-t --tyy=false 分配tty设备，该可以支持终端登录，默认为false
-i --interactive=false 打开STDIN，用于控制台交互
--name 指定容器名字,后续通过名字进行容器管理
--volume , -v:	绑定一个卷

* docker run -i -t -d ubuntu:lastest (运行一个在后台执行的容器，同时，还能用控制台管理)
* docker run -d ubuntu:lastest ping www.docker.com (运行一个带命令在后台不断执行的容器，不直接展示容器内部信息)

# docker images [OPTIONS][RESPOSITORY[:TAG]]
-a 列出本地所有的镜像
docker images ubuntu(列出本地镜像中REPOSITORY为ubuntu的镜像列表)

# docker ps -a 查看全部容器

# 进入容器 docker attach 
docker attach c_id (但在，使用该命令有一个问题。当多个窗口同时使用该命令进入该容器时，所有的窗口都会同步显示。如果有一个窗口阻塞了，那么其他窗口也无法再进行操作。)
二、使用SSH进入Docker容器
三、使用nsenter进入Docker容器(安装)

# 停止和开启容器
docker stop -f 容器
docker start 容器

# 查看容器状态
docker stats

# 删除容器
如果你要删除的 container 还是运行状态，那么就要先把容器停止了：
docker container stop <container ID>
docker container rm  <container ID>


$ docker run --name my-nginx -v /home/mydocker/nginx-content:/usr/share/nginx/html:ro -d -p 8080:80 nginx










# mysql
docker pull mysql
docker run --name my-mysql -e MYSQL_ROOT_PASSWORD=deng -d mysql
docker run -it --network some-network --rm mysql mysql -hsome-mysql -uexample-user -p



