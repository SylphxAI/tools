<div align="center">

# MCP Tools 🛠️

**Modular MCP server toolkit - 12+ tools for AI agents**

[![Built with Turbo](https://img.shields.io/badge/Built%20with-Turbo-blue?style=flat-square&logo=turborepo)](https://turbo.build/)
[![License](https://img.shields.io/badge/License-ISC-green?style=flat-square)](https://github.com/SylphxAI/tools/blob/main/LICENSE)
[![pnpm](https://img.shields.io/badge/pnpm-workspace-orange?style=flat-square&logo=pnpm)](https://pnpm.io)

**Filesystem ops** • **Network requests** • **Data processing** • **RAG tools** • **PDF extraction**

[Quick Start](#-quick-start) • [Packages](#-packages) • [Development](#-development)

</div>

---

## 🚀 Overview

A comprehensive collection of modular tools designed for the Model Context Protocol (MCP), enabling AI agents to perform various operations efficiently.

**The Problem:**
```
Building MCP servers from scratch:
- Repetitive boilerplate code
- Inconsistent tool interfaces
- Scattered tool implementations
- No shared utilities or patterns
```

**The Solution:**
```
MCP Tools Monorepo:
- Modular tool architecture 🧩
- Consistent interfaces across tools 🎯
- Shared core utilities 📦
- MCP adaptors for easy integration ⚡
```

**Result: Build MCP servers faster with reusable, well-tested tool components.**

---

## 📦 Packages

### Core & Infrastructure

| Package | Description | Purpose |
|---------|-------------|---------|
| **tools-core** | Core utilities and type definitions | Base framework for all tools |
| **tools-adaptor-mcp** | MCP server integration adaptor | Convert tools to MCP servers |
| **tools-adaptor-vercel** | Vercel platform adaptor | Deploy tools on Vercel |

### Data Processing Tools

| Package | Description | MCP Server |
|---------|-------------|------------|
| **tools-json** | JSON parsing, validation, transformation | ✅ tools-json-mcp |
| **tools-xml** | XML parsing and processing | ✅ tools-xml-mcp |
| **tools-base64** | Base64 encoding/decoding | ✅ tools-base64-mcp |
| **tools-pdf** | PDF text extraction | ✅ tools-pdf-mcp |

### System & Network Tools

| Package | Description | MCP Server |
|---------|-------------|------------|
| **tools-filesystem** | File operations (read, write, list, search) | ✅ tools-filesystem-mcp |
| **tools-net** | Network requests (fetch, IP info, DNS) | ✅ tools-net-mcp |
| **tools-fetch-mcp** | Specialized fetch tool for MCP | ✅ Standalone MCP |
| **tools-hasher** | Hashing utilities (MD5, SHA, etc.) | ✅ tools-hasher-mcp |

### Specialized Tools

| Package | Description | MCP Server |
|---------|-------------|------------|
| **tools-rag** | Retrieval-Augmented Generation tools | ✅ tools-rag-mcp |
| **tools-wait** | Delay and timing utilities | ✅ tools-wait-mcp |

**Pattern**: Most tools follow the `tools-{name}` + `tools-{name}-mcp` pattern, separating core logic from MCP server implementation.

---

## 🎯 Use Cases

### AI Agent Development
Build powerful MCP servers for AI assistants:
- **File management** - Read, write, search files
- **Web scraping** - Fetch and process web content
- **Document processing** - Extract text from PDFs
- **Data transformation** - JSON/XML/Base64 operations

### Rapid Prototyping
Quickly assemble MCP servers from pre-built tools:
- **Mix and match** - Combine tools as needed
- **Consistent interfaces** - Predictable tool behavior
- **Shared utilities** - Less code duplication

### Production Deployment
Deploy robust MCP servers:
- **Vercel adaptor** - Serverless deployment
- **Turborepo** - Optimized builds
- **Type-safe** - Full TypeScript support

---

## 🚀 Quick Start

### Prerequisites

- **Node.js** - Latest LTS version (check `.nvmrc` if available)
- **pnpm** - Version specified in `package.json` `packageManager` field

### Installation

```bash
# Clone the repository
git clone https://github.com/SylphxAI/tools.git
cd tools

# Install dependencies
pnpm install
```

### Development Workflow

```bash
# Build all packages
pnpm build

# Build continuously during development
pnpm build:watch

# Run linting
pnpm lint

# Run tests (build first)
pnpm test
```

---

## 🛠️ Tech Stack

| Component | Technology |
|-----------|------------|
| **Monorepo** | Turborepo |
| **Package Manager** | pnpm workspaces |
| **Language** | TypeScript |
| **Code Quality** | Biome (50x faster than ESLint) |
| **Testing** | Vitest |
| **MCP Protocol** | Model Context Protocol |

---

## 💡 Architecture

### Tool Structure

Each tool follows a consistent pattern:

```
packages/
├── tools-{name}/          # Core tool logic
│   ├── src/
│   │   ├── index.ts       # Tool implementation
│   │   └── types.ts       # TypeScript types
│   └── package.json
└── tools-{name}-mcp/      # MCP server wrapper
    ├── src/
    │   └── index.ts       # MCP server entry
    └── package.json
```

### Benefits

- **Separation of concerns** - Core logic separate from MCP protocol
- **Reusability** - Use tools outside of MCP context
- **Testability** - Test core logic independently
- **Flexibility** - Easy to create alternative adaptors

---

## 📖 Package Details

### Core Utilities

**tools-core**
```typescript
import { defineTool } from '@sylphx/tools-core'

const myTool = defineTool({
  name: 'my-tool',
  description: 'Does something useful',
  schema: { /* Zod schema */ },
  execute: async (input) => { /* implementation */ }
})
```

### MCP Adaptor

**tools-adaptor-mcp**
```typescript
import { createMCPServer } from '@sylphx/tools-adaptor-mcp'
import { myTool } from '@sylphx/tools-mytool'

const server = createMCPServer({
  tools: [myTool],
  name: 'My MCP Server',
  version: '1.0.0'
})
```

---

## 🔧 Development

### Building Packages

```bash
# Build all packages
pnpm build

# Build specific package
pnpm --filter @sylphx/tools-filesystem build

# Watch mode for development
pnpm build:watch
```

### Code Quality

```bash
# Lint all packages
pnpm lint

# Fix linting issues
pnpm lint:fix

# Format code
pnpm format
```

### Testing

```bash
# Run all tests
pnpm test

# Run tests for specific package
pnpm --filter @sylphx/tools-json test

# Watch mode
pnpm test:watch
```

---

## 📋 Creating a New Tool

### Step 1: Create Core Package

```bash
# Create package directory
mkdir -p packages/tools-newtool/src

# Create package.json
cat > packages/tools-newtool/package.json <<EOF
{
  "name": "@sylphx/tools-newtool",
  "version": "1.0.0",
  "type": "module",
  "main": "./dist/index.js",
  "types": "./dist/index.d.ts"
}
EOF
```

### Step 2: Implement Tool

```typescript
// packages/tools-newtool/src/index.ts
import { defineTool } from '@sylphx/tools-core'
import { z } from 'zod'

export const newTool = defineTool({
  name: 'new-tool',
  description: 'A new tool',
  schema: z.object({
    input: z.string()
  }),
  execute: async ({ input }) => {
    // Implementation
    return { result: `Processed: ${input}` }
  }
})
```

### Step 3: Create MCP Server

```bash
# Create MCP package
mkdir -p packages/tools-newtool-mcp/src

# Create server
cat > packages/tools-newtool-mcp/src/index.ts <<EOF
import { createMCPServer } from '@sylphx/tools-adaptor-mcp'
import { newTool } from '@sylphx/tools-newtool'

const server = createMCPServer({
  tools: [newTool],
  name: 'New Tool MCP Server',
  version: '1.0.0'
})

server.start()
EOF
```

---

## 🌐 Deployment

### Vercel Deployment

```bash
# Using the Vercel adaptor
pnpm --filter @sylphx/tools-adaptor-vercel build

# Deploy
vercel
```

### Docker Deployment

```dockerfile
FROM node:lts-alpine
WORKDIR /app

# Install pnpm
RUN npm install -g pnpm

# Copy package files
COPY package.json pnpm-lock.yaml pnpm-workspace.yaml ./
COPY packages ./packages

# Install dependencies
RUN pnpm install --frozen-lockfile

# Build
RUN pnpm build

# Start MCP server
CMD ["pnpm", "start"]
```

---

## 🗺️ Roadmap

**✅ Completed**
- [x] Core tool framework
- [x] MCP adaptor
- [x] Filesystem tools
- [x] Network tools
- [x] Data processing tools (JSON, XML, Base64, PDF)
- [x] Hashing utilities
- [x] RAG tools
- [x] Turborepo monorepo setup

**🚀 Planned**
- [ ] Image processing tools
- [ ] Database adaptors (PostgreSQL, MongoDB)
- [ ] Authentication tools
- [ ] Caching utilities
- [ ] Monitoring and logging tools
- [ ] GraphQL tools
- [ ] WebSocket tools

---

## 🤝 Contributing

Contributions are welcome! Please follow these guidelines:

1. **Fork the repository**
2. **Create a feature branch** - `git checkout -b feature/my-tool`
3. **Follow the tool pattern** - Use existing tools as reference
4. **Add tests** - Ensure good coverage
5. **Update documentation** - Add your tool to this README
6. **Submit a pull request**

### Code Style

- Use **TypeScript** for all code
- Follow **Biome** formatting rules
- Write **comprehensive tests**
- Add **JSDoc comments** for public APIs

---

## 🤝 Support

[![GitHub Issues](https://img.shields.io/github/issues/SylphxAI/tools?style=flat-square)](https://github.com/SylphxAI/tools/issues)

- 🐛 [Bug Reports](https://github.com/SylphxAI/tools/issues)
- 💬 [Discussions](https://github.com/SylphxAI/tools/discussions)
- 📧 [Email](mailto:hi@sylphx.com)

**Show Your Support:**
⭐ Star • 👀 Watch • 🐛 Report bugs • 💡 Suggest features • 🔀 Contribute

---

## 📄 License

ISC © [Sylphx](https://sylphx.com)

---

## 🙏 Credits

Built with:
- [Turborepo](https://turbo.build) - Monorepo build system
- [pnpm](https://pnpm.io) - Fast package manager
- [Biome](https://biomejs.dev) - Code quality tools
- [TypeScript](https://typescriptlang.org) - Type safety

Special thanks to the MCP community ❤️

---

<p align="center">
  <strong>Modular. Reusable. Production-ready.</strong>
  <br>
  <sub>The MCP toolkit that scales with your needs</sub>
  <br><br>
  <a href="https://sylphx.com">sylphx.com</a> •
  <a href="https://x.com/SylphxAI">@SylphxAI</a> •
  <a href="mailto:hi@sylphx.com">hi@sylphx.com</a>
</p>
