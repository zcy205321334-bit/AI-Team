# Repository Structure v1.0

> Owner: 佩丽卡 | 最后更新：2026-06-23
> 🔒 Frozen v1.0 | 冻结日期：2026-06-23 | 后续修改需基于 Sprint 1 实际运行发现的问题

---

## 唯一真相原则

| 系统 | 内容 | Owner | 禁止 |
|------|------|-------|------|
| GitHub | 代码、ADR、架构文档 | 凯尔希 | 代码以外的最终文档 |
| Notion | 项目状态、任务、决策 | 佩丽卡 | 聊天记录永久化 |
| Obsidian | 知识沉淀、方法论、踩坑 | 李织烟 | 项目状态文档 |

---

## GitHub 结构

```
github.com/zcy205/AI-Team/
│
├── AI-Team/                     # 团队核心文档
│   ├── TEAM_CHARTER.md          # 团队宪章
│   ├── PRODUCT_WORKFLOW.md      # 产品流程
│   ├── ENGINEERING_WORKFLOW.md  # 工程流程
│   ├── KNOWLEDGE_WORKFLOW.md    # 知识流程
│   ├── DECISION_RULES.md        # 决策规则
│   ├── COMMUNICATION.md         # 沟通协议
│   ├── MEMORY_SCHEMA.md         # 记忆结构
│   ├── REPOSITORY_STRUCTURE.md  # 本文件
│   │
│   └── docs/
│       ├── ADR/                 # 架构决策记录
│       │   ├── ADR-001-xxx.md
│       │   └── ADR-002-xxx.md
│       │
│       ├── RFC/                 # 需求评审文档（Markdown备份）
│       │   └── RFC-xxx.md
│       │
│       └── SPECS/               # 技术规格文档
│
├── OzonRelay/                   # OzonRelay 项目
│   ├── README.md
│   ├── src/
│   ├── docs/
│   └── ...
│
├── Hermes/                      # Hermes Agent 配置
│   └── ...
│
└── [其他项目仓库]
```

**GitHub 规范：**
- README 是入口，指向 Notion 获取最新状态
- ADR 是永久记录，不删除
- 每次 Release Tag 对应 Notion Milestone

---

## Notion 结构

```
AI Team（工作区）
│
├── 🏠 首页（Dashboard）
│   ├── 当前 Sprint 概览
│   ├── 阻塞项
│   └── 本周里程碑
│
├── 📋 Tasks（主任务库）
│
├── 🗺️ Roadmap（路线图）
│
├── 🏁 Milestones（里程碑）
│
├── 📝 Decision Log（决策记录）
│
├── 📄 RFCs（需求评审）
│
├── 📊 Sprint（冲刺管理）
│
├── 💼 Projects/
│   ├── OzonRelay/
│   │   ├── README
│   │   ├── 当前里程碑
│   │   └── 技术债务
│   │
│   ├── Hermes/
│   ├── AI系统/
│   ├── 投资/
│   └── 学习/
│
└── 📁 Archive/
    └── [已完成项目归档]
```

---

## Obsidian 结构

见 KNOWLEDGE_WORKFLOW.md

---

## 三系统跳转关系

```
GitHub
  │
  ├── README → Notion 项目页面（获取最新状态）
  ├── ADR → Notion Decision Log（索引）
  └── SPECS → Obsidian 知识卡片（详细说明）

Notion
  │
  ├── Task 完成 → 通知李织烟归档 → Obsidian
  ├── Decision Log → 同步到 MEMORY.md（佩丽卡）
  └── RFC → GitHub docs/RFC/（永久备份）

Obsidian
  │
  ├── 知识卡片 → Notion 相关 Task 附链接
  ├── 踩坑记录 → Notion Decision Log（如涉及决策）
  └── 月度提炼 → MEMORY.md（佩丽卡）
```

---

## 文件命名规范

| 系统 | 规范 | 示例 |
|------|------|------|
| GitHub 文件 | kebab-case + 语义化 | `ozon-pricing-formula.md` |
| GitHub 分支 | `feature/task-xxx-desc` | `feature/task-123-add-pricing` |
| Notion 页面 | 中文或英文，简洁 | `OzonRelay README` |
| Obsidian 笔记 | 中文或英文，主题化 | `Ozon定价公式.md` |
| ADR | `ADR-XXX-标题` | `ADR-001-Ozon-API选型.md` |
| RFC | `RFC-XXX-标题` | `RFC-001-自动上架流程.md` |

---

## 禁止事项

- ❌ 在 Chat 中保存最终代码/文档链接
- ❌ 在 Notion 写详细技术实现（→ GitHub）
- ❌ 在 Obsidian 写项目状态（→ Notion）
- ❌ 在 GitHub 写会议纪要（→ Obsidian）
- ❌ 多处存放同一信息的多个副本
- ❌ 创建文档后不再更新（变成死文档）

---

## 审计规则

每月末检查：

- [ ] GitHub 无超过30天无更新的死文档
- [ ] Notion 无超过60天「进行中」的死任务
- [ ] Obsidian 无超过90天无更新的孤立笔记
- [ ] 三系统之间无矛盾信息
