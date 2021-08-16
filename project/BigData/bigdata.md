### **皮皮的大数据笔记**

##### 目录

​	[Hadoop](./hadoop/hadoop.md)

​	[Spark](./spark/spark.md)



**Hadoop与Spark**

​	Hadoop是一个由Apache基金会所开发的分布式系统基础架构。用户可以在不了解分布式底层细节的情况下，开发分布式程序，充分利用了集群的威力进行高速运算和存储。

​	Hadoop实现了一个分布式系统（Hadoop Distributed File System ，*HDFS*）。*HDFS*有高容错性的特点，并且设计用来部署在低廉的（low-cost）硬件上；而且它提供高吞吐量（high throughput）来访问应用程序的数据，适合那些有着超大数据集（large data set）的应用程序。*HDFS*放宽了（relax）POSIX的要求，可以以流的形式访问（streaming access）文件系统中的数据。 

​	Hadoop的框架最核心的设计就是：***HDFS* 和 Map Reduce**。HDFS为海量的数据提供了存储，则MapReduce为海量的数据提供了计算。



​	Apache Spark 是专为大规模数据处理而设计的快速通用的计算引擎。Spark 是UC Berkeley AMP lab (加州大学伯克利分校的AMP实验室)所开源的类Hadoop MapReduce的通用并行框架，Spark 拥有Hadoop MapReduce所具有的优点；但不同于MapReduce的是——Job中间输出结果可以保存在内存中，从而不再需要读写HDFS，因此	Spark能更好地适用于数据挖掘与机器学习等需要迭代的 MapReduce 的算法。 
 Spark 在某些工作负载方面表现得更加优越，换句话说，Spark 启用了内存分布数据集，除了能够提供交互式查询外，它还可以优化迭代工作负载。 
​	Spark 是在 Scala 语言中实现的，它将 Scala 用作其应用程序框架。与 Hadoop 不同，Spark 和 Scala 能够紧密集成，其中的 Scala 可以像操作本地集合对象一样轻松地操作分布式数据集。 尽管创建 Spark 是为了支持分布式数据集上的迭代作业，但是实际上它是对 Hadoop 的补充，可以在 Hadoop 文件系统中并行运行。通过名为 Mesos 的第三方集群框架可以支持此行为。



区别：

1.数据的存储和处理
<u>hadoop</u>
	Hadoop实质上更多是一个分布式系统基础架构: 它将巨大的数据集分派到一个由普通计算机组成的集群中的多个节点进行存储，同时还会索引和跟踪这些数据，大幅度提升大数据处理和分析效率。Hadoop 可以独立完成数据的存储和处理工作，因为其除了提供HDFS分布式数据存储功能，还提供MapReduce数据处理功能。

<u>spark</u>
	Spark 是一个专门用来对那些分布式存储的大数据进行处理的工具，没有提供文件管理系统，自身不会进行数据的存储。它必须和其他的分布式文件系统进行集成才能运作。可以选择Hadoop的HDFS,也可以选择其他平台。

2.处理速度
<u>hadoop</u>

​	Hadoop是磁盘级计算，计算时需要在磁盘中读取数据；其采用的是MapReduce的逻辑，把数据进行切片计算用这种方式来处理大量的离线数据.

<u>spark</u>

​	Spark，它会在内存中以接近“实时”的时间完成所有的数据分析。Spark的批处理速度比MapReduce快近10倍，内存中的数据分析速度则快近100倍。比如实时的市场活动，在线产品推荐等需要对流数据进行分析场景就要使用Spark。

3.灾难恢复
<u>hadoop</u>

​	Hadoop将每次处理后的数据写入磁盘中，对应对系统错误具有天生优势。

<u>spark</u>

​	Spark的数据对象存储在弹性分布式数据集(RDD:)中。“这些数据对象既可放在内存，也可以放在磁盘，所以RDD也提供完整的灾难恢复功能。



参考文章：[Hadoop和Spark的区别](https://blog.csdn.net/u010899985/article/details/81503542)