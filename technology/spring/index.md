### spring系列

##### 技术点
* aop原理
* 事物实现

##### 启动初始化方式
* ContextLoaderListener
    - 实现ServletContextListener接口
    - 实现contextInitialized和contextDestroyed方法来初始化和销毁spring容器
* DispatcherServlet
    - 实现Servlet接口
    - 实现init方法初始化spring容器
* SpringBoot
    - SpringApplication.run
    - 获取应用类型webApplicationType：Standard/Web
    - 创建spring容器
    - 初始化装配容器
    - 参考文章：[Spring Boot深入原理 - SpringApplication启动原理](http://www.majunwei.com/view/201708231840127244.html)
    
##### 启动流程
* ContextLoaderListener
    - 
    - initWebApplicationContext
         1. 创建WebApplicationContext
         2. 加载对应的spring配置文件中的Bean
         3. 将WebApplicationContext放入ServletContext（Java Web的全局变量）中
* DispatcherServlet
    - init
        1. 

##### 扩展接口


##### 参考文章
1. [Spring IOC 流程中核心扩展接口的12个扩展点源码分析](http://starqiu.github.io/2019/02/18/%E4%BD%BF%E7%94%A8SparkSql%E5%88%86%E6%9E%90%E8%A1%A8/%E4%BD%BF%E7%94%A8SparkSql%E5%88%86%E6%9E%90%E8%A1%A8/)
2. [Spring的启动流程](https://www.jianshu.com/p/280c7e720d0c)
3. [浅谈ContextLoaderListener及其上下文与DispatcherServlet的区别](https://www.cnblogs.com/weknow619/p/6341395.html)