---
layout: two-cols
background: '/picture/background2.jpeg'
transition: fade-out
---


### 1. Parser
将 SQL/DataFrame/Dataset 转化成一棵未经解析（Unresolved）的树，在 Spark 中称为逻辑计划（Logical Plan），它是用户程序的一种抽象
### 2. Analyzer
利用Catalog中的信息,对Parser中生成的树进行解析.
Analyzer有一系列规则（Rule）组成,每个规则负责某项检查或者转换操作,如解析SQL中的表名 列名,同时判断它们是否存在.
通过Analyzer,我们可以得到解析后的逻辑计划.
### 3. Optimizer
对解析完的逻辑计划进行树结构的优化,以获得更高的执行效率.
优化过程也是通过一系列的规则来完成,常用的规则如谓词下推、列裁剪、连接重排序等.


<template v-slot:right>
<div style="display: flex;justify-content: center;align-items: center;margin-left: 10px">

![spark_sql2](/picture/spark_sql2.png)
</div>

<div style="margin-left: 10px">

### 4. Planner
将优化后的逻辑计划转化成物理执行计划（Physical Plan）.
由一系列的策略（Strategy）组成,每个策略将某个逻辑算子转化成对应的物理执行算子，并最终变成 RDD 的具体操作.
注意在转化过程中,一个逻辑算子可能对应多个物理算子的实现,
如 join 可以实现成 SortMergeJoin 或者 BroadcastHashJoin，这时候需要基于成本模型（Cost Model）来选择较优的算子

</div>



</template>

<!-- Catalyst 有以下几个重要的组成部分 -->


---
layout: two-cols
background: '/picture/background2.jpeg'
transition: fade-out
---

# FlinkSQL的Calcite


### <font color=#31655f>1. SQL解析阶段</font>
calcite parser 解析（sql -> AST，AST 即 SqlNode Tree）

### <font color=#31655f>2. SqlNode验证阶段</font>
calcite validator 校验（SqlNode -> SqlNode，语法、表达式、表信息）

### 3. 语义分析阶
SqlNode 转换为 RelNode，RelNode 即 Logical Plan（SqlNode -> RelNode）

### <font color=#31655f>4. 优化阶段</font>
calcite optimizer 优化（RelNode -> RelNode，剪枝、谓词下推等）


<template v-slot:right>

<div style="margin-left: 10px;margin-bottom: 107px">

![flinksql_project](/picture/flinksql_project.png)


</div>
<div style="margin-left: 10px">

### <font color=#31655f>5. 物理计划生成阶段</font>
Logical Plan 转换为 Physical Plan（等同于 RelNode 转换成 DataSet\DataStream API）
</div>

</template>


---
layout: two-cols
background: '/picture/background2.jpeg'
transition: fade-out
---
# calcite具有的功能

### 1. 自定义 sql 解析器
比如说我们自己制作一个引擎，然后我们要在这个引擎上来创造一套基于 sql 的接口，
那么我们就可以使用直接 calcite，不用自己去写一套专门的 sql 的解析器，以及执行以及优化引擎，calcite都具备
### 2. sql parser（extends SqlAbstractParserImpl
将 sql 的各种关系代数解析为具体的 AST，这些 AST 都能对应到具体的 java model，
在 java 的世界里面，对象很重要，有了这些对象（SqlSelect、SqlNode），
就可以根据这些对象做具体逻辑处理了。举个例子，
如下图，一条简单的 select c,d from source where a = '6' sql，
经过 calcite 的解析之后，就可以得到 AST model（SqlNode）。
可以看到有 SqlSelect、SqlIdentifier、SqlIdentifier、SqlCharStringLiteral。


<template v-slot:right>
<div style="margin-left: 10px">

![flinksql_calcite](/picture/flinksql_calcite.png)

### 3. sql validator（extends SqlValidatorImpl）
根据语法、表达式、表信息进行 SqlNode 正确性校验。
### 4. sql optimizer
剪枝、谓词下推等优化
</div>
</template>
