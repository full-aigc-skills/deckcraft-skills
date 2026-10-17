# DeckCraft Skills

> A minimal Agent Skill for presentation authoring, review and export. The local skill exists; host and native calls remain unverified.

English | [简体中文](README.zh-CN.md) · [Documentation](docs/README.md) · [Reference analysis](docs/dreamina-reference-analysis.md)

## Positioning

For creators using agents to build, review and deliver presentations, and engineers maintaining auditable automation. This repository owns triggers, operational knowledge, progressive references and scenario acceptance. The host owns authorization and tool execution; DeckCraft owns editing, rendering and export.
The native application is maintained by storytold/deckcraft. This project does not replace its editor engine or claim full PowerPoint compatibility.

## At a glance

```text
User task → skill routing → operation references → DeckCraft CLI/MCP → document and render checks
```

| Property | Current fact (2026-10-09) |
|---|---|
| Repository | `deckcraft-skills`, independent Git repository on `main` |
| Stage | One-skill local candidate; runtime verification pending |
| Installable skills | One `deckcraft-use` skill |
| Release and remote | No release version; no Git remote configured |
| Skill manifest | `skills/deckcraft-use/SKILL.md` |
| Host support | No verified host combinations |
| License | Apache-2.0 here; MIT OR Apache-2.0 for upstream DeckCraft |

## Capabilities and boundaries

| Target capability | Input / output | Status and acceptance |
|---|---|---|
| Command discovery | Runtime command list → available operations | Upstream interface confirmed; integration not implemented |
| Authoring | Content brief → editable deck | Planned; read back text, structure and layout |
| Visual review | Slide → rendered image and review | Planned; model opinion cannot replace structural checks |
| Delivery | Native deck → PPTX/PDF/images and receipts | Planned; reopen, hash and validate file type |
| Recovery | Existing execution record → reconciliation and next action | Planned; never blindly replay an uncertain mutation |

Upstream provides a CLI, Headless MCP and desktop Remote mode. This does not establish integration here. PDF artwork currently uses raster images with a real-text layer. Real-world PPTX fidelity and host/platform acceptance need separate evidence.

## Installation status

The skill can be loaded from the local `skills/deckcraft-use/` path. There is no public marketplace release, lock file or verified host, so speculative remote installation commands are intentionally absent.

## Quick start

Read the [Skill plan](docs/skill-catalog.md) and [compatibility boundaries](docs/compatibility.md) to select a contribution or review scope.
Readers who already installed the upstream CLI can consult its source-declared read-only interfaces:

```bash
deckcraft-cli --version
deckcraft-cli commands
deckcraft-cli describe slide.new
```

These are upstream examples, not executed in this delivery and not installation verification for this project. File writes, process startup and desktop connections must be within the authorized task scope.

## Configuration and runtime modes

This skill has no runtime service or environment-variable contract. It describes when Headless or Remote mode applies; the plugin and host own MCP processes and permissions.
Upstream `deckcraft-cli mcp` is headless. `deckcraft-cli mcp --connect 7990` needs an already running desktop control server on that port. Window screenshots are unavailable in Headless.

## Dreamina lessons and improvements

Reuse skill routing, progressive references, runtime discovery, pinned sources and evidence layers. Add deck readback, export reopen and visual review for DeckCraft. Dreamina's billing controller is outside the base plugin architecture. See [the reference analysis and priorities](docs/dreamina-reference-analysis.md).

## Quality and verification

Local skill structure checks and a headless MCP smoke against pinned DeckCraft source passed. Host installation and full real-deck acceptance require separate evidence.
The [verification matrix](docs/verification.md) separates skill installation, plugin loading, MCP calls and real-deck acceptance.

## Roadmap and contribution

Deliver individually installable skills and a usable DeckCraft workflow first, then verify the plugin in real hosts. See [ROADMAP](ROADMAP.md), [contribution guide](CONTRIBUTING.md), [security policy](SECURITY.md) and [attribution](ATTRIBUTION.md).
Documents are implementation inputs, not proof of delivered runtime behavior. No public issue tracker or support channel has been configured; use the project collaboration session for now.

## License

[Apache-2.0](LICENSE). No DeckCraft or Dreamina implementation code or brand assets were copied. Future imports must record their source, license and purpose.

## 场景技能开发候选

已增加 6 个领域场景技能及 1 个内嵌编辑器入口。详见 [场景目录](docs/scene-skills.md)。本地未发布候选，不代表全部场景的创作质量已验收。

## 场景操作手册

新增 `deckcraft-scenario-playbooks`：8 条带具体命令、参数与检查的流程，见 [技能入口](skills/deckcraft-scenario-playbooks/SKILL.md)。示例数据需替换，实际运行与创作效果状态见命令证据；不将目录存在当验收通过。

## main模板与品牌复用候选

新增[main模板、页面复用及结构化目录指导](skills/deckcraft-scenario-playbooks/references/main-workflows.md)，保留89个新增标识和旧目录重复项的歧义。已有场景及新增模板/复用流程通过Windows原生main回归：真实starter、指定页顺序、可编辑PPTX和源文件保持已核对；外部PowerPoint渲染及真实宿主同步仍未验收。
