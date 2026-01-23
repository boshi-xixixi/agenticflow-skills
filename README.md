# 🌊 AgenticFlow

<div align="center">

![AgenticFlow](https://img.shields.io/badge/Agentic-Flow-blue?style=for-the-badge&logo=openai)
![License](https://img.shields.io/badge/license-MIT-green?style=for-the-badge)
![IDE Support](https://img.shields.io/badge/IDE-Trae%20|%20Cursor%20|%20VS%20Code-purple?style=for-the-badge)

**The Universal Knowledge Base for the AI Agent Era**

[English](README_EN.md) | [中文](README.md)

</div>

---

## 🚀 什么是 AgenticFlow?

AgenticFlow 是一个**跨 IDE、跨平台**的标准化技能库，专为 AI Agent（如 Trae, Cursor, Copilot）设计。它不仅仅是一堆文档，而是经过结构化设计的**上下文（Context）**，旨在让 AI 在软件开发生命周期的每一个环节都能展现出专家级的水平。

从**产品脑暴**到**架构设计**，从**全栈开发**到**自动化测试**，AgenticFlow 提供了一套开箱即用的“大脑扩展包”。

## 🌟 核心特性 (Why Use This?)

- **🦄 万能适配 (Universal Adapter)**
  - **Trae Native**: 完美兼容 `.trae/Skills` 架构，即插即用。
  - **Cursor Ready**: 内置 `.cursorrules`，让 Cursor 瞬间理解项目全貌。
  - **VS Code Friendly**: 优化的工作区配置，配合 Copilot 使用更佳。

- **📚 全栈覆盖 (Full-Stack Mastery)**
  - 覆盖产品 (PM)、设计 (Design)、开发 (Dev)、测试 (QA)、运维 (DevOps) 全流程。
  - 包含 React, Flutter, Python, Node.js, SQL 等主流技术栈的最佳实践。

- **⚡️ 生产力倍增 (Productivity Boost)**
  - 不再需要重复告诉 AI "如何写好 React 代码" 或 "如何做 SQL 优化"。
  - 直接引用相关 Skill，AI 立即切换到专家模式。

## 📂 技能地图 (Skill Map)

所有技能均位于 `skills/` 目录下，按角色和领域精心分类：

| 领域 | 目录 | 描述 |
|------|------|------|
| **🧠 Product** | `01_ProductManager_*` | 需求分析、脑暴、PRD 生成模式 |
| **🏗 Architecture** | `02_Architect_*` | API 设计规范、系统架构决策 |
| **🎨 Design** | `02_Designer_*` | 前端实现规范、Web 设计指南 |
| **💻 Development** | `03_Developer_*` | **React 最佳实践**、Artifact 构建器 |
| **📱 Mobile** | `03_Mobile_*` | **Flutter** 工程化、性能优化、架构 |
| **🧪 Testing** | `04_Tester_*` | 浏览器自动化测试、测试策略 |
| **🔧 Backend** | `05_Backend_*` | Node.js/Python 模式、DB 优化、**MCP 服务器构建** |
| **🚀 DevOps** | `05_DevOps_*` | Git 工作流、GitOps 实践 |
| **📄 Office** | `06_Office_*` | Word/Excel/PDF 自动化处理与解析 |

## 🛠️ IDE 配置指南

### 1. Trae 用户 🟦
AgenticFlow 包含原生 `.trae/Skills` 目录。
- **使用方式**: 直接打开本项目，Trae 的 AI 助手会自动加载所有技能。
- **自定义**: 你可以在 `.trae/config` 中调整偏好（如果有）。

### 2. Cursor 用户 ⬛️
项目根目录包含 `.cursorrules` 文件。
- **使用方式**: 在 Chat 中输入 `@Files` 引用特定的 `SKILL.md`。
- **自动感知**: Cursor 会根据 `.cursorrules` 自动理解目录结构映射。

### 3. VS Code / Windsurf 用户 🟦
- **VS Code**: 推荐安装 GitHub Copilot。将 `skills/` 下的相关文档作为 Context 发送给 Chat。
- **Windsurf**: 类似于 Cursor，可手动引用 `skills/` 下的规则文件。

## 📦 构建与扩展

部分高级模块（如 React Best Practices）包含构建脚本：

```bash
# 生成 React 最佳实践聚合文档
cd skills/03_Developer_ReactBestPractices
npm install && npm run build
```

## 🤝 参与贡献

AgenticFlow 是一个开源项目，我们需要你的智慧！
请阅读 [CONTRIBUTING.md](CONTRIBUTING.md) 了解如何提交新的技能。

## 🔍 Keywords & Topics

> **Core**: AI Agents, Agentic Workflow, Context Management, Prompt Engineering, SOP, Best Practices
> **Tech Stack**: React, Flutter, Python, Node.js, TypeScript, SQL, Docker, GitOps
> **Tools**: Trae IDE, Cursor, VS Code, GitHub Copilot, Windsurf, MCP (Model Context Protocol)
> **Domains**: RAG Pipelines, LLM Ops, System Design, Automation, Testing, Office Open XML

## 📄 License

MIT License © 2024 AgenticFlow Contributors
