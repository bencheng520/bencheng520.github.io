


### dubbo 异步

##### 重点文章
- [Dubbo源码分析----DefaultFuture](https://blog.csdn.net/u013160932/article/details/81155265)
- [Condition接口原理与应用](https://www.jianshu.com/p/c7af7f3fa135)

- future、request、response公用同一个id标识
- RpcContext.getContext().setFuture(future)将异步请求放到RpcContext里面
- DefaultFuture.FUTURES静态Map<Long, DefaultFuture>变量,响应通过id标识可以找到对应的request
- DefaultFuture.RemotingInvocationTimeoutScan是一个Daemon线程，30毫秒扫描一次所有的request future，有过期就抛出TimeoutException异常
- 消费方通过RpcContext.getContext().getFuture()获得request future来异步获取内容