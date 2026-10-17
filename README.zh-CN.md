# DeckCraft Skills

> 面向演示文稿创作、检查和导出的最小 Agent 技能。已提供本地技能入口，真实宿主与原生调用待验证。

[English](README.md) | 简体中文 · [文档导航](docs/README.md) · [参考分析](docs/dreamina-reference-analysis.md)

## 项目定位

服务需要用 Agent 制作、审阅和交付演示文稿的创作者，以及维护可审计自动化的工程团队。本仓负责触发描述、操作知识、渐进式参考与场景验收。宿主负责授权与工具调用；DeckCraft 负责编辑、渲染和导出。
DeckCraft 原生应用由 storytold/deckcraft 维护；本项目不重写其编辑引擎，也不把 PowerPoint 完整兼容性作为已有能力。

## 一眼看懂

```text
用户任务 → 技能路由 → 按需读取操作参考 → DeckCraft CLI/MCP → 文档与渲染验收
```

| 属性 | 当前事实（2026-10-09） |
|---|---|
| 仓库 | `deckcraft-skills`，独立 Git 仓库，分支 `main` |
| 产品阶段 | 单技能本地候选；运行验证待推进 |
| 可安装技能 | 1 个 `deckcraft-use` |
| 发布版本与远端 | 尚无发布版本；尚未配置 Git 远端 |
| 技能清单 | `skills/deckcraft-use/SKILL.md` |
| 宿主支持 | 没有已验证宿主组合 |
| 许可证 | 本仓 Apache-2.0；DeckCraft 上游 MIT OR Apache-2.0 |

## 能力与边界

| 目标能力 | 输入 / 输出 | 状态与验收 |
|---|---|---|
| 命令发现 | 运行时命令列表 → 可用操作 | 上游接口已确认；本项目未实现 |
| 创建与编辑 | 内容需求 → 可编辑文稿 | 规划；需回读文本、结构和布局 |
| 视觉检查 | 幻灯片 → 渲染图和评审 | 规划；模型意见不能代替结构校验 |
| 导出交付 | 原生文稿 → PPTX/PDF/图片及回执 | 规划；需重开、摘要和类型检查 |
| 恢复 | 既有执行记录 → 对账与后续动作 | 规划；未知修改不能直接重发 |

上游有 CLI、Headless MCP 和桌面 Remote 模式；这不代表本项目已经完成适配。PDF 图稿当前为栅格加真实文本层；真实 PPTX 保真和跨平台宿主验收仍需独立证据。

## 安装状态

当前可以从本地路径单独加载 `skills/deckcraft-use/`，但尚无公开市场发行、锁文件或已验证宿主，因此不提供假定可用的远端安装命令。

## 快速开始

先阅读 [技能规划](docs/skill-catalog.md) 和 [兼容性](docs/compatibility.md)，确认你要贡献或评审的范围。
已经自行安装 DeckCraft CLI 的读者，可参考上游源码声明的只读接口：

```bash
deckcraft-cli --version
deckcraft-cli commands
deckcraft-cli describe slide.new
```

这些是上游命令示例，本轮未执行，也不是本项目安装验证。写文件、启动进程和连接桌面须处于任务授权范围内。

## 配置与运行模式

本技能不包含运行时服务或环境变量配置；它说明 Headless/Remote 的适用范围，具体 MCP 进程和权限由插件与宿主负责。
上游 `deckcraft-cli mcp` 是无界面模式；`deckcraft-cli mcp --connect 7990` 需要已经启动并监听该端口的桌面应用。不要把窗口截图能力归给 Headless。

## Dreamina 借鉴与优化

借鉴技能路由、渐进式参考、运行时发现、来源固定和证据分层；针对 DeckCraft 增加文稿回读、导出重开与视觉检查。Dreamina 的计费控制器不属于本插件的基础架构。详见 [分析与优化优先级](docs/dreamina-reference-analysis.md)。

## 质量与验证

本地技能结构检查与固定上游 headless MCP 冒烟已通过；宿主安装和完整真实文稿验收仍须分别记录，不能由结构检查代替。
[验证矩阵](docs/verification.md) 定义技能安装、插件加载、MCP 调用和真实文稿验收的独立证据。

## 路线与贡献

先交付可独立安装的技能和可用的 DeckCraft 操作流程，再验证插件和宿主。参见 [ROADMAP](ROADMAP.md)、[贡献指南](CONTRIBUTING.md)、[安全策略](SECURITY.md) 和 [来源说明](ATTRIBUTION.md)。
文档是实现输入，不代表执行功能已经完成。尚无公开问题追踪或支持渠道，当前使用项目协作会话。

## 许可证

[Apache-2.0](LICENSE)。没有复制 DeckCraft、Dreamina 的实现代码或品牌素材；未来引入资源须逐项登记来源、许可和用途。

## 场景技能开发候选

已增加 6 个领域场景技能及 1 个内嵌编辑器入口。详见 [场景目录](docs/scene-skills.md)。本地未发布候选，不代表全部场景的创作质量已验收。

## 场景操作手册

新增 `deckcraft-scenario-playbooks`：8 条带具体命令、参数与检查的流程，见 [技能入口](skills/deckcraft-scenario-playbooks/SKILL.md)。示例数据需替换，实际运行与创作效果状态见命令证据；不将目录存在当验收通过。

## main模板与品牌复用候选

新增[main模板、页面复用及结构化目录指导](skills/deckcraft-scenario-playbooks/references/main-workflows.md)，保留89个新增标识和旧目录重复项的歧义。已有场景及新增模板/复用流程通过Windows原生main回归：真实starter、指定页顺序、可编辑PPTX和源文件保持已核对；外部PowerPoint渲染及真实宿主同步仍未验收。
