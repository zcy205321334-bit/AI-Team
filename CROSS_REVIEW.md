# Workflow 交叉审查报告 v1.0

> 审查人：佩丽卡 | 审查范围：全部7份文档 | 日期：2026-06-23

---

## 一、职责冲突（3处）

### 冲突 1：RFC「技术评估」的归属

**PRODUCT_WORKFLOW：**
> RFC 评审 → 凯尔希填写技术评估

**ENGINEERING_WORKFLOW：**
> 未提及 RFC 参与义务

**问题：** RFC 是佩丽卡创建的数据库，评审流程嵌在我的文档里。凯尔希的文档没有承诺参与 RFC 评审。这会造成「流程存在但没人执行」。

**建议：** ENGINEERING_WORKFLOW.md 中明确增加一条：
> 「参与 RFC 评审：在收到佩丽卡 RFC 通知后48小时内填写技术评估字段。」

---

### 冲突 2：Obsidian 目录结构的定义权

**MEMORY_SCHEMA + PRODUCT_WORKFLOW：**
> 我定义了 Obsidian 的完整目录结构（Projects/Topics/SOPs/Reviews）

**KNOWLEDGE_WORKFLOW：**
> 李织烟的文档完全复制了这个结构

**问题：** Obsidian 归李织烟管，但目录结构是我定的。这在逻辑上是对的（架构归我），但没有被明确授权。如果李织烟要调整目录结构，她需要改谁的文件？

**建议：** 在 KNOWLEDGE_WORKFLOW.md 开头加一条：
> 「Obsidian 目录结构由佩丽卡定义（见 MEMORY_SCHEMA.md），李织烟负责执行和维护。目录调整需佩丽卡发起 Decision Log。」

---

### 冲突 3：Sprint 规划的「谁来做」

**PRODUCT_WORKFLOW：**
> 每周一 09:00 佩丽卡做 Sprint 规划

**TEAM_CHARTER：**
> 未明确 Sprint 规划的执行者是谁

**问题：** 「Sprint 规划」这个动作是我设计的，但谁真正去 Notion 创建 Sprint 记录？是佩丽卡用 Notion API 写，还是通知凯尔希/李织烟做？

**建议：** PRODUCT_WORKFLOW 中明确：
> 「Sprint 规划由佩丽卡通过 Notion API 自动创建 Notion Sprint 记录。」
> （或者改为：Sprint 手动创建，由佩丽卡在 Notion 中填写）

---

## 二、信息重复（2处）

### 重复 1：Obsidian 目录结构出现在三处

| 出现位置 | 内容 |
|----------|------|
| PRODUCT_WORKFLOW.md | 简版目录 |
| KNOWLEDGE_WORKFLOW.md | 完整目录 |
| MEMORY_SCHEMA.md | 目录 + 说明 |

**问题：** 同一信息写三遍，维护成本高，改一处要同步三处。

**建议：** Obsidian 目录结构只在 KNOWLEDGE_WORKFLOW.md 中保留完整版本。MEMORY_SCHEMA.md 只写「详见 KNOWLEDGE_WORKFLOW.md」，PRODUCT_WORKFLOW.md 只写「见 Obsidian 目录规范」。

---

### 重复 2：Sprint 规划的触发时间

| 出现位置 | 内容 |
|----------|------|
| PRODUCT_WORKFLOW.md | 每周一 09:00 |
| COMMUNICATION.md | 每周一 09:00 Sprint 规划发布 |

**问题：** 同一触发时间出现在两份文档中。

**建议：** Sprint 节奏只在 PRODUCT_WORKFLOW.md 中定义，COMMUNICATION.md 只引用，不重复。

---

## 三、缺少 Owner（5处）

### 缺口 1：RFC「评审」是异步还是同步？

**现状：** RFC 评审流程写了「评审会议（异步）」，但没说清楚在哪里评论。

**缺失内容：**
- 评审在哪里进行？（Notion RFC 页面评论？Chat？）
- 凯尔希/李织烟不回应怎么办？（超时机制）

**建议：** RFC 模板中加一行：
> 「评审超时：发出 RFC 后48小时无反馈 → 佩丽卡在 Chat 中催一次 → 再24小时无反馈 → 视为无意见，默认通过。」

---

### 缺口 2：Chat 中的「升级」没有格式规范

**COMMUNICATION.md 定义了升级格式：**
> `[BLOKED] {任务名} / 原因 / 已尝试 / 需要`

**但 ENGINEERING_WORKFLOW 和 KNOWLEDGE_WORKFLOW 都没有引用这个格式。**

**缺失内容：** 凯尔希/李织烟的文档中未说明如何使用这个格式。

**建议：** 在 ENGINEERING_WORKFLOW 和 KNOWLEDGE_WORKFLOW 中各加一句：
> 「发现阻塞时，按 COMMUNICATION.md 格式发送升级消息。」

---

### 缺口 3：Sprint 回顾「谁来写总结」

**现状：**
- PRODUCT_WORKFLOW 说「周五18:00 Sprint 回顾」
- COMMUNICATION.md 说「Sprint 回顾由佩丽卡写」

**问题：** 佩丽卡做了 Sprint 规划，也由佩丽卡写回顾。但「归档到 Obsidian」这个动作按分工是李织烟的职责。

