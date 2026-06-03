---
name: context-sync
description: 跨平台上下文同步 — 在 Hermes/Claude Code/Codex/OpenClaw 之间传递会话上下文
version: 1.0.0
origin: 风生水起
platforms: [hermes, claude-code, codex, openclaw]
---

# Context Sync · 跨平台上下文同步

确保同一项目中切换 Agent 工具时不丢失上下文。

## 解决的问题

- Hermes 跟 Claude Code 之间切换时，之前讨论的内容无法延续
- OpenClaw 网关转发消息时丢失上下文历史
- 飞书群里跟 Hermes 聊一半，切到 Claude Code 做开发，回来 Hermes 不记得了

## 同步机制

共享目录 `~/.hermes/context/` 存储最新上下文摘要：

```
~/.hermes/context/
├── current.md       # 当前活跃上下文
├── projects/
│   └── project-x/
│       ├── context.md
│       └── decisions.md
└── history/
    └── 2026-06-03.md
```

## Hermes 使用

加载 `memory-management-protocol` 技能后自动读取上下文同步文件。

## Claude Code 使用

在 `AGENTS.md` 中引用：
```markdown
项目上下文位于 ~/.hermes/context/projects/PROJECT/
请在开始工作前读取 context.md
```

## Codex 使用

在 `config.toml` 中配置 skills 路径引用共享上下文。
