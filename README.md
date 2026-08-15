# YourTJ Wiki

YourTJ 同济校园社区的知识库 / Wiki 内容仓库。

**本仓库是 YourTJ Wiki 的唯一真实源（Single Source of Truth）**：全部 wiki 内容以 Markdown 文件形式存放于此，所有编辑经 GitHub PR 协作完成（多人协作编辑、审核、contributors 自动生成），服务器定时/即时同步到线上论坛内嵌 Wiki。

## 目录结构

```text
YourTJ-Wiki/
├── README.md
├── CONTRIBUTING.md          # 编辑指南、PR 流程、frontmatter 规范
├── CODEOWNERS               # 可选：目录级审核负责人
├── assets/                  # 图片等二进制，md 内相对路径引用
├── <namespace>/             # 顶层目录 = 命名空间（对应论坛 wiki 分组）
│   ├── <子目录>/<页面>.md
│   └── index.md
```

- 顶层目录 = 命名空间（namespace），对应论坛 Wiki 的分组；
- 任意层级子目录 = 页面层级；
- 每个页面一个 `.md` 文件，使用 YAML frontmatter（见下）。

## 页面格式

```markdown
---
title: 页面标题
order: 10
description: 一句话摘要
---

正文（GitHub Flavored Markdown）。
```

| 字段 | 必填 | 说明 |
|---|---|---|
| `title` | ✅ | 页面标题，显示在导航树与页面头部 |
| `order` | ❌ | 排序权重，同级页面按此升序排列（默认 0） |
| `description` | ❌ | 摘要，用于首页/卡片展示 |

## 图片与附件

- 放在仓库内 `assets/` 目录（可按 namespace 分子目录，如 `assets/新生指南/xxx.png`）；
- 在 md 中**使用相对路径引用**：`![说明](../assets/新生指南/xxx.png)`；
- 不要引用外部图床，保证内容可移植、可审核。

## 如何贡献

见 [CONTRIBUTING.md](CONTRIBUTING.md)。一句话版：**fork → 改 md → PR → review → merge → 线上自动同步**。

## 线上同步

线上论坛（yourtj-hub）内置同步器，从本仓库拉取内容并渲染为论坛内嵌 Wiki：

- PR merge 后 webhook 触发同步（分钟级生效）；
- 每日定时同步兜底（默认 03:00）；
- 管理员可在论坛后台手动触发同步。
