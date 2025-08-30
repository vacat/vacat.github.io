# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## 项目概述

这是一个使用Hugo静态网站生成器构建的个人博客网站，名为"朝花夕拾"。网站支持中英双语，使用自定义的hugo-theme-ladder-skycatc主题。

## 常用命令

### 开发调试
```bash
hugo server -D          # 启动开发服务器，包含草稿内容
hugo server             # 启动开发服务器
```

### 构建发布
```bash
hugo                    # 构建静态网站到public目录
hugo --minify          # 构建并压缩输出
```

### 内容管理
```bash
hugo new blog/post-name.md     # 创建新博客文章
hugo new blog/zh/post-name.zh.md  # 创建中文博客文章
```

## 项目架构

### 配置文件结构
- `hugo.yml` - 根配置文件，包含基本站点设置
- `config/_default/` - 默认配置目录
  - `hugo.yml` - 主要配置（Google Analytics、分类等）
  - `languages.yml` - 多语言配置，定义中英文界面
  - `params.yml` - 主题参数（作者信息、评论系统、统计工具等）
  - `menus.yml` - 导航菜单配置

### 内容结构
- `content/blog/` - 英文博客文章
- `content/blog/zh/` - 中文博客文章
- `archetypes/` - 内容模板
- `static/` - 静态资源（图片等）

### 主题系统
- `themes/hugo-theme-ladder-skycatc/` - 自定义主题
- `themes/ananke/` - 备用主题（目前未使用）

### 关键特性
- 双语支持（中文优先，英文为辅）
- Giscus评论系统集成
- Umami网站统计
- 支持暗色模式
- 图片缩放功能
- Google Analytics集成

### 部署
- 使用GitHub Pages部署到 `https://vacat.github.io`
- 构建输出到 `public/` 目录

## 开发注意事项

### 多语言内容
- 中文内容创建在 `content/blog/zh/` 目录
- 英文内容创建在 `content/blog/` 目录  
- 菜单和界面文字在 `config/_default/languages.yml` 中配置

### 主题定制
- 当前使用 `hugo-theme-ladder-skycatc` 主题
- 主题相关配置在 `config/_default/params.yml`
- 自定义样式和布局修改需要在主题目录内进行

### 评论和统计
- 使用Giscus作为评论系统（基于GitHub Discussions）
- 集成Umami进行网站访问统计
- 相关配置在params.yml中