# Engineering Workflow v1.0

> Owner: 凯尔希 | 最后更新：2026-06-23
> 🔒 Frozen v1.0 | 冻结日期：2026-06-23 | Sprint 1 复盘后更新：2026-07-01

---

## 职责边界

- **负责**：怎么实现、工程质量、代码规范、测试、部署、**统一执行引擎 + 状态机 + 插件架构**
- **不负责**：做什么、为什么做、项目优先级

**Sprint 1 复盘约束：停止增加平行管线，聚焦统一执行引擎建设。**

**收到 Notion Task 后，质疑方案是合理的，质疑方向是不允许的。**

---

## 开发流程

```
接收 Notion Task（Owner = 凯尔希）
  │
  ▼
[1] 理解需求
  │  └─ 阅读 Task 的 Why + 验收标准
  │  └─ 如有 RFC，参考 RFC-XXX 技术评估
  │
  ▼
[2] 技术方案设计
  │  └─ 在 Notion Task 下补充技术方案
  │  └─ 如有重大技术选择 → 发 ADR 给佩丽卡
  │
  ▼
[3] 实现
  │  └─ 代码 → GitHub（PR 规范见下方）
  │
  ▼
[4] 测试
  │  └─ 单元测试 / 集成测试
  │  └─ 本地验证通过后提 PR
  │
  ▼
[5] PR 提交流程
  │  ├─ PR 标题格式：[Task编号] 简短描述
  │  ├─ PR Body 包含：解决什么问题、测试方式、相关文档
  │  └─ 至少一个 Reviewer（佩丽卡 或 李织烟）
  │
  ▼
[6] Merge
  │  └─ Review 通过后合并
  │  └─ 合并后更新 Notion Task 状态 → 完成
  │  └─ Notion Task 的 Proof 字段填 PR 链接
  │
  ▼
[7] 通知
      └─ Chat 中通知佩丽卡 + 李织烟
```

---

## Git 规范

### 分支命名

```
feature/task-{notion-task-id}-{简短描述}
bugfix/task-{notion-task-id}-{简短描述}
hotfix/task-{notion-task-id}-{简短描述}
```

### Commit 规范

```
[type] task-{id}: 简短描述

可选详细说明（换行）
- 变更点1
- 变更点2
```

type: `feat` | `fix` | `docs` | `refactor` | `test` | `chore`

### PR 模板

```markdown
## 概述
[task-id] 做了什么

## 验收标准检查
- [ ] 标准1
- [ ] 标准2

## 测试方式
[如何在本地验证]

## 影响范围
[会影响到哪些模块]

## 相关文档
[链接]
```

---

## ADR（架构决策记录）

> 当技术方案有重大选择时，必须创建 ADR。

存放位置：`AI-Team/docs/ADR/`（GitHub）

| 字段 | 内容 |
|------|------|
| ADR-XXX | 编号 + 标题 |
| Status | Accepted / Deprecated |
| Context | 技术背景和问题 |
| Decision | 最终选择 |
| Consequences | 正面/负面影响 |

---

## 代码规范

| 语言 | 规范 |
|------|------|
| Python | PEP 8 + type hints |
| TypeScript/JS | ESLint + Prettier |
| Shell | ShellCheck |
| PowerShell | PSScriptAnalyzer |

**所有新代码必须通过 Linter。**

---

## 与其他成员的协作

### 接收佩丽卡的需求

- 阅读 Notion Task 的 Why 和验收标准
- 有疑问 → Chat 中提出，等佩丽卡澄清
- 不接受模糊需求继续执行

### 通知李织烟（知识沉淀）

- 代码有可复用逻辑 → PR 中 @李织烟 提醒归档
- 部署后需要运维文档 → Notion Task 标记

### 通知佩丽卡（验收/方向）

- 完成后 → Notion Task 附 PR 链接
- 发现方向问题 → 提出 RFC 或直接 Chat

---

## 技术债务管理

- 在 Notion Tasks 中创建 Tech Debt 类型任务
- 优先级的判断权归佩丽卡
- 每周 Sprint 预留 20% 容量处理 Tech Debt
