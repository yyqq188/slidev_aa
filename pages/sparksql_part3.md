---
layout: cover
background: '/picture/background2.jpeg'
transition: fade-out
---

# Dataframe&Dataset

<div style="display: flex;justify-content: center;align-items: center">
<v-clicks>

## <font color=#c7ccbd>Dataframe是以列名组织的数据集,是特殊的Dataset,类型表示为Dataset\<Row\></font>

## <font color=#f6ecd2>Dataset是强类型的数据集,需要指定类型,类型表示为Dataset\<R\></font>

</v-clicks>
</div>



---
layout: two-cols
background: '/picture/background2.jpeg'
transition: fade-out
---


<template v-slot:default>
<v-clicks>

## 以字符串指定列名

<div  style="margin-top: 10px ;padding-top: 10px;padding-left: 0;padding-right: 10px">

```shell
df.select("name").show()

df.groupBy("age").count().show()

```
</div>
</v-clicks>
</template>

<template v-slot:right>
<v-clicks>

## 以属性引用的方式,可参与计算

<div  style="margin-top: 10px ;padding-top: 10px;padding-right: 10px;padding-left: 0">

```shell
df.select($"name", $"age" + 1).show()

df.filter($"age" > 21).show()
```
</div>
</v-clicks>
</template>


---
layout: cover
background: '/picture/background2.jpeg'
transition: fade-out
---

# 通过反射创建Dataframe

<div style="display: flex;justify-content: center;align-items: center">

```java
SparkSession spark = SparkSession.builder().master("").appName("demo").getOrCreate();
JavaRDD<String> sourceRDD = spark.read().textFile("file://demo/demo.txt").javaRDD();
JavaRDD<Person> personRDD = sourceRDD.map(line -> line.split(","))
        .map(x -> {
            Person person = new Person();
            person.setName(x[0]);
            person.setAge(Integer.valueOf(x[1]));
            return person;
        });
Dataset<Row> personDF = spark.createDataFrame(personRDD, Person.class);✅
personDF.createOrReplaceTempView("person");
Dataset<Row> resultDF = spark.sql("select * from person");
resultDF.show();
spark.close();
//-----------
@Data
@AllArgsConstructor
@NoArgsConstructor
private static class Person{
    String name;
    Integer age;
}
```

</div>



---
layout: cover
background: '/picture/background2.jpeg'
transition: fade-out
---

# 通过schema创建Dataframe

<div style="display: flex;justify-content: center;align-items: center">

```java
SparkSession spark = SparkSession.builder().master("").appName("demo").getOrCreate();
JavaRDD<String> peopleRDD = spark.sparkContext()
        .textFile("examples/src/main/resources/people.txt", 1)
        .toJavaRDD();
String schemaString = "name age";
List<StructField> fields = new ArrayList<>();
for (String fieldName : schemaString.split(" ")) {
    StructField field = DataTypes.createStructField(fieldName, DataTypes.StringType, true);
    fields.add(field);
}
StructType schema = DataTypes.createStructType(fields);
JavaRDD<Row> rowRDD = peopleRDD.map(record -> {
    String[] attributes = record.split(",");
    return RowFactory.create(attributes[0], attributes[1].trim());
});
Dataset<Row> peopleDataFrame = spark.createDataFrame(rowRDD, schema);✅
peopleDataFrame.createOrReplaceTempView("people");
Dataset<Row> resultsDF = spark.sql("SELECT name FROM people");
resultsDF.show();
```
</div>
