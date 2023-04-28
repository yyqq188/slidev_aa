---
layout: cover
background: '/picture/background.jpeg'
transition: fade-out
---
# 主题操作


<v-clicks>

- 创建主题
- 增加分区
- 删除主题 
- 列出集群里的所有主题
- 列出主题的详细信息

</v-clicks>

---
layout: cover
background: '/picture/background.jpeg'
transition: fade-out
---
# 主题操作
- ## <font color=DodgerBlue>创建主题</font>
- 增加分区
- 删除主题
- 列出集群里的所有主题
- 列出主题的详细信息


---
layout: cover
background: '/picture/background.jpeg'
transition: fade-out
---
# 创建主题

<v-clicks>

##### 命令格式:

```shell
kafka-topics.sh --zookeeper {} --create --topic {} --replication-factor {} --partitions {}
```

##### 命令样例:
##### ip: 测试217节点  path:home/simp_admin/bgtm/kafka_metrics/kafkabin

```shell
export KAFKA_OPTS="-Djava.security.krb5.conf=/home/simp_admin/shell/conf/krb5.conf 
-Djava.security.auth.login.config=/home/simp_admin/shell/conf/jaas.conf"

./kafka-topics.sh --zookeeper test3.newchinalife.com:2181,test4.newchinalife.com:2181,test5.newchinalife.com:2181/kafka
 --create --topic test_topic --replication-factor 2 --partitions 3
```

</v-clicks>



<!-- 创建主题有三个参数需要指定：
主题名字
复制系数
分区数

命令样例是我们集群中可用的命令
-->

---
layout: cover
background: '/picture/background.jpeg'
transition: fade-out
---
# 主题操作
- 创建主题
- ## <font color=DodgerBlue>增加分区</font>
- 删除主题
- 列出集群里的所有主题
- 列出主题的详细信息


---
layout: cover
background: '/picture/background.jpeg'
transition: fade-out
---

# 增加分区

<v-clicks>

##### 关键参数:
```shell
-- alter
```

##### 命令格式:
```shell
kafka-topics.sh --zookeeper {} --alter --topic {} --partitions {}
```

##### 命令样例:

```shell
kafka-topics.sh 
--zookeeper test3.newchinalife.com:2181,test4.newchinalife.com:2181,test5.newchinalife.com:2181/kafka 
--alter --topic test_topic --partitions 5
```

</v-clicks>

<!-- 创建主题有三个参数需要指定：
有时候 我们需要增加分区的数量，增加分区主要是为了扩展主题的容量或者
降低单个分区的吞吐量
--alter

由当前添加到16个分区
-->

---
layout: cover
background: '/picture/background.jpeg'
transition: fade-out
---
# 主题操作
- 创建主题
- 增加分区
- ## <font color=DodgerBlue>删除主题</font>
- 列出集群里的所有主题
- 列出主题的详细信息

---
layout: cover
background: '/picture/background.jpeg'
transition: fade-out
---
# 删除主题

<v-clicks>

##### broker的`delete.topic.enable`参数必须被设置为`true`
<br>

##### 命令格式:

```shell
kafka-topics.sh --zookeeper {}  --delete --topic {}
```

##### 命令样例:

```shell
kafka-topics.sh 
--zookeeper test3.newchinalife.com:2181,test4.newchinalife.com:2181,test5.newchinalife.com:2181/kafka 
--delete --topic test_topic
```

</v-clicks>



<!--
如果一个主题不再使用了，只要它还存在于集群里，就会占用一定数量的磁盘空间和，把它删除就可以释放占用的资源，为了能够
删除主题，broker的delete.topic.enable参数必须被设置为true,否则删除主题的命令会被忽略

-->

---
layout: cover
background: '/picture/background.jpeg'
transition: fade-out
---
# 主题操作
- 创建主题
- 增加分区
- 删除主题
- ## <font color=DodgerBlue>列出集群里的所有主题</font>
- 列出主题的详细信息

---
layout: cover
background: '/picture/background.jpeg'
transition: fade-out
---

# 列出集群里的所有主题

<v-clicks>

##### 命令格式:

```shell
kafka-topics.sh --zookeeper {} --list
```

##### 命令样例:

```shell
kafka-topics.sh --zookeeper test3.newchinalife.com:2181,test4.newchinalife.com:2181,test5.newchinalife.com:2181/kafka 
--list
```

</v-clicks>



<!--
简单且常用的命令，列出kafka集群中的所有主题
-->

---
layout: cover
background: '/picture/background.jpeg'
transition: fade-out
---
# 主题操作
- 创建主题
- 增加分区
- 删除主题
- 列出集群里的所有主题
- ## <font color=DodgerBlue>列出主题的详细信息</font>


---
layout: cover
background: '/picture/background.jpeg'
transition: fade-out
---

# 列出主题的详细信息

<v-clicks>

##### 命令格式:

```shell
kafka-topics.sh --zookeeper {}  --topic {} --describe
```

##### 命令样例:

```shell
kafka-topics.sh --zookeeper test3.newchinalife.com:2181,test4.newchinalife.com:2181,test5.newchinalife.com:2181/kafka
 --topic test_topic --describe
```

</v-clicks>

<!-- 
主题工具可以获得主题的详细信息，
信息里包含分区数量以及每个分区的副本清单
-->