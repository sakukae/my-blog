
<img src="./docs/images/123.png" width = "350" height = "500" alt="Firefly" align=right />
# 我的博客

> 一个基于 Astro 的个人博客站点，用来记录技术、生活和随想。

[在线访问](https://kaku.top) · [RSS](https://your-site.com/rss.xml) · [关于我](https://your-site.com/about) · [留言板](https://your-site.com/guestbook)

![首页预览](./docs/images/1.webp)

## 简介

这是我的个人博客，基于 Astro 和 Firefly 主题二次开发。

我会在这里发布：
- 技术笔记
- 项目记录
- 日常随笔
- 读书和学习整理

## 技术栈

- Astro
- TypeScript
- Tailwind CSS
- Svelte
- Pagefind

## 本地开发

```bash
pnpm install
pnpm dev
```

开发服务器默认运行在 `http://localhost:4321`。

## 常用命令

```bash
pnpm build
pnpm preview
pnpm check
pnpm format
pnpm new-post <filename>
```

## 站点配置

主要配置都在 `src/config/` 下：

- `siteConfig.ts`：站点名称、域名、SEO、语言
- `profileConfig.ts`：头像、简介、社交链接
- `navBarConfig.ts`：导航栏
- `sidebarConfig.ts`：侧边栏布局
- `commentConfig.ts`：评论系统
- `musicConfig.ts`：音乐播放器
- `friendsConfig.ts`：友链
- `galleryConfig.ts`：相册
- `backgroundWallpaper.ts`：背景图与壁纸

文章内容主要放在：

- `src/content/posts/`
- `src/content/spec/about.md`
- `src/content/spec/guestbook.md`

## 写文章

可以使用命令创建新文章：

```bash
pnpm new-post my-first-post
```

文章 Frontmatter 示例：

```yaml
---
title: 我的第一篇文章
published: 2026-06-02
description: 这是我博客的第一篇文章。
tags: [博客, Astro]
category: 随笔
draft: false
pinned: false
comment: true
---
```

## 部署

本项目可以部署到 Vercel、Netlify、Cloudflare Pages 等平台。

构建命令：

```bash
pnpm build
```

预览命令：

```bash
pnpm preview
```

## 截图

如果你想让 README 更像自己的博客，可以把这里换成首页、文章页、移动端页面的真实截图。

## 致谢

本博客基于 Firefly / fuwari 主题二次开发，感谢原作者的开源贡献。
