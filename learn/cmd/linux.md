# wget 断点续传下载 
wget -c 要下载的文件

# file -i a.txt
a.txt: text/plain; charset=us-ascii

# iconv
Converts text form one encoding to another encoding
-f the encoding of the input (GBK) --from-code=GBK
-t the encoding of the output (UTF-8) --to-code=UTF-8
-o output file --output=FILE

# ssh
* 登录:ssh -p22 omd@192.168.25.137
* 直接执行命令:ssh root@192.168.25.137 /bin/ls -ltr /backup/data

* cat /root/.ssh/known_hosts 
ssh会把你每个你访问过计算机的公钥(public key)都记录在~/.ssh/known_hosts。

# scp (全量copy)
scp -p22 -r -p /home/omd/h.txt omd@192.168.1.137:/home/omd/
可以推送过去，也可以拉过来

# sftp
sftp -oPort=22 root@192.168.25.137 
put /etc/hosts /tmp
get /etc/hosts /home/omd 
































