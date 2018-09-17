# Async Framework

## 基本概念
### 编制（Orchestration）与编排（Choreography）

- 编制（Orchestration）—— 面向可执行的流程：通过一个可执行的流程来协同内部及外部的服务交互。通过中心流程来控制总体的目标，涉及的操作，服务调用顺序。
- 编排（Choreography）—— 面向合作：通过消息的交互序列来控制各个部分资源的交互。参与交互的资源都是对等的，没有集中的控制。



## conductor

特点：
* 工作流
* 基于JSON的工作流配置
* 分支处理（case）
* 并行处理和串行处理




###  任务类型
1. System task
2. Worker task

#### 系统任务（集中管理）
|Name	|Purpose|
|------|------|
|DYNAMIC|	A worker task which is derived based on the input expression to the task, rather than being statically defined as part of the blueprint
|DECIDE|	Decision tasks - implements case...switch style fork
|FORK|	Forks a parallel set of tasks. Each set is scheduled to be executed in parallel
|FORK_JOIN_DYNAMIC|	Similar to FORK, but rather than the set of tasks defined in the blueprint for parallel execution, FORK_JOIN_DYNAMIC spawns the parallel tasks based on the input expression to this task
|JOIN|	Complements FORK and FORK_JOIN_DYNAMIC. Used to merge one of more parallel branches*
|SUB_WORKFLOW|	Nest another workflow as a sub workflow task. Upon execution it instantiates the sub workflow and awaits it completion
|EVENT|	Produces an event in a supported eventing system (e.g. Conductor, SQS)

### 处理任务
分布式，不限实现方式（Java,C++，python等）只需Http通信即可


### 参数传递
使用JsonPath
`${SOURCE.input/output.JSONPath}`
来获取不同环节的输入输出信息

### 具体实现
ActionnProcessor  处理


## Parseq

需要一个时间调度器（线程）和nCoreNum+1 个任务调度器（线程）

调度函数

|map|用于结果转换|
|then|




## 参考：
1. [微服务编排之道](https://juejin.im/entry/59eed426f265da432e5b30cb)
