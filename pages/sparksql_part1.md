---
layout: cover
background: '/picture/background2.jpeg'
transition: fade-out
---

# 为什么使用SQL

<v-clicks>

## 1. SQL是事实上的数据处理标准

<br>

<div style="display: flex;justify-content: center;align-items: center">

```shell
MR -> java  spark-> java scale python
```

</div>


<br>

### hive
### impala 
### presto
### phoenix
### clickhouse

<br>

## 2. SQL的受众面广,容易上手,易学易用

</v-clicks>

<!--

在传统的RDBMS系统中,sql是标准的数据处理语言
但是在大数据领域 不同的数据引擎导致需要用到不同的编程语言
例如MR -> java ,spark-> java scale python
不能做到统一的处理
为了迎合这种需求,大数据的各条技术栈,都在或多或少地往SQL方向靠拢
hive impala presto phoenix clickhouse

-->


---
layout: cover
background: '/picture/background2.jpeg'
transition: fade-out
---

# Spark SQL是什么

<v-clicks>

<div style="display: flex;justify-content: center;align-items: center;font-size: 25px">

Spark SQL is Apache Spark's module for working with structured data.

</div>

</v-clicks>

---
layout: two-cols
background: '/picture/background2.jpeg'
transition: fade-out
---

# Spark SQL有哪些特性
<v-clicks>

## 1. <font color=#f6ecd2>集成</font>

Spark SQL允许使用SQL或熟悉的DataFrameAPI查询Spark程序中的结构化数据.可用于Java、Scala、Python和R

## 2. <font color=#f6ecd2>数据访问的统一</font>

DataFrames和SQL提供了访问各种数据源的通用方式
<div style="display: flex;justify-content: center;align-items: center">

```java
spark.read.format('json').load(path)
spark.read.format('text').load(path)
spark.read.format('parquet').load(path)
```

</div>


## 3. <font color=#f6ecd2>兼容hive</font>

Spark SQL支持HiveQL语法和UDF，允许您访问现有的Hive仓库

这样如果是想把hive的作业迁移到sparksql中的话,迁移的成本会低很多.

</v-clicks>

<template v-slot:right style="background-size: cover;background-attachment: fixed;">

![Local Image](/picture/phone.jpeg)

</template>


---
layout: two-cols
background: '/picture/background2.jpeg'
transition: fade-out
---

# sparksql的架构介绍 🚀

- <font color=#f6ecd2>Frontend</font>
  - hive AST,sql语句(字符串) --> 抽象语法树
  - spark program:DataFrame/DataSet API
  - streaming sql
- <font color=#f6ecd2>catalyst</font>
  - unresolved logic plan
  - schema catalog 需要和metastore进行结合 --> logic plan
  - optimized logicPlan
  (ps:select * from (select * from limit 10) limit 5;)
  - physical plan
- <font color=#f6ecd2>Backend</font>
  - 这一层主要由SparkCore层提供支持.包括Spark集群管理器、Task调度器、缓存管理器和存储系统等


<template v-slot:right style="background-size: cover;background-attachment: fixed;">

![image.png](/picture/sparksql_construct.png)

</template>

<!-- 最后需要加上注释 -->


