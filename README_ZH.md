# Claude Code WebUI

网页版的 Claude Code，允许您部署后在任意设备通过网页进行 AI 编程，兼容本地 Claude Code 配置。  

![ScreenShot](./assets//ScreenShot_1.png)

## 项目简介

Claude Code WebUI 让用户可以通过浏览器与 Claude Code 进行对话。  
该项目使用 React 构建前端，Bun 作为后端运行时，实现了完整的会话管理、实时消息流、权限控制等功能。

**注意**：目前可能仅支持 macOS/Linux，所以下面的使用方法也仅针对这两类系统。

## 开始使用

在开始安装本项目之前，请先确保安装了 Bun 环境与 Claude Code。

安装 Bun， 如果已有，请忽略。
```
curl -fsSL https://bun.sh/install | bash
```

安装 Claude Code， 如果已有，请忽略。
```
npm install -g @anthropic-ai/claude-code
```

**注意**

本项目依赖文件 `~/.claude/settings.json`， 与 Claude Code 共享此配置，请自行配置Claude Code。

## 核心功能

### 🤖 AI 对话
- 支持与 Claude Code AI 助手进行自然语言交互
- 实时流式响应显示，逐字展示 AI 生成的内容
- 支持 Markdown 渲染，包括代码高亮显示
- 优雅的加载动画和骨架屏效果

### 📂 会话管理
- 创建新会话，选择工作目录
- 查看历史会话记录
- 继续之前的对话
- 删除不需要的会话
- 自动保存会话历史到本地数据库

### 🔐 权限控制
- 工具使用需要用户授权
- 用户可以选择允许或拒绝特定工具的执行
- 支持批量授权策略配置
- AskUserQuestion 类型的权限请求需要用户手动响应

### 🎨 现代化界面
- 响应式设计，支持移动端和桌面端
- 仿 Claude 官方界面的浅色主题
- 侧边栏导航，快速切换会话
- 支持自定义工作目录选择

## 技术架构

### 前端技术栈
- **React 19** - UI 框架
- **TypeScript** - 类型安全
- **Tailwind CSS 4** - 原子化 CSS 样式
- **Radix UI** - 无样式可访问性组件
- **Zustand** - 轻量级状态管理
- **React Markdown** - Markdown 渲染
- **Highlight.js** - 代码语法高亮
- **Bun** - 打包工具和开发服务器

### 后端技术栈
- **Bun** - JavaScript 运行时
- **Hono** - 轻量级 Web 框架
- **bun:sqlite** - SQLite 数据库驱动
- **WebSocket** - 实时双向通信
- **@anthropic-ai/claude-agent-sdk** - Claude SDK

### 数据存储
- **SQLite** - 使用 WAL 模式存储会话和消息
- **本地文件系统** - 会话历史持久化

## 开发模式

### 环境要求
- [Bun](https://bun.sh) v1.0+

### 安装依赖

```bash
bun install
```

### 开发

```bash
bun run dev
```


### 生产构建

```bash
bun run build
bun run start
```

### 环境变量

```bash
# 服务器端口
PORT=10086

# 数据库路径
DB_PATH=./webui.db

# CORS 允许的来源（逗号分隔）
CORS_ORIGIN=*
```

### API 设置

项目通过 `src/claude-settings.ts` 加载 Claude 相关配置，支持以下环境变量：

- `ANTHROPIC_AUTH_TOKEN` - Anthropic API 令牌
- `ANTHROPIC_BASE_URL` - API 基础 URL
- `ANTHROPIC_MODEL` - 默认模型
- `ANTHROPIC_DEFAULT_SONNET_MODEL` - Sonnet 模型
- `ANTHROPIC_DEFAULT_OPUS_MODEL` - Opus 模型
- `ANTHROPIC_DEFAULT_HAIKU_MODEL` - Haiku 模型
- `API_TIMEOUT_MS` - API 超时时间
- `CLAUDE_CODE_DISABLE_NONESSENTIAL_TRAFFIC` - 禁用非必要流量

## 贡献指南

1. Fork 本仓库
2. 创建功能分支 (`git checkout -b feature/amazing-feature`)
3. 提交更改 (`git commit -m 'Add amazing feature'`)
4. 推送到分支 (`git push origin feature/amazing-feature`)
5. 创建 Pull Request

## 致谢

- [Anthropic](https://www.anthropic.com) - Claude AI 模型
- [Bun](https://bun.sh) - JavaScript 运行时
- [React](https://react.dev) - UI 框架
- [Tailwind CSS](https://tailwindcss.com) - CSS 框架
- [Hono](https://hono.dev) - Web 框架
