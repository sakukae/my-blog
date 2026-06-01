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

   是指专业程序员在自身技术能力之上，用 AI 辅助写代码、查问题、做优化。Vibe Coding 则是非技术人员用自然语言来描述想法，完成小需求。

高效的开发者会使用 AI 工具辅助日常工作。AI 可以帮助你：

- 加速学习曲线：将复杂概念分解为易懂的小块
- 提高编码效率：自动补全、代码生成、重构建议
- 减少重复劳动：快速生成样板代码和测试用例
- 实时问题解决：即时获得调试建议和错误修复
- 探索新技术：快速了解陌生的框架和语言

### 2. 程序员的角色定位

**以前：**
现实世界（产品经理） <--> 沟通者（程序员） <--> 计算机运行时
**现在：**
现实世界（产品经理） <--> 沟通者（程序员）<--> 技术语言 <--> AI <--> 计算机运行时
因此，在现在这个大环境下，学会如何正确高效的使用 AI 是非常有必要的。
![](.\images\AI\ai-coding\d1.avif)
对于使用 AI 比较生疏的，可以参考以下文章 ↓
暂时无法在飞书文档外展示此内容

> 入门：安装 Codex、Claude Code或者 Trae、Cursor 等 AI Coding 插件/软件
> 进阶：使用 mcp、skills、subAgent

## 二、搭建 AI 编程环境

你需要的最小环境：
- Git（看 diff、回滚、提交）
- Node.js（Claude/Gemini/Codex 三套 CLI 都用得到；建议 Node 20+，更推荐 Node 22）
- 使用 cc-switch 统一管理中转

### 1. 简易上手版

在 VS Code 中安装 Claude Code、Codex 插件
![](.\images\AI\ai-coding\d2.avif)
此时安装完，是无法使用的，要么使用官方账号登录，要么使用第三方中转，这里推荐使用 cc-switch 来管理 AI 工具，这是一个开源软件，可以可视化管理 AI 工具的供应商以及 skills、mcp 等。
![](.\images\AI\ai-coding\d3.avif)
安装完上述插件后，在 cc-switch 中直接添加并且配置 URL 和 api key 之后即可使用
![](.\images\AI\ai-coding\d4.avif)
![](.\images\AI\ai-coding\d5.avif)
只要把红色框框的都填写完，就可以点击添加，这时候重启 VS Code 就可以发现，你的 CLI 工具可以打开了。

### 2. 稳定主流版

- VS Code 以及插件，或 终端运行 CLI

2.1 安装 Git
暂时无法在飞书文档外展示此内容
详细教程参考 https://blog.csdn.net/mukes/article/details/115693833 即可

```Bash
git --version #通过这个来验证git是否已经成功安装
```

如果你要使用 AI Coding 那么 Git 是非常有必要安装的，因为可以回退版本，即使 AI 写错了，也能够快速回到上一个版本，如果不会 Git 那么你也可以让 AI 来帮你回退版本，使用场景分别为：

- 让 AI 帮你比较代码的历史版本差异
- 回退版本，如：请使用 git 帮我回退到上一个版本

### 2.2 安装 nodejs

暂时无法在飞书文档外展示此内容
官网包一路往下点下一步即可（建议别安装在 C盘），或者可以使用 nvm 来管理 nodejs（推荐）
暂时无法在飞书文档外展示此内容
安装教程详细看官方文档即可，也可以在 CSDN 上搜索安装教程，官网安装的基本上自动配置环境变量。

```Bash
#验证nodejs是否成功安装
node -v 
npm -v 
```

### 2.3 安装 CLI

使用 npm ，先前安装的 nodejs 的作用来了

- 安装 Claude Code

```Bash
npm install -g @anthropic-ai/claude-code #已弃用，建议查看官网
claude --version #检查是否已经安装成功
```

直接复制以下的内容到终端运行即可：

```Plain
& ([scriptblock]::Create((New-Object Net.WebClient).DownloadString("https://claude-zh.cn/scripts/install.ps1")))
```

- 安装 Codex

```Bash
npm i -g @openai/codex # 也可以安装桌面应用
codex --version #检查是否已经安装成功
```

最后，使用图形化开源软件 cc-swtich 来配置 API
在终端输入 claude 或者 codex 即可呼起对应的 CLI
[图片]

### 2.4 安装桌面端工具（推荐）

均建议使用 cc-switch 代理
OpenCode
开源，并且内置支持 deepseek v4 flash 免费版；支持其他 AI 使用
暂时无法在飞书文档外展示此内容

Claude Code
支持其他 AI 使用，建议搭配 cc-switch 使用
暂时无法在飞书文档外展示此内容

Codex
仅支持 GPT
暂时无法在飞书文档外展示此内容
