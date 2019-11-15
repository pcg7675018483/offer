## 1.Redis什么情况下会删除key? 
-   key过期
-   当前已用内存超过maxmemory限定时，触发主动清理策略
    -   volatile-lru：只对设置了过期时间的key进行LRU（默认值）
    -   allkeys-lru ： 删除lru算法的key
    -   volatile-random：随机删除即将过期key
    -   allkeys-random：随机删除
    -   volatile-ttl ： 删除即将过期的
    -   noeviction ： 永不过期，返回错误 
    
## 2.采用什么方法删除？
| 方法类型  | 说明 | 缺点 |
|  ----   | ---- | ---- |
| 被动删除  | 当读/写一个已经过期的key时，会触发惰性删除策略，直接删除掉这个过期key | 缺点过期的key无法及时清理占用内存 |
| 主动删除  | 定时任务定期(默认每秒执行10次,可通过hz参数调整)淘汰一批过期的key    | 抽取部分key，有部门key过期后无法及时删除（被动删除可弥补）|
| 主动删除  | 当前已用内存超过maxmemory限定时，触发主动清理策略                | 设置noeviction时redis无法继续写入 |

## 3.redis定期删除key为什么只删除部分过期而不是全部？

删除过多的key消耗的时间过长会阻塞redis的正常运行
``
针对每个db在限制的时间REDIS_EXPIRELOOKUPS_TIME_LIMIT内迟可能多的删除过期key，之所以要限制时间是为了防止过长时间 的阻塞影响redis的正常运行。这种主动删除策略弥补了被动删除策略在内存上的不友好。
``

## 4.redis为什么单线程性能却很好

## 5.redis持久化方式
-   RDB:
-   AOF:

## 6.redis架构模式哪几种

## 7.如何解决缓存雪崩，击穿，崩溃

## 8.项目中哪些场景用到的redis？为什么要用redis？直接使用内存是否可行？
-   排行榜（zSet）
-   用户间的互相关注
-   缓存验证码
  