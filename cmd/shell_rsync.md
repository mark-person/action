
# rsync
-- delete 删除DEST端存在但是SRC端不存在的文件，不使用，则DEST端会同步SCR端的文件，但DEST端已有的文件不受影响

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












