
elasticsearch-7.5.1 自带jdk13

1.修改/etc/profile(所有用户能用) 2.修改.bash_profile(用户使用)
export JAVA_HOME=/home/ppx/java/jdk-11.0.1
export PATH=$JAVA_HOME/bin:$PATH 
重新登录

tar zxf x.tar

adduser search
passwd search
deng8*****

chmod -v u+w /etc/sudoers
## Allow root to run any commands anywhere
root    ALL=(ALL)       ALL
search    ALL=(ALL)       ALL （添加这一行）

folder to folder
cp -r

目录权限
chmod -R 修改成的权限 要修改哪个文件夹

结果curl "http://127.0.0.1:9200" 能够正常访问，可是使用外网ip就提示拒绝链接

解决办法：vim config/elasticsearch.yml

增加：
network.host: 0.0.0.0
http.port: 9200

[1]: max virtual memory areas vm.max_map_count [65530] is too low, increase to at least [262144]
解决方法：切换到root用户修改配置sysctl.conf
vi /etc/sysctl.conf
添加
vm.max_map_count=655360
sysctl -p


ERROR: [1] bootstrap checks failed
[1]: the default discovery settings are unsuitable for production use; at least one of [discovery.seed_hosts, discovery.seed_providers, cluster.initial_master_nodes] must be configured
修改
elasticsearch.yml
取消注释保留一个节点
cluster.initial_master_nodes: ["node-1"]
这个的话，这里的node-1是上面一个默认的记得打开就可以了

>>>>>>>>>>>>>>>>>>>
工具
kibana

https://www.elastic.co/cn/downloads/kibana



