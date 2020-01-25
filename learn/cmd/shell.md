

# Shell 变量

不要以为由管道串起的两个命令会依次执行。Linux系统实际上会同时运行这两个命令，在
系统内部将它们连接起来。在第一个命令产生输出的同时，输出会被立即送给第二个命令。数据
传输不会用到任何中间文件或缓冲区

如果是明确一定时间范围的日志还是可以根据时间截取日志：
// 截取一定时段的日志
sed -n '/2018-10-25 17:30:41/,/2018-10-25 21:47:02/p' root.2018-10-25.log > update.log


# 命令
* 在bash中，$( )与` `（反引号）都是用来作命令替换的。
>>> 命令替换与变量替换差不多，都是用来重组命令行的，先完成引号里的命令行，然后将其结果替换出来，再重组成新的命令行。
echo today is $(date "+%Y-%m-%d")
echo today is `date "+%Y-%m-%d"`

* ${ }变量替换
>>> 一般情况下，$var与${var}是没有区别的，但是用${ }会比较精确的界定变量名称的范围

# 取路径、文件名、后缀 https://www.cnblogs.com/chengd/p/7803664.html

# 取子串及替换 
${file:0:5}

# split()
arr=(${line//,/ })  
year=${arr[0]}
userId=${arr[1]}


# Shell 数组
Bash Shell 只支持一维数组，Shell 数组用括号来表示，元素用"空格"符号分割开
array_name=(value1 ... valuen)
${array_name[index]}
获取数组长度的方法与获取字符串长度的方法相同
${#my_array[*]}
${#my_array[@]}

 str='abc';echo ${#str}法

```
# 字符串判断
str1="abc"
str2=""
if [ ! "$str1" = "$str2" ];  then
  echo 'yes'
else
  echo 'no'
fi
```

# 判断文件类型
r=$(file -i a.txt | grep us-ascii)
if [ "${r}" == "" ]; then
  echo 'NO'
else
  echo 'YES'
fi



# Shell 函数
报: numeric argument required
Shell 函数返回值只能是整形数值，一般是用来表示函数执行成功与否的，0表示成功，其他值表示失败。
```
gVal='abc'
test() {
  gVal='efg'
  return 0
}
test
echo $?
echo $gVal
```

单引号内嵌套单引号即可使用变量。
```
i=10
echo $i
echo '$i'
echo '$i is : '$i''

```
```
* 单引号属于强引用，它会忽略所有被引起来的字符的特殊处理，被引用起来的字符会被原封不动的使用，唯一需要注意的点是不允许引用自身；
* 双引号属于弱引用，它会对一些被引起来的字符进行特殊处理
1.$加变量名可以取变量的值  2.反引号和$()引起来的字符会被当做命令执行后替换原来的字符 3.当需要使用字符（$  `  "  \）时必须进行转义，也就是在前面加\ 


# Shell特殊变量

* $0 当前脚本的文件名
* $n 第一个参数是$1，第二个参数是$2
* $# 传递给脚本或函数的参数个数
* $* 传递给脚本或函数的所有参数
* $@ 传递给脚本或函数的所有参数。被双引号(" ")包含时，与 $* 稍有不同
* $? 上个命令的退出状态，或函数的返回值。

* $$ Shell本身的PID（ProcessID）
* $! Shell最后运行的后台Process的PID, 启动后台服务常用来保存pid
* 

# source
source filename [arguments]
  Excute commands from a file in the current shell.
  The entries in $PATH are used to find the directory containing FiLENAME.
也称为"点命令"(.),bash的内部命令.
* 通常用于重新执行刚修改的初始化文件，使之立即生效，而不必注销并重新登录。
* 用法 source filename或.filename

# source filename、sh filename及./filename区别
1.当shell脚本具有可执行权限时，用sh filename与./filename执行脚本是一样的。
./filename是因为当前目录没有在PATH中，"."是用来表示当前目录的
2.sh filename重新建立一个子shell，在子shell中执行脚本里面的语句，该子shell继承父shell的环境变量，
但子shell新建的，改变的变量不会被带回到父shell，除非使用export.
3.source filename:简单地读取脚本里面的语句依次在当前shell里面执行，没有建立新的子shell。
那么脚本里面所有新建、改变变量的语句都会保存在当前shell里面.





































