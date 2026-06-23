# Communication Protocol v2.0

> Owner: 佩丽卡 | 最后更新：2026-06-23 | 状态：已确认
> 关联：TEAM_CHARTER.md · PRODUCT_WORKFLOW.md · ENGINEERING_WORKFLOW.md · KNOWLEDGE_WORKFLOW.md · DECISION_RULES.md

---

## 沟通原则

**Chat** 用于需要即时响应的同步讨论。
**Notion / GitHub / Obsidian** 用于需要持久化的信息，按存储类型分流。

> 规则：任何在 Chat 中产生的需要执行或追溯的结论，必须在 24 小时内写入对应存储。

---

## 六通道分流规则

| 通道 | 介质 | 存储内容 | Owner |
|------|------|----------|-------|
| 产品需求 | Notion Task | 产品需求、验收标准、执行任务 | 佩丽卡 |
| 技术实现 | GitHub | 代码、PR、ADR | 凯尔希 |
| 长期知识 | Obsidian | 知识卡片、踩坑记录、Sprint 总结 | 李织烟 |
| 产品决策 | Notion Decision Log | L2+ 产品决策记录 | 佩丽卡 |
| 技术决策 | GitHub ADR | L3+ 架构/技术决策记录 | 凯尔希 |
| 知识决策 | Obsidian Decision Summary | 知识体系调整决策 | 李织烟 |

> 每条信息只存在于一个通道。同一信息出现在多处时，以最新更新为准，删除旧位置。

---

## 响应时效

| 消息类型 | 预期响应时间 | 说明 |
|----------|-------------|------|
| P0 阻断问题 | 30 分钟内 | 系统不可用、数据丢失 |
| P1 功能问题 | 4 小时内 | 直接影响核心目标 |
| BLOCKED 升级 | 4 小时内 | 含明确阻塞原因 + 已尝试方案 |
| 普通消息 | 24 小时内 | 无需立即处理 |
| RFC 评审 | 48 小时内 | 含技术评估或知识影响字段 |
| 非紧急讨论 | 48 小时内 | 无需追踪的协作讨论 |

---

## 三方交接规范

### 佩丽卡 → 凯尔希

**通道：Notion Task（Owner = 凯尔希）**

Task 包含：Why + 验收标准 + 相关 RFC 链接 + ETA
凯尔希完成：附 GitHub PR 链接 → 佩丽卡验收

### 佩丽卡 → 李织烟

**通道：Notion Task（Owner = 李织烟）**

Task 包含：知识类型 + Obsidian 存放路径 + 来源参考
李织烟完成：附 Obsidian 链接 → 佩丽卡审核

### 凯尔希 → 李织烟

**通道：Chat（@李织烟）+ Notion Task 关联**

触发：代码有可复用逻辑
流程：Chat @李织烟 说明 + Notion Task 关联代码路径 → 李织烟主动归档

### 任意 → 佩丽卡（BLOCKED 升级）

**通道：Chat（BLOCKED 格式）+ Notion Task Risk 字段**

格式见下方「消息格式规范」。

---

## 定期同步节奏

| 时间 | 内容 | 通道 |
|------|------|------|
| 每周一 09:00 | Sprint 规划发布 | Notion Sprint + Chat |
| 每周五 18:00 | Sprint 回顾 | Notion Sprint 总结 + Obsidian Reviews + Chat |
| 每月末 | 月度回顾 + 下月路线图 | Notion + Chat |

---

## 消息格式规范

### BLOCKED 升级（强制格式）

```
[BLOCKED] {Task-id} {任务名}
原因：{阻塞原因}
已尝试：{尝试的解决方案}
需要：{需要的帮助}
```

### Task 完成通知

```
[TASK-{id}] {任务名} 完成
链接：{PR/Obsidian/Notion 链接}
需要：验收 / 审核 / 归档
```

### RFC 评审请求

```
[RFC-{xxx}] {标题}
状态：评审中
链接：{Notion RFC 链接}
请 {凯尔希/李织烟} 填写：{技术评估/知识影响}
截止：发出后 48 小时
```

### Chat 五原则

1. 简短具体，避免长段描述
2. 紧急问题用 `[BLOCKED]` 标签
3. 非紧急协作无需标签
4. 用链接代替大段文字
5. 结论必须写入对应存储，不留在 Chat

---

## 禁止事项

- 禁止通过 Chat 传递需要执行的任务细节（必须转为 Notion Task）
- 禁止在 Chat 中做需要追溯的决策结论（必须写入 Notion Decision Log 或 GitHub ADR）
- 禁止在没有 Notion Task 的情况下直接要求凯尔希或李织烟执行任务

---

## 跨文档引用规范

本文件引用了其他 Workflow 的内容，不再重复定义：

| 引用内容 | 来源文档 |
|----------|---------|
| GitHub PR 规范 | ENGINEERING_WORKFLOW.md |
| ADR 格式与存放 | ENGINEERING_WORKFLOW.md |
| Obsidian 目录结构 | KNOWLEDGE_WORKFLOW.md |
| 知识卡片模板 | KNOWLEDGE_WORKFLOW.md |
| Sprint 回顾操作步骤 | PRODUCT_WORKFLOW.md |
| RFC 评审超时处理 | PRODUCT_WORKFLOW.md |
| BLOCKED 升级判断标准 | DECISION_RULES.md |
| 决策回顾流程 | DECISION_RULES.md |
