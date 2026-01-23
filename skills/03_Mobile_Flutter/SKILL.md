---
name: Flutter Development Expert
description: 专注于构建高性能、可扩展且架构清晰的 Flutter 应用。涵盖整洁架构、高级状态管理和深度性能优化。
---

# Flutter Development Skills

这组技能专为追求工程质量的 Flutter 开发者设计。

## 包含的技能模块

### 1. [Flutter 整洁架构 (Clean Architecture)](./Flutter整洁架构.md)
- **核心价值**: 解耦业务逻辑与 UI，确保代码的可测试性和可维护性。
- **关键技术**: BLoC/Riverpod, Use Cases, Repository Pattern, Dependency Injection.
- **使用场景**: 大型项目启动、遗留代码重构。

### 2. [Flutter 性能优化 (Performance Optimization)](./Flutter性能优化.md)
- **核心价值**: 打造 60fps/120fps 的流畅体验。
- **关键技术**: 渲染管线分析, RepaintBoundary, 列表懒加载, 内存泄漏检测, Isolate 并发。
- **使用场景**: 解决卡顿掉帧、减少内存占用、优化启动速度。

### 3. [Flutter 状态管理 (State Management)](./Flutter状态管理.md)
- **核心价值**: 选择并实施最适合项目的状态管理方案。
- **关键技术**: BLoC (严谨), Riverpod (灵活), Provider (基础).
- **使用场景**: 复杂交互逻辑设计、跨组件状态共享。

### 4. [Flutter 测试与质量保证 (Testing & QA)](./Flutter测试与质量保证.md)
- **核心价值**: 建立多维度的测试体系，确保代码质量与稳定性。
- **关键技术**: 单元测试, Widget 测试, Golden 测试, Mocktail.
- **使用场景**: 核心业务逻辑验证、UI 回归测试。

### 5. [Flutter 工程化与部署 (DevOps & Deployment)](./Flutter工程化与部署.md)
- **核心价值**: 自动化开发流程，实现标准化的环境管理与发布。
- **关键技术**: Flavors, Fastlane, GitHub Actions, 错误监控。
- **使用场景**: 多环境管理、自动化 CI/CD 流程建设。

## 如何使用

- **架构设计**: "请参考 `Flutter整洁架构` 帮我设计这个电商 App 的目录结构和核心模块。"
- **性能诊断**: "列表滚动有点卡，请根据 `Flutter性能优化` 给我一些排查建议。"
- **自动化测试**: "请根据 `Flutter测试与质量保证` 为这个登录页面编写 Widget 测试用例。"
- **部署发布**: "我想配置 GitHub Actions 自动发布 Android 测试包，请参考 `Flutter工程化与部署` 给我建议。"

## 交互式开发 (Interactive Development)

在设计架构或进行性能调优时，如果不确定用户的具体业务场景或性能指标要求，请使用 `mcp-feedback-enhanced` (e.g., `ask_followup_question`) 主动询问。
