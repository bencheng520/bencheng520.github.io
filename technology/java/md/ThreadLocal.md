### ThreadLocal系列

* 结构
    - 每个线程都有一个自己的ThreadLocalMap
    - ThreadLocalMap的key为ThreadLocal对象，value为ThreadLocal的泛型类对象
    - key引用ThreadLocal为弱引用，value引用泛型类对象为强引用
* 内存回收和泄露
    - key为弱引用，当ThreadLocal使用完之后就被回收，map出现为null的key
    - value为强引用，线程不销毁不回收，所以线程池可能会出现内存泄露
    - 在ThreadLocalMap中，调用 set()、get()、remove()方法的时候，会清理掉key为null的记录
    
* 参考文章  
[平时常说的ThreadLocal，今天就彻底解决它](https://cloud.tencent.com/developer/article/1469598)

 
