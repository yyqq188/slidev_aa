---
layout: cover
background: '/picture/background.jpeg'
transition: slide-left
---

# Kafka的管理工具介绍
### 2023-04-28

---
src: 'pages/slides2.md'
---


---
src: 'pages/slides3.md'
---

---
src: 'pages/slides4.md'
---
















---
layout: cover
background: '/picture/background.jpeg'
transition: fade-out
---

<v-clicks>

# 本地

### ![Local Image](/picture/jietu1.png)

</v-clicks>

---
layout: cover
background: '/picture/background.jpeg'
transition: fade-out
---
# 根据时间戳获得offset

<v-clicks>

### 工具一

```shell
./kafka-run-class.sh kafka.tools.GetOffsetShell 
--broker-list xx:9092,xx:9092,xx:9092 
--topic T_PREM_ARAP 
--time 1677686430000
```

</v-clicks>


---
layout: cover
background: '/picture/background.jpeg'
transition: fade-out
---
# 根据时间戳获得offset

<v-clicks>

### 工具二

### ![Local Image](/picture/jietu3.png)


</v-clicks>


---
layout: cover
background: '/picture/background.jpeg'
transition: fade-out
---
# 根据时间戳获得offset

### 工具二

### ![Local Image](/picture/jietu4.png)


---
layout: cover
background: '/picture/background.jpeg'
transition: fade-out
---
# kafka生产环境消息转发

<v-clicks>

### 工具一

### ![Local Image](/picture/jietu5.png)


</v-clicks>
