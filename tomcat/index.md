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
* 启动流程
* 组件细节
* 流程处理

#### 经验系列
* 过滤器系列
* 配置项系列