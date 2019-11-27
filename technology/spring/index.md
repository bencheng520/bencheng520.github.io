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