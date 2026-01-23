---
name: interaction-guideline
description: 提供关于如何通过自然语言高效触发和调用 Trae Skills 的最佳实践指南。适用于用户询问如何使用技能、如何优化提示词、或如何通过对话驱动复杂工作流的情况。
---

# 自然语言交互最佳实践 (Interaction Best Practices)

本 Skill 指导用户和 AI 如何通过自然语言建立高效的协作模式，以精准触发并充分利用已有的 Skill。

## 核心交互模式

### 1. 意图驱动触发 (Intent-Driven Triggering)
不要直接指挥 AI "运行某个脚本"，而是描述你的**最终目标**。Skill 的描述文件会捕捉这些意图。

- **推荐写法**: "我想重构一下这部分代码的性能" -> 触发 `React Best Practices`
- **推荐写法**: "帮我分析这个功能的实现方案" -> 触发 `Brainstorming`

### 2. 角色化指令 (Role-Based Commands)
通过赋予 AI 特定身份，可以更精确地激活对应的 Skill 集。

- **场景**: "以架构师的身份审核我的 API 设计" -> 激活 `Architect APIDesign`
- **场景**: "作为测试专家，为这个模块编写自动化脚本" -> 激活 `Browser Automation`

### 3. 上下文引用 (Context Referencing)
利用 Trae 的上下文感知能力，通过自然语言引用特定文件或状态。

- **技巧**: "参考 [README.md](README.md) 中的规范，提交当前更改" -> 组合 `Git Workflow`

## 高级交互技巧

### 1. 组合式工作流 (Chained Workflows)
在一个请求中描述多个步骤，AI 会自动按序调用 Skill。
- **示例**: "先帮我**头脑风暴**一下这个新功能，确认后生成一份 **FastAPI** 的后端实现，最后用 **Git** 提交。"

### 2. 反向查询 (Reverse Lookup)
如果不确定该用哪个技能，可以直接询问。
- **询问**: "我现在想做数据库迁移，我们有相关的 Skill 吗？"

## 交互示例库

详细的自然语言触发词与 Skill 对应关系，请参考：
- [EXAMPLES.md](references/EXAMPLES.md) - 常用场景的 Prompt 示例。
- [WORKFLOWS.md](references/WORKFLOWS.md) - 复杂任务的交互路径设计。

---
