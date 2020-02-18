
# 解决MySQL事务未提交导致死锁报错 避免死锁的方法
解决mysql 事务未提交导致死锁报错：

        当 sessionA 尝试修改 B 表数据，因为 sessionB 当前为锁定状态，而且 sessionB 对 B 表中数据具有锁定状态中，则出现死锁。sessionB 会自动终止尝试修改 A 表数据事务， 两个事务操作都被终止，并返回下面错误信息。
ERROR 1205 (HY000): Lock wait timeout exceeded; try restarting transaction

# mysql> SELECT * FROM information_schema.INNODB_TRX\G
*************************** 1. row ***************************
                    trx_id: 45900
                 trx_state: ROLLING BACK
               trx_started: 2018-04-09 10:24:38
     trx_requested_lock_id: NULL
          trx_wait_started: NULL
                trx_weight: 30687
       trx_mysql_thread_id: 0
                 trx_query: NULL
       trx_operation_state: NULL
         trx_tables_in_use: 0
         trx_tables_locked: 0
          trx_lock_structs: 1
     trx_lock_memory_bytes: 320
           trx_rows_locked: 1
         trx_rows_modified: 30686
   trx_concurrency_tickets: 0
       trx_isolation_level: REPEATABLE READ
         trx_unique_checks: 1
    trx_foreign_key_checks: 1
trx_last_foreign_key_error: NULL
 trx_adaptive_hash_latched: 0
 trx_adaptive_hash_timeout: 10000

———————————————

https://blog.csdn.net/xuheng8600/article/details/79868122



