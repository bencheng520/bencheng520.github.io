# **_做一个有计划的人_**

### **技术栏目**

##### 业务

* [jvm](technology/jvm/index.md)
* [java](technology/java/index.md)
* [tomcat](technology/tomcat/index.md)
* [spring](technology/spring/index.md)
* [mybatis](technology/mybatis/index.md)
* [dubbo](technology/dubbo/index.md)  
* [logging](technology/logger/index.md)
* redis
    - [淘汰+内存原理](https://www.cnblogs.com/mengchunchen/p/10039467.html)
    - [Redis 单线程模型介绍](https://cloud.tencent.com/developer/article/1403767)
    - [Redis Cluster执行流程](https://blog.csdn.net/weixin_34452850/article/details/90442498)
    - [redis cluster客户端映射表/网络分区](https://blog.csdn.net/liuxiao723846/article/details/86715614)
    - [redis cluster/redis sharding/twemproxy](https://www.cnblogs.com/kuncy/p/9903482.html)
    - [redis cap理论](https://www.cnblogs.com/summer108/p/9783033.html)
* kafka(系统订阅发布系统)
    - [kafka0.9 自动提交rebalance](https://sq.163yun.com/blog/article/185482391401111552)
    - [kafka0.9 网络抖动leader选举脑裂](https://zhuanlan.zhihu.com/p/92934790)
    - [kafka producer consumer zookeeper 交互逻辑](https://blog.csdn.net/u010711294/article/details/82666564)
    - [kafka metadata源码](https://blog.csdn.net/weixin_34342578/article/details/91602189)
    - [kafka index log](https://my.oschina.net/anur/blog/2988177)
    - [kafka为什么快](https://www.jianshu.com/p/7309b6bcacf9)
        - 批量发送（同步异步）
        - 顺序读写（节省磁盘io）
        - [mmap内存映射的操作系统的page cache支持](https://www.jianshu.com/p/92f33aa0ff52)
        - 消费者获取消息通过page cache共享文件从sendfile内核到socket内核最终到网卡
        - topic多partition分区并行消费
        - 采用pull模式拉取消息，可以依据消费者性能来控制拉取消息量
        - [kafka中的ISR、AR又代表什么](https://blog.csdn.net/weixin_43975220/article/details/93190906)
     - kafka api版本
        - [新版 API](https://www.jianshu.com/p/9e17d64bd8c7)[kafka的group coordinator](https://www.jianshu.com/p/833b64e141f8)
        - [旧版高级 API](https://www.cnblogs.com/alexzhang92/p/10894800.html)
        - [旧版低级 API](https://www.cnblogs.com/alexzhang92/p/10894800.html)
     - [kafka streams](https://www.jianshu.com/p/bd90d815e48a)

##### 大数据

* [spark]()
    - [Spark任务提交流程](https://www.jianshu.com/p/a69656a244a8)
* [antlr4]()
* [分布式存储系统Kudu与HBase的简要分析与对比](https://blog.csdn.net/jessicaiu/article/details/82701415)


### **工作栏目**

* [系统安全](https://www.jianshu.com/p/65e1e6f8648e)
    - XSS跨站脚本攻击（通过Filter过滤基本的特殊字符）
    - CSRF跨站点请求伪造(三种解决策略：验证 HTTP Referer 字段；在请求地址中添加 token 并验证；在 HTTP 头中自定义属性并验证）
    - SQL注入攻击(参数化/防止动态sql拼接/加密重要数据)
    - TCP SYNC攻击
* [thrift基本原理及使用](https://blog.csdn.net/zkp_java/article/details/81879577)
* [事务原理](work/transaction/index.md)
* [业务架构](work/company/index.md)
* [链路追踪]()
* [熔断降级]()
* [领域驱动](work/domain/index.md)
* [网络协议(tcp/ip)](work/network/index.md)
* [并发/设计模式/volatile/ThreadLocal使用案例](work/demo/index.md)
* [线程状态和jstack日志分析](https://www.cnblogs.com/pc-boke/articles/9099029.html)
* [微服务](work/micro_service/index.md)
    - 入口流量拆分
    - 业务微服务拆分
    - 中间件拆分
    - 数据库拆分
    - 异地多活方案
* 队列
    - [消息队列面试题要点](https://www.cnblogs.com/peteremperor/p/10273077.html)
    - [RocketMQ架构解析](https://www.jianshu.com/p/015a16347640)
* [IO多路复用的三种机制Select，Poll，Epoll](https://www.jianshu.com/p/397449cadc9a)
    - [nginx面试题](https://blog.csdn.net/a303549861/article/details/88672901)
* [mysql索引]()
    - [关于mysql索引的B+树、聚簇索引、非聚簇索引、InnoDB、MyISAM之间的关系解析](https://blog.csdn.net/guanghuichenshao/article/details/81948438)

### **生活栏目**

### **面试栏目**
* 自我介绍
    - 优势：大流量项目开发/小型平台中台型项目开发
    - 切记：流水账
* 项目经验
    - 项目架构/自身定位/解决的问题
* 反问面试官原则
    - hr/初级面试官
        + 作为老员工对公司的感受/加入公司的理由
        - 表现一般，建议或评价/指点不足和未来发展
        - 岗位找人原因/回复时间等
    — 部门领导
        + 部门/组主要人员及对应的工作
        + 入职之后的工作要求和未来职位发展
        + 团队面临最大的问题和挑战
    - 老板或者大领导
        + 公司发展目标和理念
        + 公司目前最大的挑战

