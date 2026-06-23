# Product Workflow v2.0

> Owner: 佩丽卡 | 最后更新：2026-06-23 | 状态：已确认
> 🔒 Frozen v1.0 | 冻结日期：2026-06-23 | 后续修改需基于 Sprint 1 实际运行发现的问题
> 关联：ENGINEERING_WORKFLOW.md · KNOWLEDGE_WORKFLOW.md · DECISION_RULES.md

---

## 职责范围

产品能力负责：Product Vision · Roadmap · Priority · Sprint · Notion · 产品决策。

**本 Workflow 只定义产品端的流程。技术实现细节 → ENGINEERING_WORKFLOW.md。知识整理细节 → KNOWLEDGE_WORKFLOW.md。**

---

## 需求生命周期

```
需求提出
  │
  ▼
[1] 需求采集 ──────────────► Notion Tasks（待处理）
  │
  ▼
[2] 需求分析（佩丽卡）
  │  ├─ Why + 验收标准
  │  └─ 若涉及技术方案 → 发布 RFC → 凯尔希/李织烟 评估
  │
  ▼
[3] RFC 评审（≥L2 决策）
  │  ├─ 佩丽卡：主持 + 拍板
  │  ├─ 凯尔希：技术可行性（ENGINEERING_WORKFLOW.md）
  │  └─ 李织烟：知识影响（KNOWLEDGE_WORKFLOW.md）
  │
  ▼
[4] 排入 Sprint ───────────► Notion Sprint
  │
  ├──► [5a] 凯尔希执行（技术） ──► GitHub PR
  ├──► [5b] 李织烟执行（知识） ──► Obsidian
  └──► [5c] 佩丽卡执行（架构/决策） ──► Notion
  │
  ▼
[6] 验收（佩丽卡）
  │  └─ 对照验收标准核查 Notion Task
  │
  ▼
[7] 归档
      ├─ Notion Task → 完成（Proof = 证据链接）
      ├─ 知识沉淀 → Obsidian（KNOWLEDGE_WORKFLOW.md）
      └─ 经验更新 → MEMORY.md
```

---

## Notion 数据库

> Owner: 佩丽卡。详细字段定义 → 手动在 Notion UI 中配置（API 有已知 bug，见 CROSS_REVIEW.md）。

### 数据库清单与 Owner

| 数据库 | 存储内容 | Owner |
|--------|----------|-------|
| Tasks | 产品需求与执行任务 | 佩丽卡 |
| Roadmap | 季度路线图 | 佩丽卡 |
| Milestones | 里程碑 | 佩丽卡 |
| Decision Log | L2+ 产品决策 | 佩丽卡 |
| RFCs | 需求评审记录 | 佩丽卡 |
| Sprint | 冲刺管理 | 佩丽卡 |

> Notion 中的 RFC 数据库是产品决策的唯一真相源。技术评估内容引用自凯尔希填写的字段，但不重复存储在 Notion 之外。

---

## Sprint 管理

### Sprint 节奏

- **规划**：每周一 09:00，佩丽卡从 Tasks 库拉取未完成 P0/P1 任务，分配到当周 Sprint
- **回顾**：每周五 18:00，佩丽卡更新 Sprint 总结（完成数 / 阻塞 / 教训）
- **容量上限**：每 Sprint 不超过 5 个 P1 及以上任务
- **通知**：规划/回顾完成后 → Chat 通知凯尔希 + 李织烟

### Sprint 规划步骤

1. 拉取 Tasks 库中所有未完成的 P0/P1 任务
2. 逐条确认 Why、Owner、ETA 是否仍然有效（无效 → 降级或删除）
3. 从高优先级起选，本周可完成的进入 Sprint
4. Notion Sprint 记录中 Relation → Tasks
5. 发布 Sprint 页面链接到 Chat

### Sprint 回顾步骤

1. 检查所有关联 Task 的完成情况
2. 未完成 → 移至下个 Sprint 或降级
3. 填写 Sprint 总结（完成数 / 阻塞项 / 教训）
4. 通知李织烟：关键经验 → Obsidian Reviews（见 KNOWLEDGE_WORKFLOW.md）

---

## RFC 流程

> 详细 RFC 模板 → Notion RFC 数据库内嵌模板。评审流程 → 见下方。

### RFC 生命周期

```
草稿（佩丽卡填写 Why + 验收标准）
  │
  ▼
评审中（发出给凯尔希 + 李织烟）
  │
  ├──► 凯尔希：48 小时内填写「技术评估」
  └──► 李织烟：48 小时内填写「知识影响」
  │
  ▼
通过 / 拒绝 / 需修改（佩丽卡拍板）
  │
  ▼
执行 → 对应 Task 创建
```

### 评审超时处理

- 发出 RFC 后 48 小时无反馈 → 佩丽卡在 Chat 催一次
- 再 24 小时无反馈 → 视为无意见，默认继续

### RFC 状态变更

RFC 状态变更必须同步记录到 Notion Decision Log（L2+ 决策）。

---

## 优先级判断

| 级别 | 定义 | 响应时间 |
|------|------|----------|
| P0 | 阻断性：系统不可用、数据丢失 | 立即处理 |
| P1 | 高价值：直接影响核心目标 | 本周 Sprint |
| P2 | 中价值：体验优化、长期债务 | 未来 Sprint |
| P3 | 低价值：锦上添花 | 资源充裕时处理 |

---

## 与其他能力域的交接规范

### → 工程能力（凯尔希）

- 介质：Notion Task（Owner = 凯尔希）
- 内容：Why + 验收标准 + 相关 RFC 链接
- 完成：凯尔希附 GitHub PR 链接 → 佩丽卡验收

### → 知识能力（李织烟）

- 介质：Notion Task（Owner = 李织烟）
- 内容：知识类型 + Obsidian 存放路径 + 来源参考
- 完成：李织烟附 Obsidian 链接 → 佩丽卡审核

### ← 工程能力 / 知识能力

- 收到 BLOCKED 升级 → 佩丽卡判断并更新 Notion Decision Log
- 收到方向质疑 → 佩丽卡判断是否发起 RFC

---

## 不在本 Workflow 中定义的内容

以下内容已在对应文档中定义，本 Workflow 不重复：

| 内容 | 文档 |
|------|------|
| GitHub PR 规范 | ENGINEERING_WORKFLOW.md |
| ADR 模板与存放 | ENGINEERING_WORKFLOW.md |
| 代码规范 | ENGINEERING_WORKFLOW.md |
| Obsidian 目录结构 | KNOWLEDGE_WORKFLOW.md |
| 知识卡片模板 | KNOWLEDGE_WORKFLOW.md |
| 本地操作规范 | KNOWLEDGE_WORKFLOW.md |
| L1/L2/L3/L4 决策流程 | DECISION_RULES.md |
| BLOCKED 升级格式 | COMMUNICATION.md |
| RFC 技术评估字段定义 | ENGINEERING_WORKFLOW.md |
| 知识影响评估字段定义 | KNOWLEDGE_WORKFLOW.md |
