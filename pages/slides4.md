---
layout: cover
background: '/picture/background.jpeg'
transition: fade-out
---

# kafka消费

<v-clicks>

### 控制台消费

```shell
kafka-console-consumer.sh --zookeeper {} --topic {}
```

```shell
kafka-console-consumer.sh 
--zookeeper test3.newchinalife.com:2181,test4.newchinalife.com:2181,test5.newchinalife.com:2181/kafka
--topic test_topic
```

### 补充参数
```text
--from-beginning       从最早的开始读取
--max-message {number} 最多读取的条数
--partition {number}   只读取指定分区的数据
```

### 读取偏移量主题数据


```shell
kafka-console-consumer.sh 
--zookeeper test3.newchinalife.com:2181,test4.newchinalife.com:2181,test5.newchinalife.com:2181/kafka
--topic __consumer_offsets 
--formatter 'kafka.coordinator.GroupMetadataManager$OffsetsMessageFormatter' 
--max-messages 1
```

</v-clicks>

<!--
平常最常用的命令
这里介绍一些补充的命令参数
以及关于偏移量主题消息的读取
为了解码这个主题的消息，用指定格式化器来处理消息

-->


---
layout: cover
background: '/picture/background.jpeg'
transition: fade-out
---

# kafka生产

<v-clicks>

### 生产者的命令

<br>

##### 命令格式:

```shell
kafka-console-product.sh --broker-list {} --topic {}
```

##### 命令样例:

```shell
kafka-console-product.sh 
--broker-list test3.newchinalife.com:9092,test4.newchinalife.com:9092,test5.newchinalife.com:9092
--topic test_topic
```

### 补充命令参数

```text
--key-serializer {classname}   默认是kafka.serializer.DefaultEncoder
--value-serializer {classname} 默认是kafka.serializer.DefaultEncoder
--compression-codec {name}     默认是gzip
```

</v-clicks>

<!--
这也是我们在平常工作中常用的命令

-->

