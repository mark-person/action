
# rsync
-- delete 删除DEST端存在但是SRC端不存在的文件，不使用，则DEST端会同步SCR端的文件，但DEST端已有的文件不受影响
-- delete 是在接收端执行的，所以它是在exclude/include规则生效之后才执行的


快速删除大量文件
1.先建一个空目录 mkdir /local/empty_dir
2.用rsync删除目标目录 rsync --delete-before -avH --progress /local/empty_dir/ /local/trainer_test/
3.trainer_test清空之后可以再用rm -rf trainer_test删除

-a 递归方式传输文件，并保持文件属性
--delete-before 接收者在传输之前时行删除操作
--progress 在传输时显示传输过程
-v 详细输出模式
-H 保持硬连接的文件

# 硬链接(hard link)
A是B的硬链接(A和B都是文件名), 则A的目录项中的inode节点号和B的目录项的inode节点号相同，
即一个inode节点对应两个不同的文件名，两个文件名指向同一个文件，A和B对应文件系统来说是完全平等的。
如果删除了其中一个，对另外一个没有影响。

# 软链接(soft link)
"主从"关系，如果B被删除了，A仍然存在，但指向的是一个无效链接


-n --dry-run 仅测试传输，而不实际传输。常和"-vvvv"配合使用来查看rsync是如何工作的
-v 显示rsync过程中详细信息。可以使用"-vvvv"获取更详细信息
-r --recursive: 递归到目录中去
-a --archive: 归档模式，表示递归传输并保持文件属性。

-z 传输时进行压缩提高效率

--exclude 指定排除规则来排除不需要传输入的文件
--include 只作用于发送端，被包含的文件将明确记录到文件列表中

注:一个"--exclude"只能指定一条规则，要指定多条排除规则，需要使用多个"--exclude"选项，或者将排除规则写入到文件中，
然后使用"--exclude-from"选项读取该规则文件
























