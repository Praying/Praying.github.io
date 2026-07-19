# ADR 0001: 从 Hugo 产物仓库重构为 Astro 源码仓库

- 状态：已接受
- 日期：2026-07-19

## 背景

本仓库（Praying.github.io）此前只存放 Hugo 0.49 + Jane 主题的**构建产物**（HTML/CSS/JS），
源码存放在远程的 `code` 分支。网站从"技术博客"重新定位为"个人思考记录"，
要求极致的中文阅读体验（原研哉式设计语言 + Anthropic 官网配色），
旧的 Jane 主题与 Hugo 模板体系无法承载这套排版目标。

## 决策

1. `master` 分支改为存放 **Astro 源码**（内容、布局、样式即仓库的全部真相），
   由 GitHub Actions（`actions/deploy-pages`）构建并部署到 GitHub Pages。
2. 旧构建产物从工作区清空；git 历史与远程 `code` 分支保留旧 Hugo 存档，不迁移旧文章。
3. 字体采用 fontsource 的 Noto Serif SC / Source Serif 4 子集分片**自托管**，
   不依赖 Google Fonts CDN（对大陆访问不稳定）。

## 备选方案

- **继续 Hugo + 自写主题**：Go template 定制繁琐，主题开发体验差。
- **纯手写 HTML/CSS**：控制力最强，但每篇文章都要手写页面并手动维护首页时间线，长期写作摩擦大。
- **fontsource 替换为 cn-font-split 自切字体**：需要引入字体切分工具链与大体积字体源文件，fontsource 已提供等价的 unicode-range 分片。

## 后果

- 写作工作流变为：新建 Markdown → push → 自动上线，克隆单个分支即可写作。
- 构建产物（dist）不再入库；Pages 的部署来源需在仓库设置中切换为 "GitHub Actions"。
- 旧文章 URL 全部失效（仅两篇，影响可忽略）；根域名、RSS 地址保持不变。
