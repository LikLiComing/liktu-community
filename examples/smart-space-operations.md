# 智慧空间协同运营

## 场景与问题

住宅、商业空间和园区的现场作业涉及设备设施、人员位置、服务工单与排程资源。设备协议和定位终端来源多样，告警、工单和现场人员状态分散在不同系统中；调度人员需要同时考虑任务优先级、资源可用性和动态业务规则。

## 方案设计

以空间和设施台账为基础，通过协议适配与事件驱动接入设备状态和定位数据。定位数据经过滤波、轨迹纠偏后更新人员状态；设备告警和业务事件进入工单池。调度侧将工单与资源池画像、动态约束装配为规划问题，再由约束求解器生成候选排程。

工单调度的关键不是简单按时间或距离排序，而是把业务规则显式建模：硬约束用于保证不可违反的资格、资源和时间条件；软约束用于权衡时效、优先级、负载均衡等目标。方案使用 OptaPlanner 封装规划模型、评分和 Late Acceptance 搜索，通过迭代比较候选解，在复杂组合空间中持续改进可行方案。流程图中的硬软约束示例是行业化说明，不宣称复现特定项目的完整规则清单。

> 技术名称说明：项目经历使用 OptaPlanner。Timefold Solver 是原 OptaPlanner 团队后续 fork 发展的开源求解器，不应倒写成项目当时使用的名称。可将相关算法经验表述为“OptaPlanner（可对照 Timefold Solver 后续生态）”。

算法资料：[OptaPlanner Late Acceptance 说明](https://docs.optaplanner.org/snapshot/master/optaplanner-docs/html/ch10.html)；[Timefold Solver 项目说明](https://github.com/TimefoldAI/timefold-solver)。

## ER 图与流程图

- `../templates/er/smart-space-operations.dbml`：空间、资产、设备事件、定位轨迹、工单、排程轮次、人员派工和硬软约束。
- `../templates/flow/smart-space-operations.mmd`：从多源事件接入、工单汇聚，到约束评分、派工发布和动态重排。
- `../templates/flow/smart-space-operations.drawio`：同一流程的可编辑图。Liktu 在线流程图打开这一份，也可在 diagrams.net 中继续改。
- `../templates/flow/smart-space-operations-architecture.drawio`：规划调度服务、资源池与任务缓存、OptaPlanner 求解集群、工单服务及基础数据链路的行业架构示意。

## 适用范围

适用于需要统一管理多类设施设备、现场人员和服务工单，并在多约束条件下进行动态派工的物业、园区及商业空间运营场景。图中数据模型为概念示例。
