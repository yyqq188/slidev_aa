---
layout: cover
background: '/picture/background.jpeg'
transition: slide-left
---
# 消费者群组

<v-clicks>

- 列出并描述群组
- 删除群组
- 偏移量管理

</v-clicks>

---
layout: cover
background: '/picture/background.jpeg'
transition: fade-out
---
# 消费者群组
- ## <font color=DodgerBlue>列出并描述群组</font>
- 删除群组
- 偏移量管理


---
layout: cover
background: '/picture/background.jpeg'
transition: fade-out
---
# 列出并描述群组

<v-clicks>

##### 命令样例:

```shell
kafka-consumer-groups.sh --new-consumer 
--bootstrap-server test3.newchinalife.com:9092,test4.newchinalife.com:9092,test5.newchinalife.com:9092
--list
```

##### 群组详细信息命令样例:

```shell
kafka-consumer-groups.sh --new-consumer 
--bootstrap-server test3.newchinalife.com:9092,test4.newchinalife.com:9092,test5.newchinalife.com:9092
--describe --group test_group
```

</v-clicks>

<!--
对于任意列出的群组，使用--describe代替 --list，并通过--group指定特定的群组，就可以获得该群组的详细信息，
会列出群组里所有主题的信息和每个分区的偏移量
-->




---
layout: cover
background: '/picture/background.jpeg'
transition: fade-out
---
# 消费者群组
- 列出并描述群组
- ## <font color=DodgerBlue>删除群组</font>
- 偏移量管理


---
layout: cover
background: '/picture/background.jpeg'
transition: fade-out
---
# 删除群组

<v-clicks>

### 只有旧版的消费者客户端支持删除群组的操作

<br>

### 也不建议大家使用删除操作

</v-clicks>

<!--
注意 只有旧版才有这个操作
-->


---
layout: cover
background: '/picture/background.jpeg'
transition: fade-out
---
# 消费者群组
- 列出并描述群组
- 删除群组
- ## <font color=DodgerBlue>偏移量管理</font>


---
layout: cover
background: '/picture/background.jpeg'
transition: fade-out
---
# 偏移量管理

<v-clicks>

### 导出偏移量

<br>

```shell
kafka-run-class.sh kafka.tools.ExportZkOffsets 
--zkconnect test3.newchinalife.com:2181,test4.newchinalife.com:2181,test5.newchinalife.com:2181/kafka
--group test_group --output-file offsetFile.txt
```
<br>

### 导入偏移量

<br>

```shell
kafka-run-class.sh kafka.tools.ImportZkOffsets 
--zkconnect test3.newchinalife.com:2181,test4.newchinalife.com:2181,test5.newchinalife.com:2181/kafka
--group test_group --input-file offsetFile.txt
```

</v-clicks>


<!--
利用kafka-run-class.sh脚本调用底层的java类来实现导出。在导出偏移量时，会生成一个文件，文件里包含分区和偏移量的信息。
实际操作中，可以先导出文件，修改里面的偏移量后再执行导入偏移量文件的操作，但是在导入之前，必须先关闭所有的消费者。
-->