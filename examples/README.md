# 案例

## 资料提交与审核

`../templates/flow/approval-flow.mmd` 与同名 `approval-flow.drawio` 展示资料从填写、完整性检查到保存完成的路径，也包含资料不完整时返回补充的分支。Liktu 首页和在线流程图打开 `.drawio`；`.mmd` 供 Mermaid 预览和编辑。

## 机器人智能调度平台

- `../templates/er/robot-scheduling-platform.dbml`：以场地、楼层和地图为基础，描述车队与机器人、调度任务与竞价、任务派发，以及通道和门梯等共享资源的通行预约关系。
- `../templates/flow/robot-scheduling-platform.mmd`：展示任务校验、向车队征集竞价、选标派发、路线与共享资源协调、执行状态反馈的主要过程，并包含无可用竞价和资源冲突分支。
- `../templates/flow/robot-scheduling-platform.drawio`：同一流程的可编辑图，Liktu 在线流程图直接打开这一份。

本案例参考 [Open-RMF](https://www.open-rmf.org/) 公开介绍的多车队互操作、任务分配与冲突协调能力，以及门、电梯等建筑基础设施协作场景。它是 Liktu 社区编写的概念示例，不代表 Open-RMF 官方数据库结构、消息接口或完整运行逻辑。

## 智慧空间协同运营

- [案例说明](smart-space-operations.md)：人员定位、设备物联、工单调度及 OptaPlanner 约束求解经验的行业化抽象。
- `../templates/er/smart-space-operations.dbml`：空间、设备、位置事件、工单、排程方案和派工关系。
- `../templates/flow/smart-space-operations.mmd`：从多源事件到动态约束排程、执行反馈和重排。
- `../templates/flow/smart-space-operations.drawio`：同一流程的可编辑图。
- `../templates/flow/smart-space-operations-architecture.drawio`：规划调度服务、资源与任务缓存、OptaPlanner 求解集群、工单服务和基础数据链路。

## 服务行业 AI Agent

- [案例说明](property-service-agent.md)：聚焦 LangChain4j、LangGraph4j、多分支 Agent 编排、RAG 与受控工具调用。
- `../templates/er/property-service-agent.dbml`：会话、Agent 节点、知识切片、工具调用及工单。
- `../templates/flow/property-service-agent.mmd`：意图路由、知识检索、工具调用、重试和转人工。
- `../templates/flow/property-service-agent.drawio`：同一编排流程的可编辑图。

## 企业信用与融资服务

- [案例说明](enterprise-credit-financing.md)：企业资料、征信、实地核验、融资评估与合作机构协同。
- `../templates/er/enterprise-credit-financing.dbml`：企业、报告、认证、申请、评估、机构匹配及电子合同。
- `../templates/flow/enterprise-credit-financing.mmd`：从授权采集到评估、机构流转和签署归档。
- `../templates/flow/enterprise-credit-financing.drawio`：同一业务流程的可编辑图。

## 企业数据治理与 BI

- [案例说明](enterprise-data-cleansing.md)：Spark 清洗服务封装、批次治理、质量追踪与 BI 数据集发布。
- `../templates/er/enterprise-data-cleansing.dbml`：来源、采集批次、规则、质量问题、标准数据集和 BI 视图。
- `../templates/flow/enterprise-data-cleansing.mmd`：从接口数据接入到清洗、质量记录和 BI 消费。
- `../templates/flow/enterprise-data-cleansing.drawio`：同一清洗流程的可编辑图。

## JetLinks 物联网平台

- `../templates/er/jetlinks-iot-platform.dbml`：按产品分类、协议、产品和设备组织接入模型，并带上网关、场景规则、告警和通知。网关设备通过 `parent_id` 挂子设备；物模型映射和透传编解码可以挂在产品或单台设备上。画布以设备和产品为中心，网络接入在左，规则告警在上，通知在右，枚举在下。
- `../templates/flow/jetlinks-iot-platform.mmd`：设备报文从网络组件进入设备网关，解码成功后发布到消息总线。注册、子设备、派生物模型和上下线分别处理，然后按产品存储策略落库；命中场景时写告警并发送通知。
- `../templates/flow/jetlinks-iot-platform.drawio`：同一设备消息流程的可编辑图。

关系来自 JetLinks 社区版的设备、网络、规则和通知实体，例如 `dev_product`、`dev_device_instance`、`device_gateway`、`rule_scene` 和 `alarm_record`。图中省略了创建人、修改时间等审计列，也没有放入用户、菜单、插件和文件表。设备属性、事件和日志按产品的存储策略写入时序库，不在这张关系图里建表。

这是 Liktu 社区编写的概念示例，方便对照和学习后按自己的业务修改。它不是 JetLinks 官方 DDL、接口说明或完整运行逻辑。