**建议：** 修改 Sprint 回顾流程：
- 佩丽卡：Notion Sprint 页面填写「总结」字段（完成数/阻塞/教训）
- 李织烟：读取 Notion Sprint 总结 → 写入 Obsidian Reviews/

---

### 缺口 4：本地自动化操作没有明确 Owner

**问题：**
- OzonRelay 运行在 Windows 本地
- Hermes 在 WSL 里
- Claude Code 在 VSCode 里
- 但「Windows 本地定时任务」「浏览器自动化」这类操作，谁负责？

**现状：**
- KNOWLEDGE_WORKFLOW 提到「李织烟负责 WSL/Linux 环境操作」
- 但没说 Windows 本地操作（OzonRelay 扩展、剪映、浏览器）归谁

**建议：** 补充到 TEAM_CHARTER.md：
> 「本地 Windows 操作（OzonRelay 扩展、定时任务、剪映等）→ 凯尔希（通过 Claude Code）
> 本地 WSL/Linux 操作 → 李织烟」

---

### 缺口 5：Obsidian 审核没有明确「不通过怎么办」

**现状：**
- 李织烟归档 → 通知佩丽卡审核
- 但没说佩丽卡「不通过」时怎么处理

**建议：** KNOWLEDGE_WORKFLOW.md 加一行：
> 「审核不通过：佩丽卡在 Obsidian 评论区指出问题 → 李织烟修改 → 重新通知」

---

## 四、可进一步自动化的环节（3处）

### 自动化 1：Sprint 规划

**现状：** 每周一手动创建 Notion Sprint 记录。

**建议：** 佩丽卡通过 Notion API 每周一自动创建 Sprint 记录，或用 cron 触发。

---

### 自动化 2：RFC 超时提醒

**现状：** RFC 发出后48小时无反馈，佩丽卡手动催。

**建议：** 通过 cron 定期扫描 Notion RFC 数据库，对「发出超过48小时且状态仍为评审中」的 RFC 自动在 Chat 中发送提醒。

---

### 自动化 3：Notion Task → 完成 → 通知李织烟

**现状：** 凯尔希 PR 合并后，手动 Chat 通知李织烟归档。

**建议：** GitHub PR 合并触发 webhook → 通知佩丽卡 → 佩丽卡在 Notion Task 中附 PR 链接并通知李织烟。或者凯尔希在合并 PR 时直接 @李织烟。

---

## 五、降低沟通成本的建议（4条）

### 建议 1：交接格式强制化

**现状：** Notion Task 的 Why 字段是规范，但实际交接时可能为空。

**建议：** 在 ENGINEERING_WORKFLOW.md 加一条强制规范：
> 「Owner 收到 Task 时必须检查 Why 字段是否已填写。若为空，立即返回佩丽卡要求补充，不得自行猜测执行。」

---

### 建议 2：Chat 消息最小化原则

**现状：** 当前三个 Workflow 都写了通知规则，但没有说清楚「什么情况不发 Chat」。

**建议：** 在 COMMUNICATION.md 加「沉默规则」：
> 「以下情况不发 Chat 消息：
> - 已在 Notion 更新且无紧急变更
> - 非相关人员的任务完成
> - 已超过24小时无进展（除非有重大阻塞）」
>
> 「以下情况必须发 Chat：
> - P0/P1 阻塞
> - L2 及以上决策需求
> - Sprint 规划发布
> - Sprint 回顾完成」

---

### 建议 3：RFC 评审异步化，明确截止

**现状：** RFC 评审写了「异步」，但凯尔希/李织烟何时回复没有期限。

**建议：** RFC 模板加一行：
> 「截止日期：发出后48小时」

---

### 建议 4：Decision Log 触发自动同步到 MEMORY.md

**现状：** L2 决策记录在 Notion，手动同步到 MEMORY.md。

**建议：** 每月末佩丽卡做一次全量同步。未来可做自动化：每次 Notion Decision Log 更新 → 触发佩丽卡评估是否需要更新 MEMORY.md。

---

## 优先级排序

建议按以下顺序处理（基于影响大小）：

| 优先级 | 问题 | 类型 |
|--------|------|------|
| P0 | Sprint 规划「谁来做」不明 | 缺口 |
| P0 | Windows 本地操作无 Owner | 缺口 |
| P1 | Obsidian 目录三处重复 | 重复 |
| P1 | RFC 超时无机制 | 缺口 |
| P2 | Sprint 回顾分工不清 | 缺口 |
| P2 | Chat 沉默规则缺失 | 沟通成本 |
| P3 | 交接格式无强制检查 | 沟通成本 |

---

## 待凯尔希和李织烟确认的事项

### 待凯尔希确认

1. 是否接受在 ENGINEERING_WORKFLOW.md 中增加 RFC 参与义务？
2. Windows 本地操作（OzonRelay 扩展、浏览器自动化）是否归你？

### 待李织烟确认

1. Obsidian 目录结构由佩丽卡定义，是否接受？
2. Sprint 回顾的 Obsidian 归档是否归你？
3. Obsidian 在本地的实际路径是什么？（以便我更新目录结构）

---

*审查完成。以上建议供团队讨论，确认后更新对应文档。*
