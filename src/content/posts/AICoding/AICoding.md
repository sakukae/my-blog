---
title: AI Coding 基础入门教程
published: 2026-06-01
pinned: true
description: 包括 Agent、MCP、Skills 的安装与使用
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
![](../images/AI/ai-coding/d1.avif)
对于使用 AI 比较生疏的，可以参考以下文章 ↓
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

**在 VS Code 中安装 OpenCode、Claude Code、Codex 插件**
![](../images/AI/ai-coding/d2.avif)
**此时安装完，是无法使用的，要么使用官方账号登录，要么使用第三方中转，这里推荐使用开源软件 [**cc-switch**](https://ccswitch.io/zh/) 来管理 AI 工具，可以统一管理 AI 工具的供应商以及 Skills、MCP 等。**
![点击加号](../images/AI/ai-coding/d3.avif)
**安装完上述插件后，在 cc-switch 中直接添加并且配置 URL 和 api key 之后即可使用**
![选择供应商](../images/AI/ai-coding/d4.avif)
![配置 API](../images/AI/ai-coding/d5.avif)
**只要把红色框框的都填写完，就可以点击添加，这时候重启 VS Code 就可以发现，你的 CLI 工具可以打开了。**

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

最后，使用图形化开源软件 cc-switch 来配置 API
在终端输入 claude 或者 codex 即可呼起对应的 CLI
![](../images/AI/ai-coding/d6.avif)

#### 3.2 安装桌面端工具（推荐）
**推荐理由**：方便管理对话

均建议使用 cc-switch 代理
OpenCode
https://opencode.ai/zh
开源，并且内置支持 DeepSeek v4 flash 免费版；支持其他 AI 使用

Claude Code
https://www.anthropic.com/product/claude-code
支持其他 AI 使用，建议搭配 cc-switch 使用

Codex
https://chatgpt.com/zh-Hans-CN/codex
支持其他 AI 使用，建议搭配 cc-switch 使用

## 三、MCP 与 Skills 的使用

为了更好的使用 MCP 与 Skills，首先我们要先了解二者分别是什么意思，二者之间的区别是什么。

### 1. MCP 是什么？
**MCP** 是 Anthropic 推出的一个开放协议，让 AI 模型可以连接到外部数据源和工具。可以把它理解为 AI 的"USB 接口"——一个标准化的方式来让 Agent 访问外部系统。

**简单来说就是**：MCP 是“连接协议”，让模型能访问外部工具和数据，如数据库、API、文件系统等。

### 2. Skills 是什么？
**Skills** 是 Anthropic 公司发布的一个跨平台可移植性的开发标准，是一个可调用工作流/提示模板，本质上是预定义的 prompt + 工作模式。每个 Skill 封装了一类任务的最佳实践。

**简单来说就是**：Skills 就是一个“方法论”，模块化、可复用的任务流程和操作规范，封装了专业知识、工作方法和执行步骤。

### 3. MCP 与 Skills 的区别

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

![](../images/AI/ai-coding/d7.avif)

### 4. MCP 与 Skills 的安装方法
#### 4.1 资源获取
首先先要获取 MCP 和 Skills的资源，先了解一下资源网站。
- MCP 的资源网站：
https://mcp.so/
https://www.mcpworld.com/

- Skills 的资源网站
https://www.skills.sh/
https://skillhub.cloud.tencent.com/
https://skillsmp.com/zh

#### 4.2 如何安装/配置
**4.2.1 MCP**
首先打开你需要配置的 MCP 对应的网站/仓库，根据官方的文档来选择配置方案。
如果是只有如图所示的 json 片段，那么可以手动写入对应 Agent 的配置文件夹中或者在 cc-switch 中进行配置统一管理。
![json](../images/AI/ai-coding/d8.avif)
下面仅展示在 cc-switch 中如何配置：
![](../images/AI/ai-coding/d9.avif)
将 json 粘贴在 json 配置中即可。
> 其余情况参考官方文档的配置方案。

**4.2.2 Skills**
使用 `npx` 配置，或者使用 cc-switch 来配置，这里仅展示在 cc-switch 中如何配置。
点击 skills -> 发现技能 -> 仓库管理 -> 填写对应 skills 在 github 上的仓库地址
这里以 **Everything Claude Code** 为例，将地址粘贴至 cc-switch 中，点击添加仓库，此刻稍等一会；此时与网络环境有关，github 的 skills 需要搭配 VPN 来获取仓库，点击一次即可，不久后会显示 xxx 仓库已经添加。
![](../images/AI/ai-coding/d10.avif)
**然后在仓库中，选择你需要的 skills 下载即可**
![](../images/AI/ai-coding/d11.avif)

最后在使用的时候，记得要给对应的 Agent 开启技能（skills）和 MCP 即可。

### MCP 与 Skills 的使用教程
#### 1. 自然语言使用法
直接在 AI 工具中输入
- **MCP**：这里以 context7（对应 MCP 的唯一标题） 为例。
```txt
该项目中，我要使用 XXXX 库，请帮我使用 context7（可替换成想使用的 MCP） 来查询最新文档，xxxx。
```
- **Skills**：这里以 brainstorming（对应 Skill 的名称）为例。
```txt
请使用 brainstorming ，我要搭建 xxxx
```
#### 2. 命令调用
- **在 Claude Code 和 OpenCode 中**：输入 `/` ,即可选择 Skills 或 MCP。
![](../images/AI/ai-coding/d12.avif)

- **在 Codex 中**： 输入`$` ,即可选择 Skills;输入 `/` ，又可选择 Skills 也可以选择 MCP.
![](../images/AI/ai-coding/d13.avif)

#### 3. 仅写普通提示词（不推荐）
当你没有说明要使用什么 MCP 或者 Sklls 的时候，此时会根据模型能力，按需获取工具使用。
- **Skills 会自动匹配**：如果你的任务明显符合某个 skill 的 description，Agent 会自己选择使用。比如你说“帮我优化简历匹配 JD”，它可能自动用 resume-ats-optimizer。
- **MCP 会按需求调用**：如果任务需要外部数据或工具，比如“查最新文档”“打开网页测试”“读取 Figma 设计稿”，Agent 可能会自动调用已配置的 MCP。

> 当然，这种情况仅凭模型能力来驱动是否要使用工具并不可靠；例如编写 Skills 的人在没有写好 description，那么即使 Skill 写的再好，也不一定会被模型触发也无济于事。

## 四、总结
- **AI Coding 并不是让 AI 完全替代程序员**，而是让程序员在已有技术判断力的基础上，把 AI 作为编码、调试、学习和重构的协作工具。真正高效的使用方式，不是简单地把需求丢给 AI，而是学会拆分任务、描述上下文、审查结果，并用 Git 等工具保证修改过程可控。
- **对于刚入门的开发者，可以先完成最小环境搭建**：安装 Git、Node.js，并选择一个自己顺手的 AI Coding 工具，例如 Codex、Claude Code、OpenCode、Cursor 或 Trae。熟悉基础使用后，再逐步引入 cc-switch 来统一管理供应商、API、MCP 和 Skills。
- MCP 和 Skills 是进一步提升 AI Coding 效率的两个重要方向。MCP 解决的是“让 AI 连接外部工具和数据”的问题，Skills 解决的是“让 AI 按固定方法完成专业任务”的问题。前者偏能力扩展，后者偏流程复用，二者可以互补使用。
- **建议新手的学习路径是**：先掌握 Git 与基础 AI 对话方式，再使用一个稳定的 Agent 工具完成真实开发任务；随后学习如何配置 MCP 查询文档、操作浏览器或连接外部服务；最后再通过 Skills 沉淀常用工作流。这样既能提升效率，也能避免盲目依赖 AI 带来的风险。
- 总之，AI Coding 的核心不是“让 AI 写代码”，而是让开发者拥有一个更强的协作伙伴。你越能清楚地表达目标、提供上下文、验证结果，AI 就越能成为真正提升生产力的工具。


> 以上文章为个人经验 + AI 辅助校验；总结为 AI 编写与人工校验，如有错误请邮箱联系。