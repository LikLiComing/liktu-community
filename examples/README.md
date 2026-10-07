# 案例

## 电商订单与商品

`../templates/er/online-store.dbml` 展示一个小型订单域：用户创建订单，订单由多个订单项组成，订单项关联商品；商品状态用枚举表示。

## 资料提交与审核

`../templates/flow/approval-flow.mmd` 展示资料从填写、完整性检查到保存完成的路径，也包含资料不完整时返回补充的分支。

## 机器人智能调度平台

- `../templates/er/robot-scheduling-platform.dbml`：以场地、楼层和地图为基础，描述车队与机器人、调度任务与竞价、任务派发，以及通道和门梯等共享资源的通行预约关系。
- `../templates/flow/robot-scheduling-platform.mmd`：展示任务校验、向车队征集竞价、选标派发、路线与共享资源协调、执行状态反馈的主要过程，并包含无可用竞价和资源冲突分支。

本案例参考 [Open-RMF](https://www.open-rmf.org/) 公开介绍的多车队互操作、任务分配与冲突协调能力，以及门、电梯等建筑基础设施协作场景。它是 Liktu 社区编写的概念示例，不代表 Open-RMF 官方数据库结构、消息接口或完整运行逻辑。

## JetLinks 物联网平台

- `../templates/er/jetlinks-iot-platform.dbml`：按产品分类、协议、产品和设备组织接入模型，并带上网关、场景规则、告警和通知。网关设备通过 `parent_id` 挂子设备；物模型映射和透传编解码可以挂在产品或单台设备上。画布以设备和产品为中心，网络接入在左，规则告警在上，通知在右，枚举在下。
- `../templates/flow/jetlinks-iot-platform.mmd`：设备报文从网络组件进入设备网关，解码成功后发布到消息总线。注册、子设备、派生物模型和上下线分别处理，然后按产品存储策略落库；命中场景时写告警并发送通知。

关系来自 JetLinks 社区版的设备、网络、规则和通知实体，例如 `dev_product`、`dev_device_instance`、`device_gateway`、`rule_scene` 和 `alarm_record`。图中省略了创建人、修改时间等审计列，也没有放入用户、菜单、插件和文件表。设备属性、事件和日志按产品的存储策略写入时序库，不在这张关系图里建表。

这是 Liktu 社区编写的概念示例，方便对照和学习后按自己的业务修改。它不是 JetLinks 官方 DDL、接口说明或完整运行逻辑。
