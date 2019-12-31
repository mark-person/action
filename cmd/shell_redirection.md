
# 标准输入文件stdin 0，标准输出文件stdout 1，标准错误文件stderr 2
文件类型:l 
/dev/stdin  -> /proc/self/fd/0
/dev/stdout -> /proc/self/fd/1
/dev/stderr -> /proc/self/fd/2

# /dev/null
文件类型:c
cat /dev/null > /home/omc/h.txt # 清空文件
大部分在 crontab 计划任务中都会年到未尾带 >/dev/null 2>&1
1 表示stdout标准输出,系统默认值是1,所以 ">/dev/null" 等同于 "1>/dev/null"
2 表示stderr标准错误
& 表示等同于的意思,2>&1,表示2的输出重定向等同于1

# command > file 2>file 与 command > file 2>&1 有什么区别呢?

command > file 2>file 的意思是将命令所产生的标准输出信息,和错误的输出信息送到file 中.
command > file 2>file 这样的写法,stdout和stderr都直接送到file中, file会被打开两次,
	这样stdout和stderr会互相覆盖,这样写相当使用了FD1和FD2两个同时去抢占file 的管道.

而command >file 2>&1 这条命令就将stdout直接送向file, stderr 继承了FD1管道后,再被送往file,4
	此时,file 只被打开了一次,也只使用了一个管道FD1,它包括了stdout和stderr的内容.6












