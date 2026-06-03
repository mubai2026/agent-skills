---
name: strategic-compact
description: 战略压缩 — 在逻辑断点主动压缩上下文，避免自动压缩丢失关键信息
version: 1.0.0
origin: 风生水起（改编自 ECC）
platforms: [hermes, claude-code]
---

# Strategic Compact · 战略压缩

在任务阶段的逻辑断点手动触发上下文压缩，代替随机自动压缩。

## 何时压缩

**适合压缩的场景：**
- 研究/探索完成后，准备开始实现前
- 完成一个里程碑，准备进入下一阶段前
- 调试完成后，继续功能开发前
- 失败的方案放弃后，尝试新方案前

**不适合压缩的场景：**
- 正在实现过程中（会丢失变量名、文件路径、中间状态）

## 压缩策略

1. 先调用 session-persist 保存当前状态
2. 再执行 /compact
3. 从 session 文件恢复关键上下文
