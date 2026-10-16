# DeckCraft Skills 架构

> 2026-10-09；单技能本地候选。Agent Plugins 1.0.0 以 [正式规范](https://agent-plugins.org/specification)为准。

## 1. 目标与归属

用少量技能引导 Agent 完成建稿、检查和导出。技能负责触发与操作知识；宿主负责授权、工具执行和交互；DeckCraft 负责文档模型、命令、渲染与格式。插件把技能和上游 MCP 接入组成可安装包。知识、插件和原生应用各有一个事实源。

## 2. 技能结构

```text
用户任务 → deckcraft-use → 已连接的 DeckCraft MCP / 已安装的 deckcraft-cli
                         → 原生文稿、结构回读、渲染和导出
```

当前只有 `skills/deckcraft-use/SKILL.md`，可单独安装；其余四个原设想先不开发。命令在当前上游运行时发现，不逐条建技能。[目录与触发](skill-catalog.md)

## 3. 主要流程与失败

确定用户任务和授权范围 → 运行时查询 `deckcraft-cli commands`/`describe` → 选择最少操作 → 回读文稿结构 → 渲染检查 → 导出并重新打开 → 报告可验证产物与限制。
缺少 CLI 时只做诊断；Headless 无整窗截图时说明模式差异；导入成功后仍须检查内容是否丢失。Remote 修改在回复丢失时有重发风险，技能不能声称恰好执行一次，应回读并报告不确定性。[上游 Remote](https://github.com/storytold/deckcraft/blob/d0e57d7e25f9852179cc66be12dd6188f1c05535/crates/mcp/src/backend.rs)

## 4. 决策与验证

先实现独立可用的技能和场景回归。技能不存储操作状态，不设计预算系统，不替代宿主权限。只有可复现缺口和行为测试证明需要时，才增加局部辅助脚本。[需求](requirements.md)、[验证矩阵](verification.md)、[Dreamina 借鉴](dreamina-reference-analysis.md)。
