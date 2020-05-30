### yarn

#### ResourceManager
- Scheduler
- Application Manager

##### Scheduler
- 负责为运行的容器分配资源，
- 纯调度器(pure scheduler)，只负责调度
##### Application Manager
- 接收作业提交
- 启动App Mstr管理应用程序
- 监控App Mstr状态，重启失败的App Mstr

#### NodeManager
三个逻辑概念：
- Container
- AppMstr
- Executor

功能：
- 定时向Resource Manager汇报本节点的资源使用状态和容器的运行状态
- 监督应用程序的生命周期
- 监控、管理容器消耗的资源(CPU，内存)信息
- 监控容器的运行状态和资源使用情况，杀死失去控制的应用程序
- 接收来自App Mstr的启动/停止容器的请求

##### Application Master
- yarn上的每一个应用都有一个专有的App Mstr
- Apps Mstr运行在应用程序启动时的第一个容器中
- App Mstr与Resource Manager协商获取容器执行mapper、reducer任务

App Mstr请求的资源：
- 处理作业需要的文件块
- 为应用程序创建的以容器为单位的资源
- 容器大小（例如，1GB内存，1 VCore）
- 资源在何处分配，依据从NameNode获取的块存储位置信息（如机器1的节点10上分配4个容器，机器2的节点20上分配8个容器）
- 资源请求的优先级
>> Application Master是一个特定的框架，MapReduce程序是MRAppMaster，Spark是SparkAppMaster。

##### Container
Container是对于资源的抽象，它封装了某个节点上的多维度资源，如内存、CPU等。

