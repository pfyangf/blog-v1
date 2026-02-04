# 🚀 GitHub Pages 部署指南

## ✅ 代码已推送到 GitHub

仓库地址：https://github.com/pfyangf/blog-v1

---

## 📋 GitHub Pages 配置步骤

### 方法 1: 使用 GitHub Actions 自动部署（推荐）

#### 1. 启用 GitHub Actions

1. 访问你的仓库：https://github.com/pfyangf/blog-v1
2. 点击 **Settings**（设置）
3. 在左侧菜单找到 **Pages**
4. 在 **Source** 下拉菜单中选择 **GitHub Actions**

#### 2. 触发部署

GitHub Actions 工作流已经配置好（`.github/workflows/deploy.yml`），现在只需：

```bash
# 推送任何更改到 main 分支即可触发自动部署
git add .
git commit -m "Update content"
git push origin main
```

#### 3. 查看部署状态

1. 访问仓库的 **Actions** 标签页
2. 查看 "Deploy to GitHub Pages" 工作流
3. 等待部署完成（通常 2-3 分钟）

#### 4. 访问网站

部署成功后，访问：

**https://pfyangf.github.io/blog-v1/**

---

### 方法 2: 手动部署

如果你想手动部署，可以使用以下命令：

```bash
# 设置 Git 用户信息（如果还没设置）
git config --global user.email "you@example.com"
git config --global user.name "Your Name"

# 部署到 GitHub Pages
npm run deploy
```

这会自动构建并推送到 `gh-pages` 分支。

---

## 🔧 配置说明

### 已更新的配置

在 `docusaurus.config.ts` 中已配置：

```typescript
{
  url: 'https://pfyangf.github.io',
  baseUrl: '/blog-v1/',
  organizationName: 'pfyangf',
  projectName: 'blog-v1',
}
```

### GitHub Actions 工作流

文件：`.github/workflows/deploy.yml`

```yaml
name: Deploy to GitHub Pages

on:
  push:
    branches:
      - main

jobs:
  deploy:
    runs-on: ubuntu-latest
    permissions:
      contents: write
    steps:
      - uses: actions/checkout@v4
      - uses: actions/setup-node@v4
        with:
          node-version: 18
          cache: npm
      - run: npm ci
      - run: npm run build
      - uses: peaceiris/actions-gh-pages@v3
        with:
          github_token: ${{ secrets.GITHUB_TOKEN }}
          publish_dir: ./build
```

---

## ✅ 验证部署

### 1. 检查 GitHub Actions

访问：https://github.com/pfyangf/blog-v1/actions

确认工作流运行成功（绿色对勾 ✓）

### 2. 检查 GitHub Pages 设置

1. 访问：https://github.com/pfyangf/blog-v1/settings/pages
2. 确认显示：
   - **Source**: GitHub Actions
   - **Your site is live at**: https://pfyangf.github.io/blog-v1/

### 3. 访问网站

打开浏览器访问：

**https://pfyangf.github.io/blog-v1/**

应该能看到你的博客首页！

---

## 🌐 多语言访问

- **中文版**：https://pfyangf.github.io/blog-v1/
- **英文版**：https://pfyangf.github.io/blog-v1/en/
- **归档页**：https://pfyangf.github.io/blog-v1/archive
- **标签云**：https://pfyangf.github.io/blog-v1/tags-cloud

---

## 📝 更新博客内容

### 1. 添加新文章

在 `blog/2025/` 目录下创建新的 Markdown 文件：

```markdown
---
slug: my-new-post
title: 我的新文章
authors: [admin]
tags: [tutorial]
date: 2025-02-05T10:00
---

文章摘要...

<!--truncate-->

文章正文...
```

### 2. 推送更新

```bash
git add .
git commit -m "Add new blog post"
git push origin main
```

### 3. 自动部署

GitHub Actions 会自动：
1. 检测到推送
2. 运行构建
3. 部署到 GitHub Pages

几分钟后，新文章就会出现在网站上！

---

## 🔍 故障排除

### 问题 1: 部署失败

**检查**：
1. 访问 Actions 标签页查看错误日志
2. 确认 `package.json` 中的依赖没有问题
3. 本地运行 `npm run build` 确认能正常构建

**解决**：
- 修复错误后重新推送
- GitHub Actions 会自动重新运行

### 问题 2: 网站显示 404

**检查**：
1. 确认 GitHub Pages 设置正确
2. 确认 `baseUrl` 配置为 `/blog-v1/`
3. 等待几分钟让 DNS 生效

**解决**：
- 访问 Settings → Pages 确认配置
- 清除浏览器缓存重试

### 问题 3: 样式或资源加载失败

**检查**：
- 确认 `baseUrl` 配置正确
- 检查浏览器控制台的错误信息

**解决**：
```typescript
// docusaurus.config.ts
{
  url: 'https://pfyangf.github.io',
  baseUrl: '/blog-v1/',  // 必须以 / 开头和结尾
}
```

---

## 🎨 自定义域名（可选）

如果你有自己的域名，可以配置自定义域名：

### 1. 添加 CNAME 文件

在 `static/` 目录下创建 `CNAME` 文件：

```
blog.yourdomain.com
```

### 2. 配置 DNS

在域名提供商处添加 CNAME 记录：

```
blog.yourdomain.com → pfyangf.github.io
```

### 3. 更新配置

```typescript
// docusaurus.config.ts
{
  url: 'https://blog.yourdomain.com',
  baseUrl: '/',
}
```

### 4. 在 GitHub 设置自定义域名

Settings → Pages → Custom domain → 输入 `blog.yourdomain.com`

---

## 📊 部署统计

### 当前状态

- ✅ 代码已推送到 GitHub
- ✅ GitHub Actions 工作流已配置
- ✅ 部署配置已更新
- ⏳ 等待首次部署完成

### 部署信息

- **仓库**：https://github.com/pfyangf/blog-v1
- **网站**：https://pfyangf.github.io/blog-v1/
- **分支**：main
- **部署方式**：GitHub Actions

---

## 🎉 下一步

1. **访问网站**：https://pfyangf.github.io/blog-v1/
2. **查看 Actions**：https://github.com/pfyangf/blog-v1/actions
3. **编写更多博客**：在 `blog/` 目录下添加文章
4. **自定义样式**：编辑 `src/css/custom.css`
5. **申请 Algolia**：参考 `docs/ALGOLIA_SETUP.md`

---

## 📚 相关文档

- **README.md** - 项目概述
- **GUIDE.md** - 完整实战指南
- **QUICKSTART.md** - 快速启动
- **FEATURES.md** - 功能清单
- **STARTUP.md** - 启动说明
- **docs/I18N_COMPLETE.md** - 多语言配置

---

**恭喜！你的博客已成功部署到 GitHub Pages！** 🎉

访问 https://pfyangf.github.io/blog-v1/ 查看你的博客！
