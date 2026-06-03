---
name: session-persist
description: 会话持久化 — 自动保存/恢复会话状态，解决 OpenClaw/Hermes/Claude Code 跨会话上下文断层问题
version: 1.0.0
origin: 风生水起
platforms: [hermes, claude-code, codex]
---

# Session Persist · 会话持久化

跨会话上下文保持。每次对话结束后自动将关键状态写入持久化存储，下次启动时自动恢复。

## 解决的问题

OpenClaw/Hermes/Claude Code 之间的上下文记忆断层：
- 网关重启后之前对话丢失
- 会话 context 达到上限 compact 后丢失关键信息
- 跨平台切换时无法携带上下文

## 架构

```
[OpenClaw 网关] ←→ [Hermes Agent] ←→ [Session Persist Store]
                       ↓
               [Claude Code / Codex]
                       ↓
             [~/.hermes/sessions/ 或项目目录]
```

## 使用方式

### Hermes (当前 Agent)

每次会话结束时自动执行：
1. 将当前会话关键状态写入 `~/.hermes/sessions/`
2. 状态包含：对话摘要、待办事项、决策记录、关键路径
3. 下次启动时检查同项目的 session 文件并加载

### Claude Code

```bash
# 保存当前会话
/save-session

# 恢复之前的会话
/resume-session
```

## 会话文件格式

```json
{
  "session_id": "uuid",
  "timestamp": "2026-06-03T14:00:00Z",
  "project": "agent-skills",
  "summary": "完成了 session-persist 技能的编写",
  "decisions": ["使用 JSON 格式存储会话状态", "存储目录统一在 ~/.hermes/sessions/"],
  "todos": ["编写 context-sync 技能", "配置各工具的加载路径"],
  "context_chain": ["前一会话摘要...", "当前会话摘要..."],
  "files_touched": ["skills/session-persist/SKILL.md"]
}
```
