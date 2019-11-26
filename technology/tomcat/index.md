### tomcat系列

#### 总述
* Tomcat的核心分为3个部分:
1. Web容器---处理静态页面；
2. catalina --- 一个servlet容器-----处理servlet;
3. 还有就是JSP容器，它就是把jsp页面翻译成一般的servlet。

* 备注：  
catalina 就是Tomcat服务器使用的 Apache实现的servlet容器的 名字。Catalina是美国西海岸靠近洛杉矶22英里的一个小岛，因为其风景秀丽而著名。Servlet运行模块的最早开发者Craig McClanahan因为喜欢Catalina岛故以Catalina命名他所开这个模块，尽管他从来也没有去过那里。    

#### 源码系列
* [架构简介](md/架构简介.md)
* [流程处理](md/流程处理.md)

#### 经验系列
* 过滤器系列
    - Filter是Servlet定义的规范接口，所以初始化操作是由，springboot内嵌的tomcat9是通过StandardContext组件的filterStart调用的
    - 通过Tomcat的StandardContext.filterStart可以知道servlet容器所有的一级Filter列表和顺序
    - 在一级Filter里面可以定义自己的Filter链表来实现业务逻辑，例如Shiro等（自定义Filter容器不一定要实现servlet Filter接口）
* 多tomcat实例共享源码
    - CATALINA_HOME是Tomcat的安装目录
    - CATALINA_BASE是Tomcat的工作目录
    - [Tomcat解惑 之 CATALINA_HOME与CATALINA_BASE](https://blog.csdn.net/jiaotuwoaini/article/details/51455829)
* 配置项系列
    - CatalinaProperties：巧妙的配置属性获取
    
* 调优系列
    - 主要参数设置
        - fs.file-max：tcp打开的系统文件描述符，默认1024（r2s配置6553600）
        - acceptCount：acceptor队列的大小，默认100（r2s配置500）
        - maxConnections：处理的最大连接数（socket打开的数量），nio默认10000
        - maxThreads：work线程数，默认200（r2s配置3000）
        - Connector运行模式
        - jvm内存调优
    - [基本参数调优配置](https://blog.csdn.net/fangquan1980/article/details/88653840)
    - [详解tomcat的连接数与线程池](https://www.cnblogs.com/kismetv/p/7806063.html)