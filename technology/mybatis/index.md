### mybatis系列

##### 四大对象和插件原理
* 四大对象
    - ParameterHandler：处理SQL的参数对象
    - ResultSetHandler：处理SQL的返回结果集
    - StatementHandler：数据库的处理对象，用于执行SQL语句
    - Executor：MyBatis的执行器，用于执行增删改查操作
* 插件原理
    1. Mybatis的插件借助于责任链的模式进行对拦截的处理
    2. 使用动态代理对目标对象进行包装，达到拦截的目的
    3. 作用于Mybatis的作用域对象之上

##### 初始化
* 核心对象
    - SqlSessionFactoryBuilder
        * SqlSessionFactory构造类
        * XMLConfigBuilder解析原生的xml配置
        * 解析事物管理器：JdbcTransaction、ManagedTransaction、SpringManagedTransaction
            - 根据不同的配置累心获得不同的事物：\<transactionManager type="JDBC"\>\</transactionManager\>
            - 事物里面持有初始化后的connection和datasource
        * 解析xml的时候解析plugins（interceptor）、mappers
        * 解析plugins（interceptor）放到Configuration的chain里面
        * 解析mapper的时候将sql语句解析成MappedStatement对象，加载mapper interface到Configuration中
    - SqlSessionFactory
        * SqlSession工厂类
        * 创建Executor对象，使用interceptor包装interceptorChain.pluginAll(executor)
        * Executor有SIMPLE, REUSE, BATCH,区别是否重用Statement或者批量提交
        * SqlSession持有Executor引用，Executor是最终的sql执行器
    - SqlSession：sql执行的封装类
        * 执行SqlSession.selectOne等方法，创建ResultHandler
        * 找到执行的对应的MappedStatement
        * 调用Executor执行对应的MappedStatement
            - 从Transaction接口中获得connection（Transaction会判断是否是datasource还是直连的connection）
            - 创建StatementHandler，持有ResultSetHandler，ParameterHandler
            - handler传参数执行对应的MappedStatement
    - mapper代理对象
        * 调用session.getMapper获取mapper接口代理对象
        * 通过MapperProxyFactory获得mapper的代理实现MapperProxy
        * MapperProxy下线了InvocationHandler接口，实际上就是jdk动态代理，持有SqlSession对象
* 插件源码逻辑
    - Executor获得StatementHandler会调用newStatementHandler
    - newStatementHandler通过interceptorChain.pluginAll(statementHandler)应用插件
    - 插件对象Plugin实现jdk的InvocationHandler接口，jdk动态代理对象成功应用插件
* 事物的实现
    - \<transactionManager type="JDBC"/\>
    - type可以取值为：JDBC、MANAGED
        * JDBC ：这个配置就是直接使用了 JDBC 的提交和回滚设置，它依赖于从数据源得到的连接来管理事务作用域。即利用java.sql.Connection对象完成对事务的提交（commit()）、回滚（rollback()）、关闭（close()）等
        * MANAGED  ： 这个配置几乎没做什么。它从来不提交或回滚一个连接，而是让容器来管理事务的整个生命周期（比如 JEE 应用服务器的上下文）
    - SpringManagedTransaction是mybatis-spring jar包中代替mybatis的JdbcTransaction的，让SqlSession从spring的ThreadLocal中获取jdbc connection   
* 缓存的实现
    - 一级缓存
        * 同一个 SqlSession 对象， 在参数和 SQL 完全一样的情况先， 只执行一次 SQL 语句（如果缓存没有过期）
        * 不同的 SqlSession 之间的缓存是相互隔离的
        * 自动开启、不能关闭、但是可以手动开启
        * Executor组件中实现该缓存
    - 二级缓存
        * 存在与Mapper实例中，当多个SqlSession类的实例对象共享
        * 增，删，改，等改变数据的操作时，Mapper实例都会清空其二级缓存
    - 参考文章：[mybatis的缓存机制](https://blog.csdn.net/qq_38263083/article/details/82716702)

##### 使用方式
* 原生非mapper
    User user = session.selectOne("org.fkjava.mybatis.domain.UserMapper.findById", 2);
* 原生mapper
    UserMapper mapper = session.getMapper(UserMapper.class);
* 集成spring
    - SqlSessionFactoryBean实现InitializingBean初始化配置信息、实现FactoryBean<SqlSessionFactory>托管给Spring容器
    - MapperScannerConfigurer实现BeanDefinitionRegistryPostProcessor扫描mapper包、接口、注解等，实现InitializingBean判断basePackage参数不为空
    - SqlSessionTemplate增强Mybatis的SqlSession功能
    - MapperFactoryBean替代SqlSession#getMapper()获得Mapper实例
* 集成springboot
    - MybatisAutoConfiguration自动注解功能
    - @MapperScan扫描装配mapper对象
* 集成mybatis-plus
    - 自定义注解
    - 简化接口调用
    - 支持代码生产
    - 支持自动化生产代码等
    - 多数据源支持
    - 更多请看官网和[mybatis-plus思维导图，让mybatis-plus不再难懂](https://www.jianshu.com/p/df543044e8e2)
    
##### 分页插件PageHelper
* 将分页信息放入ThreadLocal
* 拦截Executor改写执行参数（根据不同的数据库追加limit语法）
* 参考文章：[PageHelper原理](https://www.cnblogs.com/dengpengbo/p/10579631.html)
##### 分库分表组件集成
* shardbatis（客户端）
    - 通过plugin插件的形式实现
    - 只支持分表逻辑
* sharding-jdbc（客户端）
    - 封装DataSource对象，进行功能扩展
    - 获得执行sql之后解析、改写（读取配置文件）、路由、执行、结果归并
    - 柔性事务：最大努力送达SoftTransactionManager
* mycat
    - 服务端分库分表
    - 支持sort、order...
    - 分布式事物2pc，参考：[Mycat分布式事务两阶段提交过程概述](http://blog.itpub.net/15498/viewspace-2137419/)
        + 第一阶段：准备prepare，mysql记录事物日志，方便后续回滚
        + 第二阶段：提交commit，时间很短暂
* 参考文章：[Mycat原理解析-Mycat架构分析](https://blog.csdn.net/u011983531/article/details/78948680)

##### 参考文章
[Mybatis运行原理及源码解析](https://blog.csdn.net/lchpersonal521/article/details/84451357)
[MyBatis plugin的使用与源码解析](https://blog.csdn.net/u012734441/article/details/85833430)
[MyBatis对事务的处理过程分析](https://blog.csdn.net/qq_18860653/article/details/80680748)
[Spring事务流程解析](https://blog.csdn.net/qq_18860653/article/details/80049281)