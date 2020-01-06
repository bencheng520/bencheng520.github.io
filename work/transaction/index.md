### 事务系列

#### 核心文章[关于分布式事务，XA协议的学习笔记](https://www.cnblogs.com/monkeyblog/p/10449363.html)

* Transaction不是JDK接口，特别注意
* 目前JTA的实现主要有以下几种：
    - J2EE容器所提供的JTA实现(如JBoss)
    - 独立的JTA实现：如JOTM（Java Open Transaction Manager），Atomikos。这些实现可以应用在那些不使用J2EE应用服务器的环境里用以提供分布事事务保证
* 分布式事务的实现方式
    - 2pc（强一致性）[理解数据库中的undo日志、redo日志、检查点](https://www.cnblogs.com/l1pe1/p/8327849.html)
    - 3pc
    - tcc（最终一致性）
    - 本地消息表（最终一致性）
    - MQ队列（最终一致性）
    - Saga（最终一致性）

##### 事务特性（ACID）
- 原子性（atomicity）：事务是数据库的逻辑工作单位，而且是必须是原子工作单位，对于其数据修改，要么全部执行，要么全部不执行
- 一致性（consistency）：事务在完成时，必须是所有的数据都保持一致状态。在相关数据库中，所有规则都必须应用于事务的修改，以保持所有数据的完整性
- 隔离性（isolation）：一个事务的执行不能被其他事务所影响
- 持久性（durability）：一个事务一旦提交，事物的操作便永久性的保存在DB中。即便是在数据库系统遇到故障的情况下也不会丢失提交事务的操作

##### 功能分类
* 本地事务（jdbc事务）
* 分布式事务
    - jta标准（XA）事务：通过ThreadLocal携带Transaction将多个支持XA协议的XAResource加入Transaction
    - sharding-jdbc 柔性事务：通过事务表加定时任务（elastic-job）实现最终事务一致性
    - mycat：重写mysql协议，伪装成mysql server实现分布式事务
    
##### 使用分类
* web服务器提供的jndi功能

* 直接通过jar引入支持分布式组件


##### 文章要点
[Redlock：Redis分布式锁最牛逼的实现](https://www.jianshu.com/p/7e47a4503b87)  
[Sharding-JDBC与MyCat选型区别](https://www.jianshu.com/p/fdbaa2b6ba8d)  
[Spring通过atomikos实现JTA分布式事务](https://blog.csdn.net/weihao_/article/details/72782569)  
[Tomcat JNDI通过Atomikos 实现JTA](https://blog.csdn.net/xuyu_yt/article/details/77905553)  
[Sharding-JDBC柔性事务（最大努力型）原理](https://blog.csdn.net/weixin_34055787/article/details/91917214)  
[XA协议JPA的实现原理（ThreadLocal）](https://my.oschina.net/xianggao/blog/548493)  
[不同的事务管理器说明3篇](https://www.jianshu.com/p/3938e7172443)  
[MySQL XA 介绍](https://www.jianshu.com/p/7003d58ea182)  
[mysql对XA协议的支持](https://www.cnblogs.com/dennyzhangdd/p/10975192.html)  
[atomikos JTA/XA全局事务](https://www.jianshu.com/p/842acb795e05)  
[XA事务的隔离级别算什么级别(serializable)](https://www.zhihu.com/question/58308824)  

    
    

        
        
