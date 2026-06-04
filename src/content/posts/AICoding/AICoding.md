---
title: AI Coding 从入门到夯
published: 2026-04-30
pinned: true
description: AI Coding 基础入门
tags: [AI Coding, Claude Code, Codex, OpenCode]
category: AI
draft: false
---
## 一、对 AI 编程的认知

### 1. AI Coding 是什么

   是指**专业程序员在自身技术能力之上**，用 AI 辅助写代码、查问题、做优化。Vibe Coding 则是**非技术人员用自然语言**来描述想法，完成小需求。

高效的开发者会使用 AI 工具辅助日常工作。AI 可以帮助你：
- **加速学习曲线**：将复杂概念分解为易懂的小块
- **提高编码效率**：自动补全、代码生成、重构建议
- **减少重复劳动**：快速生成样板代码和测试用例
- **实时问题解决**：即时获得调试建议和错误修复
- **探索新技术**：快速了解陌生的框架和语言

### 2. 程序员的角色定位

**以前：**
现实世界（产品经理） <--> 沟通者（程序员） <--> 计算机运行时
**现在：**
现实世界（产品经理） <--> 沟通者（程序员）<--> 技术语言 <--> AI <--> 计算机运行时
因此，在现在这个大环境下，学会如何正确高效的使用 AI 是非常有必要的。
![](..\images\AI\ai-coding\d1.avif)
对于使用 AI 比较生疏的，可以参考以下文章 ↓
暂时无法在飞书文档外展示此内容

> 入门：安装 Codex、Claude Code或者 Trae、Cursor 等 AI Coding 插件/软件
> 进阶：使用 MCP、Skills、SubAgent

## 二、搭建 AI 编程环境
### 1. 最小环境
你需要的最小环境：
- Git（看 diff、回滚、提交）
- Node.js（Claude/Gemini/Codex 三套 CLI 都用得到；建议 Node 20+，更推荐 Node 22）
- 使用 cc-switch 统一管理中转

#### 1.1 安装 Git
**Git**：https://git-scm.com/install/windows
详细教程参考 https://blog.csdn.net/mukes/article/details/115693833 即可

```bash
git --version #通过这个来验证git是否已经成功安装
```

如果你要使用 AI Coding 那么 Git 是非常有必要安装的，因为可以回退版本，即使 AI 写错了，也能够快速回到上一个版本，如果不会 Git 那么你也可以让 AI 来帮你回退版本，使用场景分别为：

- 让 AI 帮你比较代码的历史版本差异
- 回退版本，如：请使用 git 帮我回退到上一个版本

#### 1.2 安装 Node.js
**Node.js**：https://nodejs.org/zh-cn
官网包一路往下点下一步即可（建议别安装在 C盘），或者可以使用 NVM 来管理 nodejs（推荐）
**NVM**：https://nvm.uihtm.com/
安装教程详细看官方文档即可，也可以在 CSDN 上搜索安装教程，官网安装的基本上自动配置环境变量。

```bash
#验证nodejs是否成功安装
node -v 
npm -v 
```
### 2. 简易上手版

在 VS Code 中安装 OpenCode、Claude Code、Codex 插件
![](..\images\AI\ai-coding\d2.avif)
此时安装完，是无法使用的，要么使用官方账号登录，要么使用第三方中转，这里推荐使用 [**cc-switch**](https://ccswitch.io/zh/) 来管理 AI 工具，这是一个开源软件，可以统一管理 AI 工具的供应商以及 Skills、MCP 等。
![点击加号](..\images\AI\ai-coding\d3.avif)
安装完上述插件后，在 cc-switch 中直接添加并且配置 URL 和 api key 之后即可使用
![选择供应商](..\images\AI\ai-coding\d4.avif)
![配置 API](..\images\AI\ai-coding\d5.avif)
只要把红色框框的都填写完，就可以点击添加，这时候重启 VS Code 就可以发现，你的 CLI 工具可以打开了。

### 3. 稳定主流版

- VS Code 以及插件，或 终端运行 CLI

#### 3.1 安装 CLI

使用 npm ，先前安装的 nodejs 的作用来了

- 安装 Claude Code

```bash
npm install -g @anthropic-ai/claude-code #已弃用
claude --version #检查是否已经安装成功
```

Windows PowerShell:
```plain
irm https://claude.ai/install.ps1 | iex
```

- 安装 Codex

```bash
npm i -g @openai/codex # 也可以安装桌面应用
codex --version #检查是否已经安装成功
```

最后，使用图形化开源软件 cc-swtich 来配置 API
在终端输入 claude 或者 codex 即可呼起对应的 CLI
![](..\images\AI\ai-coding\d6.avif)

#### 3.2 安装桌面端工具（推荐）
**推荐理由**：方便管理对话

均建议使用 cc-switch 代理
OpenCode
https://opencode.ai/zh
开源，并且内置支持 deepseek v4 flash 免费版；支持其他 AI 使用

Claude Code
https://www.anthropic.com/product/claude-code
支持其他 AI 使用，建议搭配 cc-switch 使用

Codex
https://chatgpt.com/zh-Hans-CN/codex
支持其他 AI 使用，建议搭配 cc-switch 使用

## MCP 与 Skills 的使用

为了更好的使用 MCP 与 Skills，首先我们要先了解二者分别是什么意思，二者之间的区别是什么。

### 1. MCP 是什么？
MCP 是 Anthropic 推出的一个开放协议，让 AI 模型可以连接到外部数据源和工具。可以把它理解为 AI 的"USB 接口"——一个标准化的方式来让 Agent 访问外部系统。

简单来说就是：MCP 是“连接协议”，让模型能访问外部工具和数据，如数据库、API、文件系统等。

### 2. Skills 是什么？
Skills 是 Anthropic 公司发布的一个跨平台可移植性的开发标准，是一个可调用工作流/提示模板，本质上是预定义的 prompt + 工作模式。每个 Skill 封装了一类任务的最佳实践。

简单来说就是：Skills 就是一个“方法论”，模块化、可复用的任务流程和操作规范，封装了专业知识、工作方法和执行步骤。

### 3. MCP 与 Skills 之间的区别

| 对比项         | MCP                                            | Skills                                                   |
| -------------- | ---------------------------------------------- | -------------------------------------------------------- |
| 本质           | 一套协议，让 AI 连接外部工具、数据源、服务     | 一组可复用的任务说明和资源                               |
| 解决什么问题   | “让模型能调用东西”                             | “让模型按固定方法做事”                                   |
| 典型内容       | 工具、资源、提示词、远程服务、本地进程         | `SKILL.md`、脚本、参考资料、模板                         |
| 适合场景       | 查文档、连 Figma、控浏览器、查数据库、调 API   | 写论文格式、简历优化、代码审查流程、前端设计规范         |
| 安装方式       | 配置 MCP server，常见为 `npx`、HTTP URL、OAuth | 放到 Skills 目录、使用 Agent 工具自带的插件商城下载 |
| 是否能执行动作 | 可以，MCP server 暴露工具给模型调用            | 本身主要是说明书；可附带脚本，由 Agent 按说明运行        |
| 安全重点       | 远程/本地工具可能读取数据或执行操作            | 技能说明可能影响模型行为，也可能附带脚本                 |


> 注意：两者互补而非替代，MCP 是“工具”，Skills 是“方法论”。