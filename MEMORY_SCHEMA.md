# Memory Schema v1.0

> Owner: 佩丽卡 + 李织烟 | 最后更新：2026-06-23

---

## 记忆系统架构

```
三层记忆
│
├── L1 核心记忆（MEMORY.md）
│   │  永久保留，高频访问
│   │  容量：精简（≤500条）
│   │  内容：身份、偏好、决策索引、教训索引
│   │
│   ├── L2 项目记忆（Notion Projects）
│   │  当前活跃项目的详细信息
│   │  按需更新，项目结束归档
│   │
│   └── L3 经验沉淀（Obsidian）
│       长期积累的知识、踩坑、方法论
│       持续增长，按主题组织
│
└── 同步机制
    │
    ├── Notion ←→ Obsidian：按需同步（知识卡片）
    ├── Obsidian ←→ MEMORY.md：月度提炼
    └── MEMORY.md ←→ Notion：实时（决策索引）
```

---

## MEMORY.md 结构（L1 核心记忆）

> 佩丽卡维护，在 QClaw 工作区

```
# MEMORY.md

# A. 核心身份与关系原则
  - 用户画像、交互原则

# B. 用户长期偏好
  - 行为偏好、风格偏好

# C. 当前有效决策
  - 决策索引（Decision Log 入口）

# D. 经验教训索引
  - tech / lesson / feedback / observation
  - 每条含：发生了什么 / 根因 / 对策

# E. 技术与环境约束
  - 已安装工具、环境配置

# F. 观察中事项
  - 活跃项目跟踪、降级规则

# G. 已失效条目索引
  - 归档历史、避免重复记忆
```

**更新规则：**
- 新经验 → 立即写入 MEMORY.md
- 冲突条目 → 旧条目标记 deprecated，覆盖链保留
- 月度提炼 → Obsidian 归档过密内容

---

## Notion Projects 结构（L2 项目记忆）

> 佩丽卡维护，在 Notion

每个项目一个数据库页面，包含：
- 项目 Overview（目标、当前状态、关键约束）
- Roadmap（季度计划）
- 当前 Sprint
- 活跃任务列表
- 技术债务清单
- Decision Log（项目内）

---

## Obsidian 结构（L3 经验沉淀）

> 李织烟维护，本地 Vault

见 KNOWLEDGE_WORKFLOW.md 的目录结构。

---

## 三系统同步规则

### Notion ↔ Obsidian

| 同步方向 | 内容 | 触发 |
|----------|------|------|
| Notion → Obsidian | 项目文档、会议记录 | 每月末 |
| Obsidian → Notion | 知识卡片链接 | 知识沉淀完成时 |

**同步原则：**
- Notion 是「项目状态」的唯一真相
- Obsidian 是「知识内容」的唯一真相
- 两者通过链接互通，不复制内容

### MEMORY.md ↔ 其他系统

| 内容 | 来源 → 写入 | 时机 |
|------|-------------|------|
| 重大决策 | Notion Decision Log → MEMORY.md | 月度提炼 |
| 技术经验 | Obsidian → MEMORY.md | 月度提炼 |
| 教训 | 任意来源 → MEMORY.md | 发生时立即 |

---

## 记忆衰减规则

> 防止记忆系统无限膨胀

| 层 | 衰减规则 | 归档位置 |
|----|----------|----------|
| L1 MEMORY.md | 30天未访问 → 降级到L2或归档 | Obsidian 或 Notion |
| L2 Notion Projects | 项目结束 → Obsidian 归档 | Obsidian Projects/ |
| L3 Obsidian | 60天未更新 → 移动到 Archive | Archive/ |

**禁止删除任何记忆。只归档，不删除。**

---

## 跨 Agent 记忆同步

> 三位 Agent 如何共享记忆

```
QClaw（佩丽卡）
  │
  ├── MEMORY.md → QClaw 工作区（实时）
  │
  └── 定期同步到：
      ├── Notion Projects（项目状态）
      └── Obsidian（知识沉淀）

Claude Code（凯尔希）
  │
  ├── 共享记忆：Notion Tasks + Decision Log
  │
  └── 通过 Notion 读取项目上下文
      （不维护自己的 MEMORY）

Hermes（李织烟）
  │
  ├── Obsidian ← 完整 Vault（本地）
  │
  └── 通过 Obsidian + Notion 与团队共享
```

---

## 冲突解决

**同一事实出现在多个地方时：**
1. 以最新更新为准
2. 其他位置删除或标记「已迁移」
3. 冲突原因记录在 MEMORY.md

---

## 审计清单（每月执行一次）

由佩丽卡在每月末执行：

- [ ] MEMORY.md 条目数量 ≤ 500
- [ ] Obsidian 无重复笔记
- [ ] Notion Tasks 无超过30天「进行中」条目
- [ ] 三系统链接有效（无死链）
- [ ] Decision Log 无超过7天未关闭的L2条目
- [ ] 降级规则执行（过时内容→归档）
