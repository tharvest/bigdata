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
- 定时想Resource Manager汇报本节点的资源使用状态和容器的运行状态
- 监督应用程序的生命周期
- 监控、管理容器消耗的资源(CPU，内存)信息
- 监控容器的运行状态和资源使用情况，杀死失去控制的应用程序
- 接收来自App Mstr的启动/停止容器的请求

##### Application Master
- yarn上的每一个应用都有一个专有的App Mstr
- Apps Mstr运行在应用程序启动时的第一个容器中
- App Mstr与Resource Manager协商获取容器执行mapper、reducer任务
- 