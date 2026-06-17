# 通用 AGENTS 规则集

> 一套面向个人项目、多 Agent 协作与长期 AI 开发工作流的通用 Agent 操作系统（Agent Operating System）。

一个好用的 Agent 规则集，不应该只是“会说很多话”，而应该做到：

- 先看上下文，再行动
- 尽量最小改动，不随意扩面
- 不虚报验证，不编造完成状态
- 任务结束后留下可继续开发的记录
- 新会话能快速恢复项目上下文，减少重复扫描和 Token 消耗
- 多 Agent 协作时职责清晰、边界明确
- 长期项目能够持续演进，而不是不断重复探索

这份仓库就是围绕这些原则整理出来的 `AGENTS` 规则集合，适合作为个人项目、多 Agent 协作与 AI 开发工作流的通用基线。

------

# Why This Repo

很多 Agent 提示词的问题，不是能力不够，而是边界不清：

- 会直接开始改，而不是先读上下文
- 会顺手扩大修改范围
- 会把“理论可行”说成“已经验证”
- 会在任务结束后不留下可追踪记录
- 新会话需要重新理解整个项目
- 多 Agent 协作时职责重叠
- 不同工具之间缺乏统一上下文
- 浪费大量 Token 在重复分析上

这个仓库的目标很直接：

给 AI Agent 一套更稳定、更克制、更适合长期协作的工作约束。

------

# Features

- 中文优先：面向中文使用场景整理，关键路径和文件名保留英文
- 职责拆分：按项目、规划、开发、测试、审查、排障、发布等角色拆分 Agent
- 多 Agent 协作：通过 Coordinator Agent 管理职责边界与协作状态
- Token 优化：通过 Token Agent 控制上下文范围与成本
- 上下文治理：Project Context、Log、Handoff 三层结构分离
- 默认流程明确：从恢复项目状态到完成交接形成统一节奏
- 结果表达克制：强调真实、可追溯、不过度承诺
- 长期项目友好：适合持续迭代与上下文沉淀
- 可直接复用：适合作为个人项目通用规则基线

------

# Quick Start

如果你准备把这套规则用于自己的项目，推荐按这个顺序理解：

1. 阅读 `AGENTS.md`
2. 查看 `AGENTS/` 下各 Agent 文件
3. 使用 `Project Agent` 生成或更新 `PROJECT_CONTEXT.md`
4. 使用 `Coordinator Agent` 生成或更新 `HANDOFF.md`
5. 开始开发与协作
6. 使用 `Log Agent` 持续维护 `log.md`

最常见的使用方式：

1. `Project Agent` 恢复项目状态
2. `Coordinator Agent` 恢复协作状态
3. `Plan Agent` 明确任务范围
4. `Dev Agent` / `Debug Agent` / `Refactor Agent` 执行任务
5. `Test Agent` 验证结果
6. `Review Agent` 审查改动
7. `Git Agent` 整理提交边界
8. `Log Agent` 更新开发记录
9. `Coordinator Agent` 更新协作状态
10. `Project Agent` 更新项目状态
11. `Token Agent` 评估上下文与成本状态

------

# Repository Structure

```text
.
├─ AGENTS.md
├─ README.md
├─ LICENSE
├─ log.md
├─ PROJECT_CONTEXT.md
├─ HANDOFF.md
└─ AGENTS/
   ├─ Project_AGENT.md
   ├─ Coordinator_AGENT.md
   ├─ Token_AGENT.md
   ├─ Git_AGENT.md
   ├─ Plan_AGENT.md
   ├─ Dev_AGENT.md
   ├─ Review_AGENT.md
   ├─ Refactor_AGENT.md
   ├─ Log_AGENT.md
   ├─ Test_AGENT.md
   ├─ Debug_AGENT.md
   ├─ README_AGENT.md
   └─ Release_AGENT.md
```

------

# Core Files

## `AGENTS.md`

总入口。

定义：

- 通用规则
- Agent 列表
- Agent 调用原则
- 默认工作流

如果只先看一个文件，先看这里。

------

## `PROJECT_CONTEXT.md`

项目当前状态说明书。

用于记录：

- 项目定位
- 核心目标
- 当前开发阶段
- 技术栈
- 项目结构
- 核心模块
- 已知问题
- 下一步任务
- 开发约束

回答的问题：

> 项目是什么？

由：

```
Project Agent
```

负责维护。

------

## `HANDOFF.md`

