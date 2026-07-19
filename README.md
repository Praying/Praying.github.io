# 湖心小筑

一个人的思考与文字。白纸、墨色、一方朱印。

线上地址：<https://praying.github.io>

## 写一篇新文章

在 `src/content/posts/` 下新建一个 Markdown 文件，文件名即 URL（建议用英文或拼音小写短横线命名）：

```markdown
---
title: 文章标题
date: 2026-07-20
---

正文……
```

- `date` 决定时间线上的位置，精确到日即可。
- 想让一篇文章暂不上线：frontmatter 里加 `draft: true`。
- `git push` 到 `master`，GitHub Actions 会自动构建并上线。

## 本地预览

```bash
npm install
npm run dev      # 开发预览 http://localhost:4321
npm run build    # 构建到 dist/
npm run preview  # 预览构建产物
```

## 设计

- 配色：纸白 `#FAF9F5`、墨色 `#1F1E1D`、朱印 `#D97757`（仅用于站名旁的小印、链接悬停与选中底色）
- 字体：思源宋体（Noto Serif SC，fontsource 子集分片自托管、按需加载）+ Source Serif 4（拉丁与数字）
- 原则：无标签、无搜索、无评论、无暗色模式 —— 见 [CONTEXT.md](./CONTEXT.md)

## 中文写作建议

- 强调请用「」或加粗，避免斜体（中文无斜体传统，浏览器会合成难看的倾斜字形）。
- 段落之间自然分段即可，无需首行缩进（网页惯例用段间距）。
