<p align="center">
  <img src="web/public/logo.svg" width="96" alt="infinite-canvas-agent logo">
</p>

<h1 align="center">无限画布 Agent (infinite-canvas-agent)</h1>

<p align="center">
  基于 <a href="https://github.com/basketikun/infinite-canvas">infinite-canvas</a> 改造 · Agent 主导的音视频工作流
</p>

<p align="center">
  <a href="docs/content/docs/overview/quick-start.mdx">快速开始</a> · <a href="docs/content/docs/overview/features.mdx">功能介绍</a> · <a href="docs/content/docs/canvas/canvas-node-manual.mdx">画布节点操作手册</a> · <a href="docs/content/docs/canvas/canvas-shortcuts.mdx">画布快捷键</a> · <a href="canvas-agent/README.md">本地 Canvas Agent</a> · <a href="docs/content/docs/progress/todo.mdx">待办事项</a>
</p>

本仓库基于开源项目 [basketikun/infinite-canvas](https://github.com/basketikun/infinite-canvas) 改造，目标是把无限画布从本地创作工作台，演进为**可对外提供服务、以 Agent 为主导的音视频工作流平台**。

改造方向：

- **对外服务**：面向多用户部署和接入，而不仅是浏览器本地单人工作台。
- **Agent 主导**：由本地 / 远程 Agent 编排画布节点、调用工具、驱动生成流程。
- **音视频工作流**：围绕图片、音频、视频节点，把生成、剪辑、引用和迭代串成可复用流程。

> [!CAUTION]
> 项目目前仍处于开发阶段，接口、数据格式和对外服务能力都可能随时调整，不保证历史数据兼容。请勿用于生产环境。

上游原项目是一款面向图片创作的开源无限画布工作台。本仓库保留画布编排、AI 生成、节点连线和本地 Agent 等基础能力，并在此之上继续改造服务形态与音视频工作流。

## 核心功能

当前可用能力仍主要来自上游画布，后续会按对外服务和 Agent 工作流继续演进：

- 无限画布：多画布项目、节点拖拽缩放、连线、小地图、撤销重做、导入导出。
- AI 创作：浏览器前台直连 OpenAI 兼容接口，支持文生图、图生图、参考图编辑、文本问答、音频和视频生成。
- 画布助手：围绕选中节点和上游节点对话、生图，并把结果插回画布。
- 本地 Agent：通过本机 Canvas Agent 连接 Codex / Claude Code，让 Agent 通过 MCP 操作当前画布。
- 音视频节点：视频生成、参考素材、任务续查、视频截帧；音频生成与节点引用。
- 插件系统：支持通过 URL 动态安装远程节点插件，并提供 TypeScript SDK 自行开发画布节点插件。

完整功能说明见 [功能介绍](docs/content/docs/overview/features.mdx)。

## 快速开始

当前版本仍以后端直连浏览器本地配置为主，对外服务能力还在开发中。

### 本地开发

```bash
git clone git@github.com:Daydreamer8FuBowen/infinite-canvas-agent.git
cd infinite-canvas-agent
cd web
bun install
bun run dev
```

启动后访问 `http://localhost:3000`。首次打开后进入右上角配置，填入自己的 OpenAI 兼容 `Base URL` 和 `API Key`。

### 本地 Canvas Agent

如需让 Codex / Claude Code 操作画布：

```bash
cd canvas-agent
npm install
npm run build
node dist/index.js
```

启动后在画布右上角点击 `Agent`，填入本机地址和 token 即可连接。详见 [本地 Canvas Agent](canvas-agent/README.md)。

## 致谢

本项目基于 [basketikun/infinite-canvas](https://github.com/basketikun/infinite-canvas) 改造。感谢原作者与社区贡献者。
