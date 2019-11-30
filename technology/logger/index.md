### logging系列

##### mybatis
* 自定义日志接口Log
* 通过适配器模式定义各种日志框架的适配器Log接口实现
* 定义一个日志工厂类，根据classpath里找到的第一个日志框架封装到Log实现适配器里面
* [聊聊MyBatis的日志框架](https://www.jianshu.com/p/05b91c7205ff)