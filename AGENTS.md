# AGENTS.md

## 通用规则

- 开始任务前，优先查看当前任务说明、`AGENTS.md`、`PROJECT_CONTEXT.md`、最近的 `log.md`
- 新会话或接手旧项目时，优先通过 `PROJECT_CONTEXT.md` 快速恢复项目上下文
- 改动保持最小必要范围，不擅自扩大修改面
- 不编造结果，不伪造验证状态，不隐瞒未完成项
- 不确定的信息必须标注“待确认”，不要写成既定事实
- 明确任务完成后，更新 `log.md`
- 若项目目标、技术栈、目录结构、核心模块、已知问题或下一步任务发生变化，应同步更新 `PROJECT_CONTEXT.md`
- 输出保持简洁，优先保留后续继续开发所需关键信息
- 默认只读取当前任务直接相关文件，禁止无理由全项目扫描
- 涉及大量文件读取、大范围重构、Git 提交/推送、多 Agent 切换时，必须先说明计划并等待确认

## 默认流程

1. 理解目标与限制
2. 查看 `AGENTS.md`、`PROJECT_CONTEXT.md`、最近的 `log.md`
3. 查找相关上下文与文件
4. 给出简要思路
5. 执行改动或分析
6. 检查/验证可验证部分
7. 总结结果
8. 任务完成后更新 `log.md`
9. 如项目上下文发生变化，更新 `PROJECT_CONTEXT.md`
10. 简短提醒是否需要执行 `/compact`

## Agent 列表

- 项目上下文维护：`AGENTS/Project_AGENT.md`
- Git 版本管理：`AGENTS/Git_AGENT.md`
- 任务规划：`AGENTS/Plan_AGENT.md`
- 开发协作：`AGENTS/Dev_AGENT.md`
- 改动审查：`AGENTS/Review_AGENT.md`
- 结构重构：`AGENTS/Refactor_AGENT.md`
- 日志记录：`AGENTS/Log_AGENT.md`
- 测试验证：`AGENTS/Test_AGENT.md`
- 问题排查：`AGENTS/Debug_AGENT.md`
- README 文档：`AGENTS/README_AGENT.md`
- 发布交付：`AGENTS/Release_AGENT.md`
- Token 与上下文成本控制：`AGENTS/Token_AGENT.md`
- 多 Agent 协调管理：`AGENTS/Coordinator_AGENT.md`
