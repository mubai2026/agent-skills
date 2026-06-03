# Agent Skills · 风生水起团队共享技能仓库

**Hermes / Claude Code / Codex 统一技能加载源。**

## 这是什么

一个中心化的 Agent 技能仓库。团队里每个 AI Agent（Hermes、Claude Code、Codex）都可以从这里按需加载技能，而不是各自装一堆冗余包。

## 目录结构

```
agent-skills/
├── skills/              ← 共享技能（每个技能一个目录，含 SKILL.md）
├── agents/              ← 共享 Agent 定义
├── configs/             ← 各工具的适配配置
│   ├── hermes/          → Hermes 的 skills 引用
│   ├── claude-code/     → Claude Code 的 AGENTS.md + settings
│   └── codex/           → Codex 的 config.toml
└── README.md
```

## 各工具如何加载

### Hermes（总大脑）
```bash
# Hermes 直接读取 skills/ 目录
# 在 config.yaml 中配置 skills 路径
skills_path: /path/to/agent-skills/skills
```

### Claude Code
```bash
# 克隆仓库后，在项目中引用
git clone https://github.com/mubai2026/agent-skills.git

# 在 ~/.claude/settings.json 或项目 AGENTS.md 中引用
```

### Codex
参考 `configs/codex/` 目录下的配置示例。

### OpenClaw
OpenClaw 作为网关不直接加载技能。但 session-persist 技能中定义的会话持久化机制可供 OpenClaw 调用，确保消息转发时不丢失上下文。

## 从 ECC 搬运的技能

本仓库部分技能灵感来自 [affaan-m/ECC](https://github.com/affaan-m/ECC)（MIT 许可证）。
我们只挑选了跟团队实际工作流相关的技能，按需定制。

## License

MIT
