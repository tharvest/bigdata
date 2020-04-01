![](./img/hbase_logo_with_orca_large.png)
### HBASE架构分析

hbase在架构上有三种服务组件组成：Zookeeper，Master Server，Region Server
![](../hadoop/img/hbase-arch.jpg)
- Zookeeper。Zookeeper的主要作用是监测集群中节点的状态，保证集群的高可用性。

- Master Server。进程名称hmaster，一个**元数据**管理服务器，管理数据的元信息，如列族的定义，数据的位置，在那个Region Server上等。
- Region Server。 负责实际数据的读写，当有数据请求时，客户端与hbase的Region Server直接通信。

>> 元数据这个词语在数据库或大数据相关的技术中会经常遇见。如hdfs中的namenode,hive中的metaserver等。
#### Region Server

HBase的数据存储是基于HDFS的，RegionServer负责存取hdfs数据。如果一台服务器既是RegionServer节点又是HDFS的DataNode节点，那么RegionServer会把数据的一个副本存储在本地HDFS中，加快访问速度。
如果一个RegionServer迁移到一个新的DataNode节点，这个RegionServer在这个节点的HDFS上没有本地副本，当HBase运行compaction时会把一个副本迁移到本地。

HBase的表按照Row Key的值划分到不同的region，RegionServer负责管理region，一个RegionServer可以管理一个或多个region，最多可以管理1000个region。
![](../hadoop/img/hregion.jpg)

#### Master Server
HBase Master主要负责分配region和管理数据的元信息。
主要功能：
- 协调RegionServer
- 在集群处于数据恢复或者动态调整负载时，分配region到某一个RegionServer中
- 管控集群，监控所有RegionServer的状态
- 提供DDL相关的API，创建、删除、更新表结构。


#### 参考资料
- [深入分析hbase架构](https://zhuanlan.zhihu.com/p/30414252)
