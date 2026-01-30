# 常用技术栈组合 (Tech Stack Combos)

## 1. 现代化 Web 全栈 (The Modern Web)
- **前端**: Next.js (App Router) + Tailwind CSS + shadcn/ui
- **后端**: Next.js API Routes 或独立 FastAPI (Python)
- **数据库**: PostgreSQL (Prisma/Drizzle)
- **适用场景**: 需要 SEO、复杂交互、快速迭代的 SaaS 产品。

## 2. 轻量化与内容优先 (Lightweight & Content-First)
- **前端**: Astro + Tailwind CSS
- **后端**: Cloudflare Workers 或 Supabase (BaaS)
- **数据库**: Supabase (PostgreSQL) / Turso (SQLite)
- **适用场景**: 博客、文档、营销页面、简单的工具类应用。

## 3. 企业级复杂系统 (Enterprise Heavyweight)
- **前端**: React/Vue (Vite) + Ant Design / Element Plus
- **后端**: Spring Boot (Java) 或 NestJS (Node.js)
- **数据库**: MySQL/PostgreSQL + Redis (缓存) + RabbitMQ (消息队列)
- **适用场景**: 内部管理系统、ERP、CRM、对稳定性要求极高的业务。

## 4. 移动端优先 (Mobile-First)
- **前端**: Flutter (跨平台) 或 React Native
- **后端**: Firebase 或 Supabase
- **适用场景**: 需要原生体验的 App、跨端分发应用。

## 5. 数据密集型/实时系统 (Data-Intensive & Real-time)
- **前端**: React + TanStack Query + Socket.io
- **后端**: Go (Gin/Echo) 或 Node.js (Fastify)
- **数据库**: MongoDB / ClickHouse + Redis
- **适用场景**: 实时看板、协作工具、大数据分析平台。
