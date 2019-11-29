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
         3. 将WebApplicationContext放入ServletContext（Java Web的全局变量）中,key为ROOT
* DispatcherServlet
    - init
        1. 创建XmlWebApplicationContext
        2. 初始化Web相关的组件
        3. 设置父容器为ROOT的WebApplicationContext
        4. 每个servlet可以有自己的XmlWebApplicationContext容器，彼此隔离，存在ServletContext的key为servlet名称
        
 * SpringBoot

##### 扩展接口


##### 参考文章
1. [Spring IOC 流程中核心扩展接口的12个扩展点源码分析](http://springcloud.cn/view/429)
2. [Spring的启动流程](https://www.jianshu.com/p/280c7e720d0c)
3. [浅谈ContextLoaderListener及其上下文与DispatcherServlet的区别](https://www.cnblogs.com/weknow619/p/6341395.html)