当前协作状态说明书。

用于记录：

- 当前主 Agent
- 当前辅助 Agent
- Agent 分工
- 当前任务状态
- 已确认决策
- 已排除方案
- 当前风险
- 下一步任务

回答的问题：

> 当前谁在负责什么？

由：

```
Coordinator Agent
```

负责维护。

------

## `log.md`

开发历史记录文件。

用于记录：

- 做了什么
- 修改了什么
- 验证到了哪里
- 遇到了什么问题
- 下一步建议

回答的问题：

> 项目过去发生了什么？

由：

```
Log Agent
```

负责维护。

------

## `AGENTS/*.md`

每个文件对应一个独立职责的 Agent。

遵循：

> 一个 Agent 只负责一个领域。

避免职责重叠和规则污染。

------

# Agents Overview

| Agent                  | 作用                                    |
| ---------------------- | --------------------------------------- |
| `Project_AGENT.md`     | 维护项目状态与 `PROJECT_CONTEXT.md`     |
| `Coordinator_AGENT.md` | 管理多 Agent 协作与 `HANDOFF.md`        |
| `Token_AGENT.md`       | 控制上下文范围与 Token 成本             |
| `Plan_AGENT.md`        | 拆解任务、控制范围、排序优先级          |
| `Dev_AGENT.md`         | 执行开发、修复和最小必要改动            |
| `Review_AGENT.md`      | 审查当前改动是否合理、是否有风险        |
| `Refactor_AGENT.md`    | 在不改变行为前提下优化结构              |
| `Test_AGENT.md`        | 基于实际执行结果做验证说明              |
| `Debug_AGENT.md`       | 复现问题、定位原因、给出修复建议        |
| `README_AGENT.md`      | 编写或优化 README 文档                  |
| `Git_AGENT.md`         | 管理提交边界、commit message 与版本状态 |
| `Log_AGENT.md`         | 维护开发历史记录                        |
| `Release_AGENT.md`     | 发布前检查、整理说明与风险提示          |

------

# Default Workflow

这套规则集默认按以下节奏工作：

1. Project Agent 恢复项目状态
2. Coordinator Agent 恢复协作状态
3. Plan Agent 明确任务范围
4. Dev Agent / Debug Agent / Refactor Agent 执行任务
5. Test Agent 验证结果
6. Review Agent 审查风险
7. Git Agent 整理提交边界
8. Log Agent 更新开发历史
9. Coordinator Agent 更新 HANDOFF.md
10. Project Agent 更新 PROJECT_CONTEXT.md
11. Token Agent 评估上下文与成本状态

重点不是流程多，而是职责清晰。

------

# PROJECT_CONTEXT.md Usage

适用于：

- 新项目启动
- 接手旧项目
- 新会话恢复上下文
- 项目经过多轮迭代后重新整理状态
- 希望减少 AI 重复扫描项目带来的成本

推荐新会话提示词：

```text
请先阅读：

- AGENTS.md
- PROJECT_CONTEXT.md
- HANDOFF.md
- 最近的 log.md

阅读后请简要总结：

1. 当前项目是什么；
2. 当前开发阶段是什么；
3. 当前主线任务是什么；
4. 当前协作状态是什么；
5. 最近完成了什么；
6. 下一步最应该做什么；
7. 本项目有哪些开发约束。

总结完成后等待下一步任务。
```

------

# Design Principles

- 最小必要改动
- 真实表达状态
- 先恢复上下文
- 保留继续开发所需信息
- 单一职责原则
- 多 Agent 协作优先
- Project Context、Log、Handoff 分层治理
- 不重复探索已确认结论
- 不编造项目状态
- 不编造验证结果
- 不编造完成状态
- 适合长期迭代

------

# Suitable For

- 个人项目
- AI 辅助编码工作流
- Codex
- Claude Code
- OpenClaw
- Cursor
- 多 Agent 协作场景
- 长期项目维护
- 通用工程协作规范
- 希望沉淀长期可复用 Agent 规则的人

------

# Suggested Extensions

如果后续继续扩展，可以增加：

- Frontend Agent
- Backend Agent
- Database Agent
- Product Agent
- Prompt Agent
- Workflow Agent
- MCP Agent
- CI/CD Agent
- Security Agent
- UI Agent
- Docs Agent
- Team Collaboration Template

------

# License

本仓库采用 [MIT License](https://chatgpt.com/c/LICENSE)。
