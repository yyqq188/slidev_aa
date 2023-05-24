---
layout: cover
background: '/picture/background2.jpeg'
transition: fade-out
---

# 配置json文件

```json {3-12}
{
  "job": {
    "spark": {
      "appName": "kafka-sandbox",
      "master": "yarn",
      "seconds": 3,
      "logLevel": "ERROR",
      "parameter": {
        "spark.streaming.kafka.maxRatePerPartition": "100",
        "spark.dynamicAllocation.enabled": "false",
        "spark.streaming.backpressure.enabled": "false"
      }
    },
    "parser": {
      "name": "t_PERM_ARAP",
      "parameter": {
        "pojoClassPath": "com.yhl.entity.source.T_PERM_ARAP_SOURCE"
      }
    },
```

---
layout: cover
background: '/picture/background2.jpeg'
transition: fade-out
---

# 配置json文件

```json {14-17}
{
  "job": {
    "spark": {
      "appName": "kafka-sandbox",
      "master": "yarn",
      "seconds": 3,
      "logLevel": "ERROR",
      "parameter": {
        "spark.streaming.kafka.maxRatePerPartition": "100",
        "spark.dynamicAllocation.enabled": "false",
        "spark.streaming.backpressure.enabled": "false"
      }
    },
    "parser": {
      "name": "t_PERM_ARAP",
      "parameter": {
        "pojoClassPath": "com.yhl.entity.source.T_PERM_ARAP_SOURCE"
      }
    },
```

---
layout: cover
background: '/picture/background2.jpeg'
transition: fade-out
---

# 配置json文件

```json {1-9}
"reader": {
        "name": "kafkaRowReader",
        "topic": ["T_PREM_ARAP"],
        "parameter": {
          "bootstrap.servers": "nod1.newchinalife.com:9092,nod3.newchinalife.com:9092,nod4.newchinalife.com:9092",
          "group.id": "aaa",
          "auto.offset.reset": "earliest",
          "enable.auto.commit": false
        }
      },
      "transformer": [
        {
          "name": "join",
          "parameter": {
            "tableName":"NCI_HBASE_CAP:T_PREM_ARAP",
            "family": "cf1",
            "joinColumns": ["LIST_ID"],
            "joinDelimiter":"_",
            "joinColumnsHash": "hash",
            "ddl" : "BUSI_PROD_CODE string,BUSI_PROD_NAME string,DERIV_TYPE string"
          }
        },
```

---
layout: cover
background: '/picture/background2.jpeg'
transition: fade-out
---

# 配置json文件

```json {11-20}
"reader": {
        "name": "kafkaRowReader",
        "topic": ["T_PREM_ARAP"],
        "parameter": {
          "bootstrap.servers": "nod1.newchinalife.com:9092,nod3.newchinalife.com:9092,nod4.newchinalife.com:9092",
          "group.id": "aaa",
          "auto.offset.reset": "earliest",
          "enable.auto.commit": false
        }
      },
      "transformer": [
        {
          "name": "join",
          "parameter": {
            "tableName":"NCI_HBASE_CAP:T_PREM_ARAP",
            "family": "cf1",
            "joinColumns": ["LIST_ID"],
            "joinDelimiter":"_",
            "joinColumnsHash": "hash",
            "ddl" : "BUSI_PROD_CODE string,BUSI_PROD_NAME string,DERIV_TYPE string"
          }
        },
```

---
layout: cover
background: '/picture/background2.jpeg'
transition: fade-out
---

# 配置json文件

<div style="display: flex;justify-content: center;align-items: center">

```json {1-14}
        "writer": {
          "name": "hbaseWriter",
          "tableName": "test_yhl",
          "family": "cf1",
          "rowkey": "BUSI_PROD_CODE",
          "columns": ["BUSI_PROD_NAME","DERIV_TYPE"],
          "parameter": {
            "hbase.zookeeper.quorum": "nod2.newchinalife.com,nod4.newchinalife.com,nod5.newchinalife.com",
            "hbase.zookeeper.property.clientPort": "2181",
            "hbase.rpc.timeout": "1200000",
            "hbase.client.operation.timeout": "960000",
            "hbase.client.retries.number": "10",
            "hbase.client.pause": "120000",
            "hbase.client.scanner.timeout.period": "200000"
          }
        }
  }
}
```
</div>


---
layout: cover
background: '/picture/background2.jpeg'
transition: fade-out
---

## 1. maven命令jar导入到本地库

```shell
mvn install:install-file -Dfile=/Users/yanghualei/
datax_spark_module-1.0-SNAPSHOT-jar-with-dependencies.jar 
-DgroupId=org.example 
-DartifactId=datax_spark_module 
-Dversion=1.0-SNAPSHOT 
-Dpackaging=jar
```

## 2. 创建项目并添加依赖
```xml
<dependencies>
    <dependency>
        <groupId>org.example</groupId>
        <artifactId>datax_spark_module</artifactId>
        <version>1.0-SNAPSHOT</version>
    </dependency>
</dependencies>
```


---
layout: cover
background: '/picture/background2.jpeg'
transition: fade-out
---

## 3. 创建入口类继承DataxSparkMainV8
##   在resource下创建json配置文件
##   并在入口类中指定json配置文件

<div style="display: flex;justify-content: center;align-items: center">

```java
public class DemoMain extends DataxSparkMainV8{
    public static void main(String[] args) throws Exception {
        String jsonPath = "demo.json";
        run(jsonPath);
    }
}
```
</div>


---
layout: cover
background: '/picture/background2.jpeg'
transition: fade-out
---

## 4. 按照约定的package名称创建job的组件

<div style="display: flex;justify-content: center;align-items: center;margin-top: 20px">

![packagename](/picture/packagename.png)
</div>


---
layout: cover
background: '/picture/background2.jpeg'
transition: fade-out
---

## 以上配置就算完成基本的job配置,可以打包运行
<br>

## 如果有自定义的逻辑,需要继承各自的抽象类...
<br>

<div style="display: flex;justify-content: flex-start;flex-direction: column">

## <font color=#369d82>AbstractParser</font>
## <font color=#369d82>AbstractReader</font>
## <font color=#369d82>AbstractTransform</font>
## <font color=#369d82>AbstractWriter</font>

</div>
