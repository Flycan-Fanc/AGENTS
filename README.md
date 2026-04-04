# 通用 AGENTS 规则集

> 一套面向个人项目与 AI 协作开发场景的通用 Agent 规则模板。

一个好用的 Agent 规则集，不应该只是“会说很多话”，而应该做到：

- 先看上下文，再行动
- 尽量最小改动，不随意扩面
- 不虚报验证，不编造完成状态
- 任务结束后留下可继续开发的记录

这份仓库就是围绕这些原则整理出来的 `AGENTS` 规则集合，适合直接作为你自己的通用基线复用。

## Why This Repo

很多 Agent 提示词的问题，不是能力不够，而是边界不清：

- 会直接开始改，而不是先读上下文
- 会顺手扩大修改范围
- 会把“理论可行”说成“已经验证”
- 会在任务结束后不留下可追踪记录

这个仓库的目标很直接：给 AI Agent 一套更稳定、更克制、更适合长期协作的工作约束。

## Features

- 中文优先：面向中文使用场景整理，关键路径和文件名保留英文
- 职责拆分：按规划、开发、测试、审查、排障、发布等角色拆分 Agent
- 默认流程明确：从理解任务到更新 `log.md` 都有统一节奏
- 结果表达克制：强调真实、可追溯、不过度承诺
- 适合复用：可直接拷贝到其他项目作为基础规则集

## Quick Start

如果你准备把这套规则用于自己的项目，推荐按这个顺序理解：

1. 先阅读 `AGENTS.md`
2. 再查看 `AGENTS/` 下各角色文件
3. 开始协作后，把每次明确任务记录到 `log.md`

最常见的使用方式是：

1. `Plan Agent` 明确范围
2. `Dev Agent` / `Debug Agent` / `Refactor Agent` 执行任务
3. `Test Agent` 验证结果
4. `Review Agent` 复核改动
5. `Git Agent` 整理提交边界
6. `Log Agent` 更新 `log.md`

## Repository Structure

```text
.
├─ AGENTS.md
├─ README.md
├─ LICENSE
├─ log.md
└─ AGENTS/
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

总入口。定义通用规则、默认流程和 Agent 列表。  
如果只先看一个文件，就先看这个。

### `AGENTS/*.md`

每个文件对应一个具体职责的 Agent，适合按任务类型组合使用，而不是把所有要求塞进同一份长提示词里。

### `log.md`

任务记录文件。  
用于保留本次做了什么、改了什么、验证到了哪里、还有什么没完成。

## Agents Overview

| Agent | 作用 |
| --- | --- |
| `Plan_AGENT.md` | 拆解任务、控制范围、排序优先级 |
| `Dev_AGENT.md` | 执行开发、修复和最小必要改动 |
| `Review_AGENT.md` | 审查当前改动是否合理、是否有风险 |
| `Refactor_AGENT.md` | 在不改变行为前提下优化结构 |
| `Test_AGENT.md` | 基于实际执行结果做验证说明 |
| `Debug_AGENT.md` | 复现问题、定位原因、给出修复或建议 |
| `README_AGENT.md` | 编写或优化 README 文档 |
| `Git_AGENT.md` | 管理提交边界、commit message 和版本状态 |
| `Log_AGENT.md` | 任务完成后更新 `log.md` |
| `Release_AGENT.md` | 发布前检查、整理说明和标记风险 |

## Default Workflow

这套规则集默认按以下节奏工作：

1. 理解目标与限制
2. 查找相关上下文与文件
3. 给出简要思路
4. 执行改动或分析
5. 检查或验证可验证部分
6. 总结结果
7. 更新 `log.md`
8. 简短提醒是否需要执行 `/compact`

重点不是流程多，而是让输出更可靠。

## Design Principles

- 最小必要改动：不擅自扩大修改面
- 真实表达状态：未验证就明确写未验证
- 保留继续开发所需信息：避免下次重新摸索
- 按角色拆分规则：降低提示词混乱和职责重叠
- 适合长期迭代：文档、日志、提交边界都更清晰

## Suitable For

- 个人项目
- AI 辅助编码工作流
- 通用工程协作规范
- 希望沉淀长期可复用 Agent 规则的人

## Suggested Extensions

如果后续要继续扩展，可以在这套基线之上增加：

- Frontend Agent
- Backend Agent
- Database Agent
- Prompt / Workflow Agent
- CI/CD Agent
- 多人协作约定模板

## License

本仓库采用 [MIT License](./LICENSE)。
