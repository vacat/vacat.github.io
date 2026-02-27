# PROJECT KNOWLEDGE BASE

**Generated:** 2026-02-27
**Type:** Hugo Static Blog

## OVERVIEW

"朝花夕拾" - 双语个人博客。Hugo + 自定义 Ladder 主题 fork。部署至 GitHub Pages。

## STRUCTURE

```
.
├── hugo.yml                    # 根配置（baseURL, theme, defaultLanguage）
├── config/_default/            # 主配置目录
│   ├── hugo.yml               # taxonomies, GA
│   ├── languages.yml          # 双语配置（zh权重1, en权重2）
│   ├── params.yml             # 主题参数（Giscus, Umami）
│   └── menus.yml              # 导航菜单
├── content/blog/               # 博客内容
│   ├── *.zh.md                # 中文文章（根级）
│   ├── zh/                    # 中文目录（空，备用）
│   └── en/                    # 英文文章
├── data/                       # 数据文件（财务分析 markdown）
├── archetypes/default.md       # 内容模板
└── themes/                     # Git 子模块
    ├── hugo-theme-ladder-skycatc/  # 主主题（自定义 fork）
    ├── hugo-theme-ladder/          # 原始主题（参考）
    └── ananke/                     # 备用主题
```

## WHERE TO LOOK

| Task | Location |
|------|----------|
| 修改站点URL/标题 | `hugo.yml` |
| 修改菜单/导航 | `config/_default/languages.yml` |
| 修改主题参数/评论/统计 | `config/_default/params.yml` |
| 新建中文文章 | `content/blog/` 创建 `*.zh.md` |
| 新建英文文章 | `content/blog/en/` 创建 `*.en.md` |
| 修改主题样式/布局 | `themes/hugo-theme-ladder-skycatc/` |
| 修改 CI/CD | `.github/workflows/hugo.yaml` |

## CONVENTIONS

- **语言优先级**: 中文（weight: 1）> 英文（weight: 2）
- **命名规范**: 中文文章用 `.zh.md` 后缀，英文用 `.en.md` 后缀
- **主题修改**: 在 `hugo-theme-ladder-skycatc` 中进行，不修改原始主题
- **主题更新**: `git submodule update --remote`

## ANTI-PATTERNS

- 不要修改 `themes/hugo-theme-ladder/` 或 `themes/ananke/`（仅作参考）
- 不要在 `content/blog/zh/` 目录创建内容（当前使用根级 `.zh.md`）

## COMMANDS

```bash
hugo server -D              # 开发服务器（含草稿）
hugo --minify               # 构建生产版本
hugo new blog/post.zh.md    # 新建中文文章
hugo new blog/en/post.en.md # 新建英文文章
```

## NOTES

- Hugo 版本：0.145.0（CI 指定）
- 评论系统：Giscus（repo: vacat/vacat.github.io）
- 统计：Umami（独立部署）
- 主题子模块更新后需 `git submodule update --init --recursive`