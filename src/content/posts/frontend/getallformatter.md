---
title: 最新 vuepress2 获取所有 formatter 教程
published: 2026-06-02
description: 一次性获得所有 formatter
tags: [web,vuepress,markdown]
category: web
draft: false
---

> 当前 vuepress 版本为：v2.0.0-rc.26

## 1. 写插件：把所有 frontmatter 挂到 siteData
**核心代码**：
```js
// .vuepress/getAllFrontmatter.js
export const getAllFrontmatter = {
  name: 'get-all-frontmatter',

  onInitialized(app) {
    // 自定义 frontmatter 属性，将 app.pages 中的 page.frontmatter 映射在 frontmatter 上
    app.siteData.frontmatter = app.pages.map((page) => page.frontmatter)
  },
}
``` 

## 2. 在配置中注册插件

```js
// .vuepress/config.js
import { defineUserConfig } from 'vuepress'
import { getAllFrontmatter } from './getAllFrontmatter.js'

export default defineUserConfig({
  plugins: [getAllFrontmatter],
})
```

注册完成以后，前端组件里就可以通过 useSiteData() 读取：
```js
siteData.value.frontmatter
```
## 3. 在组件中使用
```vue
<!-- .vuepress\components\info.vue -->
<template>
  <div>
    <div v-for="(item, index) in frontmatter" :key="index">
      <pre>{{ JSON.stringify(item, null, 2) }}</pre>
    </div>
  </div>
</template>

<script setup>
import { computed } from 'vue'
import { useSiteData } from 'vuepress/client'

const siteData = useSiteData()
const frontmatter = computed(() => siteData.value.frontmatter || [])
</script>
```

意思是：
- useSiteData() 取到 VuePress 全局站点数据
- siteData.value.frontmatter 就是你在插件里挂进去的全站 frontmatter

## 4. 注册这个组件

```js
// .vuepress/client.js
import { defineClientConfig } from 'vuepress/client'
import AllFrontmatter from './components/AllFrontmatter.vue'

export default defineClientConfig({
  enhance({ app }) {
    app.component('info', info)
  },
})
```

## 5. 在 markdown 中使用这个组件
```markdown
---
title: Info Page
description: A compact rendering of all collected frontmatter records.
---
## Site data snapshot

<info/>

```

## 6. 验收成果

![](..\images\frontend\vue\d1.avif)


