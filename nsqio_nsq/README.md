# base
```
git@github.com:nsqio/nsq.git
```
@v1.1.0

# 源码解析
基本的逻辑比较简单易懂，主要分成生产者和消费者，中间做了一个delegates，统一了连接回调的接口。

- producer.go 用于生产者相关的操作
  - 连接之后会在conn里面开启读写2个协程
  - Producer里面开一个路由协程，处理读写协程过来的数据，这之间通过chan收发消息

- consumer.go 用于消费者相关的操作
  - handlerLoop 用于处理注册的消息回调函数，每种消息的回调可以指定 handlerLoop的数量

- conn.go 这里用于收发消息
  - 在delegates.go里面定义了delegates接口，统一了生产者和消费者的回调接口