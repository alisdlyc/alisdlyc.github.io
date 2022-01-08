---
title: Spark
date: 2021-12-27 12:25:33
tags: Spark
comments: false
---

# Spark



**官网**：https://spark.apache.org/

**文档**：https://spark.apache.org/docs/latest/

**UDF**：https://spark.apache.org/docs/3.2.0/sql-ref-functions-builtin.html#array-functions

### 一、用Scala和Spark进行数据分析

#### 1.1 采用与底层框架相同的编程语言的好处

+ 性能开销小
+ 能用上最新的版本和最好的性能
+ 有助于了解Spark的原理
+ 采用Scala可以完成数据处理的所有事情，不需要借助外界的数据库，也**不需要切换环境**

#### 1.2 Spark编程模型

+ 在输入数据集上定义一组转换
+ 调用action，可以将转换后的数据集保存在持久化存储上，或者将结果返回到驱动程序的本地内存
+ 运行本地计算，处理分布式计算的结果

#### 1.3 SQL vs DataFrane

在常用的列式存储中，SQL是读取和过滤存储最好的方式，SQL的缺点是很难用动态、可读和可测试的方式来表达复杂的多阶段分析。而这些都是DataFrame API的强项。

#### 1.4 DataFrame的转置和重塑

将宽表转换成长表，可以利用DataFrame的flatMap方法，它是RDD.flatMap方法的一个封装。

flatMap：接受一个函数作为参数，该函数处理一条输入记录，并返回一个包含你零条或者多条输出记录的序列。可以将flatMap看做map和filter转换函数的一般形式。即map是flatMap的一种特殊形式，一条输入记录仅产生一条输出记录。filter是flatMap的另一种特殊形式，即输入和输出类型相同，并且基于一个布尔函数决定或返回零条或一条记录。

#### 1.5 CaseClass

为了剥离出模型中Spark特定的组件，我们希望有一种创建简单记录类型的方法，从而可以将DataFrame中的字段视作静态类型的变量，而不用在Row中动态查找。我们可以通过Case Class的方式来创建这些记录，称为case类。case类是一个简单的不可变类，它默认实现了所有Java类的基本方法。

