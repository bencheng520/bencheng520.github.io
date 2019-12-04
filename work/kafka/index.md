### kafka

##### 为啥快

- reactor线程模型，读写业务线程分离（select/poll）
- 顺序读写磁盘（寻址很耗费时间）
- 生产者批量生产发送
- topic分partition，消费者并行消费
- 底层零拷贝（buffer拷贝/buffer合并/文件sendfile）
- 时间轮延迟操作处理流程[Kafka科普系列 | 轻松理解Kafka中的延时操作](https://blog.csdn.net/u013256816/article/details/89325701)







    
    

        
        