# 案例

## 电商订单与商品

`../templates/er/online-store.dbml` 展示一个小型订单域：用户创建订单，订单由多个订单项组成，订单项关联商品；商品状态用枚举表示。

## 资料提交与审核

`../templates/flow/approval-flow.mmd` 展示资料从填写、完整性检查到保存完成的路径，也包含资料不完整时返回补充的分支。

## 机器人智能调度平台

- `../templates/er/robot-scheduling-platform.dbml`：以场地、楼层和地图为基础，描述车队与机器人、调度任务与竞价、任务派发，以及通道和门梯等共享资源的通行预约关系。
- `../templates/flow/robot-scheduling-platform.mmd`：展示任务校验、向车队征集竞价、选标派发、路线与共享资源协调、执行状态反馈的主要过程，并包含无可用竞价和资源冲突分支。

本案例参考 [Open-RMF](https://www.open-rmf.org/) 公开介绍的多车队互操作、任务分配与冲突协调能力，以及门、电梯等建筑基础设施协作场景。它是 Liktu 社区编写的概念示例，不代表 Open-RMF 官方数据库结构、消息接口或完整运行逻辑。
