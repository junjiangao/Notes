---
title: Jekyll 博客搭建指南
date: 2025-01-07 16:00:00 +0800
categories: [技术, 教程]
tags: [jekyll, github-pages, 博客搭建]
---

# Jekyll 博客搭建完整指南

在这篇文章中，我将分享如何从零开始搭建一个 Jekyll 博客并部署到 GitHub Pages。

## 为什么选择 Jekyll？

Jekyll 是一个静态网站生成器，特别适合搭建个人博客：

### 优势

1. **简单直观**：使用 Markdown 写作，专注内容创作
2. **GitHub 支持**：原生支持 GitHub Pages，部署简单
3. **高性能**：静态网站，加载速度快
4. **可定制**：丰富的主题和插件生态
5. **免费**：完全免费的解决方案

### 适用场景

- ✅ 个人技术博客
- ✅ 项目文档网站
- ✅ 简单的企业网站
- ✅ 学习笔记整理

## 搭建步骤

### 1. 环境准备

首先确保你的系统安装了以下工具：

```bash
# 检查 Ruby 版本 (需要 >= 2.7.0)
ruby --version

# 检查 Bundler
bundler --version

# 如果没有安装 Bundler
gem install bundler
```

### 2. 创建 Jekyll 项目

```bash
# 创建新的 Jekyll 站点
jekyll new my-blog
cd my-blog

# 或者克隆现有主题
git clone https://github.com/cotes2020/jekyll-theme-chirpy.git my-blog
```

### 3. 配置文件详解

#### `_config.yml` 主要配置项：

```yaml
# 基本信息
title: 你的博客标题
tagline: 副标题
description: 博客描述

# URL 设置
url: 'https://username.github.io'
baseurl: '/repository-name'

# 作者信息
author:
  name: 你的姓名
  email: your-email@example.com

# 社交链接
github:
  username: your-github-username
```

#### `Gemfile` 依赖管理：

```ruby
source "https://rubygems.org"

gem "jekyll", "~> 4.3.0"
gem "jekyll-theme-chirpy", "~> 6.0"

group :jekyll_plugins do
  gem "jekyll-feed"
  gem "jekyll-sitemap"
  gem "jekyll-seo-tag"
end
```

### 4. 本地开发

```bash
# 安装依赖
bundle install

# 启动本地服务器
bundle exec jekyll serve

# 浏览器访问
# http://localhost:4000
```

### 5. GitHub Pages 部署

#### 方法一：GitHub Actions（推荐）

创建 `.github/workflows/pages-deploy.yml`：

```yaml
name: Deploy to GitHub Pages

on:
  push:
    branches: [ main ]

jobs:
  build-and-deploy:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout
        uses: actions/checkout@v4
        
      - name: Setup Ruby
        uses: ruby/setup-ruby@v1
        with:
          ruby-version: '3.1'
          bundler-cache: true
          
      - name: Build site
        run: bundle exec jekyll build
        
      - name: Deploy to GitHub Pages
        uses: actions/deploy-pages@v3
```

#### 方法二：直接推送到 gh-pages 分支

```bash
# 构建网站
bundle exec jekyll build

# 推送 _site 目录到 gh-pages 分支
git subtree push --prefix _site origin gh-pages
```

## 内容创作

### 文章格式

在 `_posts` 目录创建文件，命名格式：`YYYY-MM-DD-title.md`

```markdown
---
title: 文章标题
date: 2025-01-07 10:00:00 +0800
categories: [分类1, 分类2]
tags: [标签1, 标签2]
---

# 文章内容

这里是文章正文...
```

### Front Matter 详解

```yaml
---
title: 文章标题                    # 必填
date: 2025-01-07 10:00:00 +0800   # 发布日期
categories: [技术, 教程]           # 分类
tags: [jekyll, tutorial]          # 标签
pin: true                         # 置顶
toc: true                         # 目录
comments: true                    # 评论
image: /path/to/image.jpg         # 特色图片
---
```

## 常用插件推荐

### SEO 优化

```ruby
# Gemfile
gem "jekyll-seo-tag"
gem "jekyll-sitemap"
```

### 数学公式支持

```ruby
gem "jekyll-katex"
```

### 图片处理

```ruby
gem "jekyll-responsive-image"
```

## 性能优化建议

1. **图片优化**
   - 使用 WebP 格式
   - 压缩图片大小
   - 实现懒加载

2. **CSS/JS 优化**
   - 压缩静态资源
   - 使用 CDN 加速

3. **SEO 优化**
   - 设置合理的 meta 标签
   - 生成 sitemap.xml
   - 优化 URL 结构

## 常见问题

### 1. 构建失败

```bash
# 清除缓存
bundle exec jekyll clean

# 重新安装依赖
bundle install

# 检查配置文件语法
bundle exec jekyll doctor
```

### 2. 本地预览异常

```bash
# 指定端口运行
bundle exec jekyll serve --port 4001

# 监听所有网络接口
bundle exec jekyll serve --host 0.0.0.0
```

### 3. GitHub Pages 部署问题

- 检查 GitHub Pages 设置
- 确认 workflows 权限
- 查看 Actions 构建日志

## 总结

Jekyll 是搭建静态博客的优秀选择，结合 GitHub Pages 可以实现：

- ✅ 零成本搭建
- ✅ 自动化部署
- ✅ 高度可定制
- ✅ 良好的 SEO 表现

希望这个指南能帮助你快速上手 Jekyll 博客搭建！

---

**相关资源：**

- [Jekyll 官方文档](https://jekyllrb.com/docs/)
- [GitHub Pages 文档](https://docs.github.com/en/pages)
- [Chirpy 主题文档](https://chirpy.cotes.page/)

如果你在搭建过程中遇到问题，欢迎在评论区讨论！