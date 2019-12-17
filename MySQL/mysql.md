## 1.使用MySQL时可以做哪些优化？
-   选择合适的数据库引擎
-   字段类型尽可能用小的类型代替
-   where条件，group by, order by 字段加适量索引
-   自增类型的主键

## 2.MySQL有哪些存储引擎？MyIsAM和InnoDB的区别？
-   存储引擎
    -   MyIsAM
    -   InnoDB
    -   Memory
-   MyIsAM和InnoDB的区别
    -   是否支持事务
    -   是否支持行锁
    -   是否支持外键          

## 3.索引有哪些类型？功能、优缺点是什么？
-   主键
-   唯一键
-   外键
-   普通索引
-   全文索引

## 4.MySQL主从复制原理
-   Master服务器开启binlog,执行的事务操作写入到日志
-   Slave 异步io线程读取Master上的binlog写入到自己的中继日志
-   Slave 读取中继日志写入到自己

## 5.主从复制延迟
-   查看主从复制是否有延迟： 命令:show slave status   Seconds_Behind_Master的值是延时时间单位ms
-   解决办法:
    -   从库IO多线程复制
    -   升级丛库的硬件资源
    -   分库，将原来一个库分成多个库
 

