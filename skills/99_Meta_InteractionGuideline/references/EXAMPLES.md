# 常用场景 Prompt 示例 (Natural Language Examples)

本文件列举了如何通过简单的自然语言触发复杂的技能流。

## 1. 软件开发全生命周期 (SDLC)

| 用户输入 (Natural Language) | 预期触发的 Skill | 交互价值 |
| :--- | :--- | :--- |
| "我有个做 AI 记账的想法，帮我理理" | `brainstorming` | 自动进入苏格拉底式提问模式，明确需求 |
| "设计一个支持多租户的 REST API" | `api-design-principles` | 引入最佳实践，避免设计陷阱 |
| "把这个原型实现成 Next.js 页面" | `frontend-design` + `vercel-react-best-practices` | 产出美观且性能优化的代码 |
| "代码写完了，检查一下安全风险" | `Security Specialist` | 自动化安全扫描和审计 |

## 2. 文档与协作

| 用户输入 (Natural Language) | 预期触发的 Skill | 交互价值 |
| :--- | :--- | :--- |
| "总结这个 PDF 里的核心财务数据" | `pdf` + `xlsx` | 跨格式数据提取与处理 |
| "根据这个 PRD 写一份详细的测试用例" | `webapp-testing` | 自动生成测试脚本 |
| "帮我把刚才的修改提交了，记得规范 commit" | `git-workflow` | 自动生成 Conventional Commits |

## 3. 运维与部署

| 用户输入 (Natural Language) | 预期触发的 Skill | 交互价值 |
| :--- | :--- | :--- |
| "设置一下生产环境的自动化部署" | `gitops-workflow` | 编写 ArgoCD/Flux 配置文件 |
| "分析一下现在的数据库慢查询" | `Backend Database Expert` | SQL 优化与索引建议 |

## 技巧：如何写出更好的指令？

1. **动词 + 宾语 + 约束**: "重构 (动词) 这个函数 (宾语)，不要改变逻辑但要提升可读性 (约束)"。
2. **提及工具**: "用 Playwright (工具) 给登录页面写个测试"。
3. **反馈循环**: "我觉得刚才的方案太复杂了，能简单点吗？" (利用 AI 的上下文记忆)。
