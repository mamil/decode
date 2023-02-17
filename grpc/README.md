# base
```
google.golang.org/grpc@v1.42.0
```
@v1.1.0

# 源码解析
简单看了一下，主要集中在自己实现的方法怎么让grpc调用这一段
调用 RegisterXXXServiceServer 之后，自己的实现就会被记录在serviceInfo 中
有消息进来的时候会进到 processUnaryRPC 这里，其中会接收消息，然后进行各种解析和调用。其中就有自己实现的调用。
最后会把结果返回。整个函数比较长，也比较复杂。


