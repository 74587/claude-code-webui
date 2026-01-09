# Claude Code WebUI

A web-based version of Claude Code that allows you to deploy and use AI programming through a webUI on any device, compatible with local Claude Code configuration.

![ScreenShot](./assets//ScreenShot_1.png)

## Introduction

Claude Code WebUI enables users to interact with Claude Code through a browser.
This project uses React for the frontend and Bun as the backend runtime, implementing complete conversation management, real-time message streaming, permission control, and more.

**Note**: Currently, only macOS/Linux may be supported, so the usage instructions below are only for these two systems.

## Getting Started

Before installing this project, please ensure you have Bun and Claude Code installed. If you already have them, you can skip this step.

Install Bun:
```bash
curl -fsSL https://bun.sh/install | bash
```

Install Claude Code:
```bash
npm install -g @anthropic-ai/claude-code
```

Run Claude Code WebUI:

```
bunx @devagentforge/claude-code-webui@latest
```

The default port is 10086, if you want to change it, just set the env.

```bash
PORT=3000 bunx @devagentforge/claude-code-webui@latest 
```

Run from Source:

```bash
git clone https://github.com/DevAgentForge/claude-code-webui.git
cd claude-code-webui

bun i
bun run build
bun run start
```

**Note**

This project depends on the file `~/.claude/settings.json`, which is shared with Claude Code. Please configure Claude Code yourself.

## Core Features

### 🤖 AI Conversation
- Natural language interaction with Claude Code AI assistant
- Real-time streaming response display, showing AI-generated content word by word
- Markdown rendering support with code syntax highlighting
- Elegant loading animations and skeleton screen effects

### 📂 Session Management
- Create new sessions with custom working directories
- View historical session records
- Continue previous conversations
- Delete unwanted sessions
- Automatically save session history to local database

### 🔐 Permission Control
- Tool usage requires user authorization
- Users can choose to allow or deny execution of specific tools
- Support for bulk authorization policy configuration
- AskUserQuestion-type permission requests require manual user response

### 🎨 Modern Interface
- Responsive design for both mobile and desktop
- Light theme mimicking Claude's official interface
- Sidebar navigation for quick session switching
- Custom working directory selection support

## Technical Architecture

### Frontend Tech Stack
- **React 19** - UI Framework
- **TypeScript** - Type Safety
- **Tailwind CSS 4** - Atomic CSS Styling
- **Radix UI** - Unstyled Accessible Components
- **Zustand** - Lightweight State Management
- **React Markdown** - Markdown Rendering
- **Highlight.js** - Code Syntax Highlighting
- **Bun** - Build Tool and Development Server

### Backend Tech Stack
- **Bun** - JavaScript Runtime
- **Hono** - Lightweight Web Framework
- **bun:sqlite** - SQLite Database Driver
- **WebSocket** - Real-time Bidirectional Communication
- **@anthropic-ai/claude-agent-sdk** - Claude SDK

### Data Storage
- **SQLite** - Using WAL mode to store sessions and messages
- **Local File System** - Session History Persistence

## Development Mode

### Requirements
- [Bun](https://bun.sh) v1.0+

### Install Dependencies

```bash
bun install
```

### Development

```bash
bun run dev
```

### Production Build

```bash
bun run build
bun run start
```

### Environment Variables

```bash
# Server Port
PORT=10086

# Database Path
DB_PATH=./webui.db

# CORS Allowed Origins (comma-separated)
CORS_ORIGIN=*
```

### API Configuration

The project loads configuration through `src/claude-settings.ts`, sharing a configuration file with Claude Code. It supports the following environment variables:

- `ANTHROPIC_AUTH_TOKEN` - Anthropic API Token
- `ANTHROPIC_BASE_URL` - API Base URL
- `ANTHROPIC_MODEL` - Default Model
- `ANTHROPIC_DEFAULT_SONNET_MODEL` - Sonnet Model
- `ANTHROPIC_DEFAULT_OPUS_MODEL` - Opus Model
- `ANTHROPIC_DEFAULT_HAIKU_MODEL` - Haiku Model
- `API_TIMEOUT_MS` - API Timeout
- `CLAUDE_CODE_DISABLE_NONESSENTIAL_TRAFFIC` - Disable Non-essential Traffic

## Contributing

1. Fork this repository
2. Create your feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Create a Pull Request

## Acknowledgments

- [Anthropic](https://www.anthropic.com) - Claude AI Model
- [Bun](https://bun.sh) - JavaScript Runtime
- [React](https://react.dev) - UI Framework
- [Tailwind CSS](https://tailwindcss.com) - CSS Framework
- [Hono](https://hono.dev) - Web Framework
