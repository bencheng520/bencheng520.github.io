### Proxy系列

##### 工具介绍
APT：编译前/编译后 修改字节码（lombok）
ASM：字节码改写
AspectJ：编译前/编译后/加载前 修改字节码（spring使用了aspectj语法格式）
LoadTimeWeaver(代码织入)：spring/aspectj都有各自的实现
Javassit：编译前/编译后/加载前/运行期（dubbo动态生成class字节码并加载）
JVM JVMTI：instrument（pinpoint）
jdk proxy：dubbo/spring/mybatis（InvocationHandler）
cglib：spring (底层利用了ASM改写字节码)（MethodInterceptor）

##### aop三剑客
- APT:APT(Annotation Processing Tool)即注解处理器，是一种处理注解的工具，确切的说它是javac的一个工具，它用来在编译时扫描和处理注解,代表框架为lombok
- aspectJ:AspectJ是一个面向切面的框架，它扩展了Java语言。AspectJ定义了AOP语法，所以它有一个专门的[编译器]用来生成遵守Java字节编码规范的Class文件。适合在某一个方法前后插入部分代码，处理某些逻辑：比如方法运行时间、插入动态权限检查等。问题会造成很多的冗余代码，产生很多代理类。简单来说就是在生成class时动态织入代码
- Javassit: Javassist是一个开源的分析、编辑和创建Java字节码的类库。是由东京工业大学的数学和计算机科学系的 Shigeru Chiba(千叶滋)所创建的。简单来说就是源码级别的api去修改字节码
##### 分类介绍
* 静态代理
    - java的wrapper设计模式相似，可以在开发编码的时候使用
* 动态代理
    - 动态字节码改写技术
    - 动态运行生成代理对象
    
##### 参考文章
+ [spring aspectj原理](https://blog.csdn.net/aizhupo1314/article/details/84989894)
* [spring LoadTimeWeaver(代码织入)](https://www.cnblogs.com/wade-luffy/p/6073702.html)
* [AspectJ LTW(Load Time Weaving)](https://www.iteye.com/blog/log-cd-562056)
+ [Spring的AspectJ工作原理分析](https://www.jianshu.com/p/307e0839b619)
+ [JDK和CGLIB动态代理区别](https://blog.csdn.net/yhl_jxy/article/details/80635012)
    - jdk需要生成被代理的对象
    - cglib可以不生产被代理的对象，直接返回被代理类的子类对象
    

 
