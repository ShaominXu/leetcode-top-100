# 算法百炼

LeetCode 高频题练习与笔记。

按知识点分类的 Markdown 笔记在 `[docs/topics/](./docs/topics/index.md)`（各子目录一个 `README.md`），站点首页为 `[docs/index.md](./docs/index.md)`。

## GitHub Pages

站点源码位于 `[docs/](./docs/)`（入口为 `docs/index.md`），使用 MkDocs 在 CI 中构建后发布。
发布流程由 `[.github/workflows/pages.yml](./.github/workflows/pages.yml)` 完成。

在仓库 **Settings → Pages** 中：

1. **Build and deployment → Source** 选 **GitHub Actions**（不要再用 “Deploy from a branch”）。
2. 推送 `main` 后工作流会执行 `mkdocs build --strict`，上传 `site/` 并部署；也可在 **Actions** 里手动 **Run workflow**。
3. 站点地址：`https://<你的用户名>.github.io/LeetCode-Top-100/`

本仓库采用“只维护 Markdown，自动构建网页”的方式，无需手写 HTML 页面。