# VibeCraft

> 装好一切，直接写代码。

VibeCraft 是 Claude Code 的桌面启动器与 Skill 商城。

打开 App，环境自动检测、供应商一键切换、插件统一管理、Skill 商城在线安装——从「想用 Claude Code」到「真的在用 Claude Code 写代码」，不到 5 分钟。

---

## 它解决什么

Claude Code 自己很强，但用户在真正写第一行代码之前要先扛过四道关：

1. **环境关**——Node.js / Git / Conda / Claude Code 本体得装齐
2. **供应商关**——官方 API / 国产模型 / 云服务商 / 聚合平台 / 第三方网关，配置散在 `~/.claude/settings.json` 里
3. **插件关**——MCP / Skills / Agents / 自定义脚本散落在各处，开关与更新都要手动
4. **生态关**——Skill 散落在 GitHub、npm、各种 marketplace，没有统一入口

VibeCraft 把这四件事压成一个桌面 App + 一个商城后端。

---

## 核心功能

### 环境检测与引导安装
启动自动检测 Node.js / Git / Conda / Claude Code。缺哪个给一键入口，Windows 便携版自动写 PATH。

### 供应商切换
内置 40+ 预设——Anthropic 官方、DeepSeek、Kimi、智谱、阿里云百炼、火山引擎、OpenRouter、AnyRouter、PackyCode 等。点一下切换，配置自动写入 `~/.claude/settings.json`。

### 插件管理
MCP 服务器 / Skills / Agents / 自定义插件在同一面板里启用、禁用、更新。

### Skill 商城（双 lane）
- **官方 lane**：本仓自营，免费 / 付费 / 激活码解锁
- **外部 lane**：实时聚合 GitHub / npm / ClawHub / SkillsMP / 等 5 个第三方来源，全部免费

### 本地 HTTP 代理
Anthropic ↔ OpenAI 格式互转。用 OpenAI 客户端的工具直接调 Claude，零代码迁移。

---

## 下载与安装

从 [Releases](https://github.com/Infinity-light/vibecraft-releases/releases) 下载对应平台：

- **Windows**：`VibeCraft-x.y.z-win-x64.exe`（免安装便携版）
- **macOS Apple Silicon**：`VibeCraft-x.y.z-mac-arm64.dmg`
- **macOS Intel**：`VibeCraft-x.y.z-mac-x64.dmg`

双击运行即可，更新会通过应用内提示完成。

---

## 技术栈

| 层 | 技术 |
|----|------|
| 桌面前端 | Vue 3 + TypeScript + Vite + Tailwind |
| 桌面后端 | Rust + Tauri v2 |
| 服务端 | NestJS v10 + TypeORM + PostgreSQL |
| 包管理 | pnpm workspaces（monorepo） |

**为什么是 Tauri**：体积 10MB（Electron 150MB），原生签名，启动毫秒级——桌面启动器对包体和速度敏感。

**为什么 NestJS**：商城后端要拆 ads / payments / entitlements / skills 多模块，NestJS 的 DI 与模块边界天然适配。

---

## 路线图（0.9.x → v1.0）

- 安装器稳定性（unix 权限位 / Windows PATH / Git + Miniconda 缺口）
- 4 槽工作目录面板重做
- Provider 默认 AIping 探活
- 鉴权流程清理（去 email_verified login gate / 修注册 deadlock）
- 本地 HTTP 代理稳定化
- 首次使用教程

---

## 反馈与社区

- **Bug / 建议**：[GitHub Issues](https://github.com/Infinity-light/vibecraft-releases/issues)
- **更新通知**：Watch 本仓库即可

---

## License

私有项目。安装包公开发布、源码暂不开放。
