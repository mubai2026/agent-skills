# Claude Code 配置 — agent-skills 引用
# 在项目根目录的 AGENTS.md 中引用本仓库的技能

## 技能引用

将 agent-skills 克隆到本地后，在 `~/.claude/settings.json` 中：
```json
{
  "skills": {
    "paths": ["/path/to/agent-skills/skills"]
  }
}
```

## 可用技能

| 技能 | 用途 |
|------|------|
| session-persist | 会话持久化 |
| context-sync | 跨平台上下文同步 |
| strategic-compact | 战略压缩 |
| continuous-learning | 持续学习 |
| code-review | 代码审查 |
| tdd-workflow | TDD 工作流 |
| security-review | 安全审查 |
