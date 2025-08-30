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
hugo new blog/zh/post-name.md --kind blog # 使用blog原型创建
```

### 实用命令
```bash
hugo list drafts              # 列出所有草稿文章
hugo list future              # 列出未来发布的文章
hugo --cleanDestinationDir    # 构建前清理目标目录
hugo --buildDrafts            # 构建包含草稿内容
hugo --buildFuture            # 构建包含未来发布的文章
```

## 项目架构

### 配置文件结构
- `hugo.yml` - 根配置文件，包含基本站点设置（URL、主题、默认语言）
- `config/_default/` - 默认配置目录
  - `hugo.yml` - 主要配置（Google Analytics、分类taxonomies等）
  - `languages.yml` - 多语言配置，定义中英文界面和菜单
  - `params.yml` - 主题参数（作者信息、评论系统Giscus、统计工具Umami等）
  - `menus.yml` - 导航菜单配置

### 重要配置说明
- **默认语言**: 中文 (`zh`)，英文内容在子目录中
- **评论系统**: 使用Giscus（基于GitHub Discussions）
- **网站统计**: 使用Umami进行访问统计
- **主题特性**: 支持暗色模式、图片缩放、多语言

### 内容结构
- `content/blog/` - 英文博客文章
- `content/blog/zh/` - 中文博客文章
- `archetypes/` - 内容模板
- `static/` - 静态资源（图片等）

### 主题系统
- `themes/hugo-theme-ladder-skycatc/` - 自定义主题（主主题）
- `themes/hugo-theme-ladder/` - 原始Ladder主题（作为参考）
- `themes/ananke/` - 备用主题（目前未使用）
- 所有主题都通过Git子模块管理，更新命令：
  ```bash
  git submodule update --init --recursive
  git submodule update --remote
  ```

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
- 自动部署通过GitHub Actions工作流（`.github/workflows/hugo.yaml`）
  - 在main分支push时自动触发
  - 使用Hugo 0.145.0版本构建
  - 包含GC清理和minify压缩

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