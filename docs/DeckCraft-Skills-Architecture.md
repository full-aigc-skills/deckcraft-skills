# DeckCraft Skills Architecture

> 2026-10-09; one-skill local candidate. The [Agent Plugins 1.0.0 specification](https://agent-plugins.org/specification) governs plugin packaging.

## 1. Goal and ownership

Use a small set of skills to guide agents through authoring, review and export. Skills own triggers and operational knowledge. Hosts own authorization, tool execution and interaction. DeckCraft owns the document model, commands, rendering and formats. The plugin packages the skills with access to upstream MCP.

## 2. Skill layout

```text
User task → deckcraft-use → connected DeckCraft MCP / installed deckcraft-cli
                           → native deck, readback, rendering and export
```

Only `skills/deckcraft-use/SKILL.md` exists and can be installed alone. The four other proposed entries are deferred. Discover current upstream commands at runtime instead of creating one skill per command. See the [catalog](skill-catalog.md).

## 3. Flow and failure boundaries

Determine task and authorization → discover `deckcraft-cli commands`/`describe` at runtime → run minimal operations → read back the deck → render and review → export and reopen → report artifacts and limits.
A missing CLI triggers diagnosis. Headless has no window screenshot. Successful import still requires content checks. Upstream Remote can resend after a lost response, so a skill cannot promise exactly-once mutation; read back and disclose uncertainty. See [upstream Remote](https://github.com/storytold/deckcraft/blob/d0e57d7e25f9852179cc66be12dd6188f1c05535/crates/mcp/src/backend.rs).

## 4. Decision and verification

Deliver independently usable skills and scenario checks first. Skills do not own operation state, budgets or host authorization. Add a local helper only when a reproduced gap and behavior test justify it. See [requirements](requirements.md), [verification](verification.md) and [Dreamina lessons](dreamina-reference-analysis.md).
