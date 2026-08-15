# Contributing to YourTJ Wiki

感谢贡献！YourTJ Wiki 的所有内容变更都通过 GitHub PR 协作完成：提交 PR → 审核 → merge → 服务器自动同步上线。

## 快速开始

1. **Fork** 本仓库；
2. 在 fork 中新建分支，编辑/新增 Markdown 文件；
3. 提交并推送，向本仓库开 Pull Request；
4. 仓库维护者 review 后 merge，线上 Wiki 自动同步。

> 也可以直接在 GitHub 网页端打开任意页面 → 右上角 ✏️ 铅笔图标 → fork 编辑 → 提交 PR。

## 命名与路径规范

- **顶层目录 = 命名空间**（如 `新生指南/`、`校园生活/`）；新命名空间先开 Issue 讨论；
- 文件名即 URL slug：小写字母/数字/连字符，如 `课程评价.md`、`campus-life.md`；
- 目录层级即页面层级，避免过深（建议 ≤ 3 层）；
- 重命名 = 移动文件（git 自动识别），线上评论/点赞/订阅不受影响。

## 页面规范

- 必须带 YAML frontmatter：`title`（必填）、`order`（排序权重，可选）、`description`（摘要，可选）；
- 使用 GitHub Flavored Markdown：标题层级从 `#` 开始（页面大标题用 `#`）；
- 代码块标注语言；图片放 `assets/` 并用相对路径引用；
- 敏感信息（手机号/学号/密码/内部链接）不要写进 wiki；
- 涉及课程评价等争议内容，请客观描述事实、避免情绪化表述。

## 自动检查（CI）

每个 PR 都会自动运行以下质量检查（全部通过才能 merge）：

- **markdownlint**：Markdown 语法/风格（标题层级、列表、代码块标注、空行等）；
- **textlint（中文排版）**：中西文/数字间空格、全角英文、不成对引号、空段落等；
- **lychee**：外链死链检查。

本地预览检查（需 Node.js 22+）：

```bash
npm ci
npm run lint:md   # markdownlint
npm run lint:zh   # textlint 中文排版
```

检查规则见 `.markdownlint-cli2.jsonc` / `.textlintrc.json` / `.lychee.toml`，需要放宽规则时在 PR 中说明理由。

## 审核约定

- 默认 merge 需 ≥2 人 review（branch protection）；
- 结构变更（新命名空间、目录重组、批量移动）建议在 PR 描述中说明意图；
- 有争议内容开 Issue 讨论，不在 PR 里争执。

## 自动同步说明

PR merge 到默认分支后，线上论坛通过 webhook 分钟级同步；每日定时同步兜底；管理员也可手动触发。同步失败不会影响线上旧内容。

## 问题反馈

内容错误/缺失 → 开 Issue；想讨论改造 → 开 Issue 或 Discussion。
