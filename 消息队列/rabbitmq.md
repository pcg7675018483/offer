## 1.RabbitMQ 队列有哪些类型

## 2.消息队列的作用与使用场景
-   异步：批量数据或一些IO操作耗时的任务 例如:批量上传文件、发送电子邮件
-   削峰：高负载任务负载均衡 例：电商秒杀
-   解耦：串行任务并行化 例：退货流程解耦
-   广播：基于发布/订阅模型实现一对多通信


## 3.如何保证消息队列的高可用？
集群架构

## 4.如何保证消息不被重复消费？（如何保证消息消费的幂等性）
消息携带消息唯一的消息id，消费后的消息id记录起来

## 5.如何保证消息的可靠性传输？（如何处理消息丢失的问题）
-   生产端
    -   事务
    -   生产端开启发送消息confirm机制
    -   消息未路由到队列 ReturnListener 监听
    -   设置备份交换机 (创建交换机时设置 alternate-exchange 参数)
-   broker端
    -   持久化交换机
    -   持久化队列
    -   消息持久化
    -   broker 集群防止消息丢失
-   消费端
    -   消费完成后自动确认ack (拒绝后的消息 可重新入队或到达死信队列) 


## 6.如何保证消息的顺序性？

每个队列只有一个消费者，有顺序关联的key放到同一个Queue中

## 7.如何解决消息队列的延时以及过期失效问题？消息队列满了以后该怎么处理？有几百万消息持续积压几小时，说说怎么解决？

## 8.如果让你写一个消息队列，该如何进行架构设计啊？说一下你的思路。

## 9.RabbitMQ 有哪些类型的交换机
-   DirectExchange : 直连交换机 
-   TopicExchange : 主题交换机
-   FanoutExchange : 扇形交换机
-   HeaderExchange : 头交换机

## 10.这么自动删除没有消费者消费的消息
设置队列会消息的TTL时间

## 11.无法路由的消息去哪了
-   消息未路由到队列 ReturnListener 监听
-   设置备份交换机 (创建交换机时设置 alternate-exchange 参数)



## 12.可以使用消息优先级得到消费么
设置消息优先级

## 13.如何实现延时消息
-   安装延迟插件设置延迟时间
-   队列设置死信队列，消息设置过期时间

## 14.MQ这么实现RPC
两个队列一个放入请求信息，一个放入响应信息。通过消息唯一id确定是哪个客户端发送的消息

## 15. RabbitMQ 流量控制这么做？设置队列大小有用么？

## 16.一个队列多个消费端
-   轮训: 缺点 -> 部分消息消费时间过长 不同消费端性能不同 
-   公平分发



## 17.消息在什么时候回到达死信队列
死信队列
-   消息被拒绝 (消费端开启自动签收 拒绝签收)
-   消息TTL过期
-   队列达到最大长度
