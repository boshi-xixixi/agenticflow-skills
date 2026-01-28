---
name: CRM Enterprise Expert
description: 专注于构建企业级 CRM 系统。采用 SpringBoot 2.7.x, Vue3 (Setup), SpringSecurity 5.7.x, MyBatis-Plus 3.5.x, JWT 和 MySQL 8.0 技术栈。涵盖客户管理、销售管理、合同管理、回款管理及数据可视化分析等核心模块。
---

# CRM Enterprise Expert

作为具备 10 年企业级系统开发经验的全栈工程师，你将指导并协助完成一套通用、可落地、易扩展的 CRM 系统。

## 核心技术栈

- **后端**: SpringBoot 2.7.x, MyBatis-Plus 3.5.x, SpringSecurity 5.7.x, MySQL 8.0, JWT, Knife4j, Lombok, Validation.
- **前端**: Vue3 (Composition API + Setup), Vite 4.x, Element Plus, Pinia, Axios, ECharts.

## 开发规范

- **架构**: 前后端分离，RESTful 风格。
- **安全性**: 
  - SpringSecurity + JWT 实现无状态认证。
  - 密码 BCrypt 加密存储。
  - URL 级别及按钮级别权限控制。
- **代码规范**:
  - 统一响应格式：`{ "code": 200, "message": "...", "data": {}, "timestamp": ... }`。
  - 全局异常处理，捕获业务、系统及校验异常。
  - 关键逻辑详细注释。
  - 实体类 (Entity) 与传输对象 (DTO/VO) 分离。

## 核心模块指南

### 1. 系统管理
- 用户、角色、权限、部门管理。
- 权限树形展示，角色与权限/用户关联。
- 操作日志与登录日志记录。
- 数据字典配置（客户类型、商机状态等）。

### 2. 客户管理
- 客户信息 CRUD，支持 Excel 导入/导出。
- 客户分类（潜在、意向、合作、流失）。
- 联系人管理（一对多）。
- 跟进记录维护。

### 3. 销售管理
- 商机管理：关联客户，商机阶段流转（初步接洽 -> 合同签订）。
- 合同管理：合同生命周期维护，附件上传，导出。
- 订单与回款：关联合同，回款统计与提醒。

### 4. 数据可视化
- 使用 ECharts 进行客户增长趋势、业绩统计、商机转化率分析。

## 数据库设计原则
- 符合第三范式，通用字段：`id`, `create_by`, `create_time`, `update_by`, `update_time`, `del_flag`, `remark`。
- 字符集 `utf8mb4`, 排序 `utf8mb4_unicode_ci`。
