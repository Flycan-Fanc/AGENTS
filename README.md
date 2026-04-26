# 通用 AGENTS 规则集

> 一套面向个人项目与 AI 协作开发场景的通用 Agent 规则模板。

一个好用的 Agent 规则集，不应该只是“会说很多话”，而应该做到：

- 先看上下文，再行动
- 尽量最小改动，不随意扩面
- 不虚报验证，不编造完成状态
- 任务结束后留下可继续开发的记录
- 新会话能快速恢复项目上下文，减少重复扫描和 token 消耗

这份仓库就是围绕这些原则整理出来的 `AGENTS` 规则集合，适合直接作为你自己的通用基线复用。

## Why This Repo

很多 Agent 提示词的问题，不是能力不够，而是边界不清：

- 会直接开始改，而不是先读上下文
- 会顺手扩大修改范围
- 会把“理论可行”说成“已经验证”
- 会在任务结束后不留下可追踪记录
- 新会话需要重新理解整个项目，浪费大量上下文和额度

这个仓库的目标很直接：给 AI Agent 一套更稳定、更克制、更适合长期协作的工作约束。

## Features

- 中文优先：面向中文使用场景整理，关键路径和文件名保留英文
- 职责拆分：按项目上下文、规划、开发、测试、审查、排障、发布等角色拆分 Agent
- 默认流程明确：从理解任务、读取 `PROJECT_CONTEXT.md` 到更新 `log.md` 都有统一节奏
- 上下文可恢复：通过 `PROJECT_CONTEXT.md` 帮助 AI 快速理解项目状态
- 结果表达克制：强调真实、可追溯、不过度承诺
- 适合复用：可直接拷贝到其他项目作为基础规则集

## Quick Start

如果你准备把这套规则用于自己的项目，推荐按这个顺序理解：

1. 先阅读 `AGENTS.md`
2. 再查看 `AGENTS/` 下各角色文件
3. 新项目或旧项目接手时，先使用 `Project Agent` 生成 `PROJECT_CONTEXT.md`
4. 开始协作后，把每次明确任务记录到 `log.md`
5. 当项目目标、技术栈、目录结构或下一步任务变化时，同步更新 `PROJECT_CONTEXT.md`

最常见的使用方式是：

1. `Project Agent` 生成或更新 `PROJECT_CONTEXT.md`
2. `Plan Agent` 明确范围
3. `Dev Agent` / `Debug Agent` / `Refactor Agent` 执行任务
4. `Test Agent` 验证结果
5. `Review Agent` 复核改动
6. `Git Agent` 整理提交边界
7. `Log Agent` 更新 `log.md`

## Repository Structure

```text
.
├─ AGENTS.md
├─ README.md
├─ LICENSE
├─ log.md
├─ PROJECT_CONTEXT.md
└─ AGENTS/
   ├─ Project_AGENT.md
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

## Core Files

### `AGENTS.md`

总入口。定义通用规则、默认流程、Agent 列表和 `PROJECT_CONTEXT.md` 维护规则。  
如果只先看一个文件，就先看这个。

### `PROJECT_CONTEXT.md`

项目上下文入口文件。  
用于记录项目当前状态，包括项目目标、技术栈、目录结构、核心模块、已知问题、下一步任务和开发约束。

它的作用不是替代 README，而是帮助 AI 在新会话中快速恢复项目理解。

### `AGENTS/*.md`

每个文件对应一个具体职责的 Agent，适合按任务类型组合使用，而不是把所有要求塞进同一份长提示词里。

### `log.md`

任务记录文件。  
用于保留本次做了什么、改了什么、验证到了哪里、还有什么没完成。

`log.md` 记录开发过程，`PROJECT_CONTEXT.md` 记录项目当前状态。

## Agents Overview

| Agent               | 作用                                            |
| ------------------- | ----------------------------------------------- |
| `Project_AGENT.md`  | 维护项目上下文，生成或更新 `PROJECT_CONTEXT.md` |
| `Plan_AGENT.md`     | 拆解任务、控制范围、排序优先级                  |
| `Dev_AGENT.md`      | 执行开发、修复和最小必要改动                    |
| `Review_AGENT.md`   | 审查当前改动是否合理、是否有风险                |
| `Refactor_AGENT.md` | 在不改变行为前提下优化结构                      |
| `Test_AGENT.md`     | 基于实际执行结果做验证说明                      |
| `Debug_AGENT.md`    | 复现问题、定位原因、给出修复或建议              |
| `README_AGENT.md`   | 编写或优化 README 文档                          |
| `Git_AGENT.md`      | 管理提交边界、commit message 和版本状态         |
| `Log_AGENT.md`      | 任务完成后更新 `log.md`                         |
| `Release_AGENT.md`  | 发布前检查、整理说明和标记风险                  |

## Default Workflow

这套规则集默认按以下节奏工作：

1. 理解目标与限制
2. 查看 `AGENTS.md`、`PROJECT_CONTEXT.md`、最近的 `log.md`
3. 查找相关上下文与文件
4. 给出简要思路
5. 执行改动或分析
6. 检查或验证可验证部分
7. 总结结果
8. 更新 `log.md`
9. 如项目上下文发生变化，更新 `PROJECT_CONTEXT.md`
10. 简短提醒是否需要执行 `/compact`

重点不是流程多，而是让输出更可靠。

## PROJECT_CONTEXT.md Usage

`PROJECT_CONTEXT.md` 适合在以下场景使用：

- 新项目启动
- 接手旧项目
- Codex / Claude Code / OpenClaw 新开会话
- 切换模型或 API 后历史上下文不可用
- 项目经过多轮迭代后需要重新整理当前状态
- 希望减少 AI 重复扫描项目带来的 token 消耗

推荐新会话提示词：

```text
请先阅读 PROJECT_CONTEXT.md、AGENTS.md、log.md、README.md。

阅读后请简要总结：
1. 当前项目是什么；
2. 技术栈是什么；
3. 当前阶段是什么；
4. 最近完成了什么；
5. 下一步最应该做什么；
6. 本项目有哪些不能随便改的规则。

总结完成后，等待我的下一步任务。
```

当以下内容发生变化时，建议更新 `PROJECT_CONTEXT.md`：

- 项目定位或核心目标
- 当前开发阶段
- 技术栈
- 目录结构
- 核心功能模块
- 关键业务规则
- 已知问题
- 下一步任务
- 重要开发约束

## Design Principles

- 最小必要改动：不擅自扩大修改面
- 真实表达状态：未验证就明确写未验证
- 先恢复上下文：新会话优先阅读 `PROJECT_CONTEXT.md`
- 保留继续开发所需信息：避免下次重新摸索
- 区分过程与状态：`log.md` 记录过程，`PROJECT_CONTEXT.md` 记录当前状态
- 按角色拆分规则：降低提示词混乱和职责重叠
- 适合长期迭代：文档、日志、提交边界都更清晰

## Suitable For

- 个人项目
- AI 辅助编码工作流
- Codex / Claude Code / OpenClaw 等 Agent 编程场景
- 通用工程协作规范
- 希望沉淀长期可复用 Agent 规则的人

## Suggested Extensions

如果后续要继续扩展，可以在这套基线之上增加：

- Frontend Agent
- Backend Agent
- Database Agent
- Prompt / Workflow Agent
- CI/CD Agent
- Security Agent
- UI Agent
- Docs Agent
- 多人协作约定模板

## License

本仓库采用 [MIT License](./LICENSE)。
