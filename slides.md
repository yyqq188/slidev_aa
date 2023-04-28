---
layout: cover
background: '/picture/background.jpeg'
transition: slide-left
---

# Kafka的管理和监控
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
---

<v-clicks>

# 本地

![kafka shell 工具命令]('/picture/jietu1.png')

</v-clicks>

---
layout: cover
background: '/picture/background.jpeg'
---
# 本地
<v-clicks>

## 根据时间戳获得offset

### 工具一

```shell
./kafka-run-class.sh kafka.tools.GetOffsetShell 
--broker-list xx:9092,xx:9092,xx:9092 
--topic T_PREM_ARAP 
--time 1677686430000
```

### 工具二

![java工具]('/picture/jietu2.png')

</v-clicks>

