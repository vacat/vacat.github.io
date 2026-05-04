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

## TAG 规范

**英文 tag**：全小写，空格用 `-` 连接
```
ai, llm, mcp, kv-cache, ai-agent, ai-coding, ai-security, daily-digest
```

**中文 tag**：保留中文公司名和专有概念
```
阿里巴巴, 美团, 京东, 财报分析, 具身智能, 外卖, 人形机器人
```

**禁止**：
- 重复词：`人形人形机器人`
- 大小写混乱：`ai-agents`, `Ai-Agent`, `LLM`
- 双重括号格式：`tags: [[a, b]]`（正确：`tags: [a, b]`）
- 空 tag：至少有一个 tag，空文章默认 `daily-digest`

**同义合并**：
- `外卖业务` → `外卖`
- `机器人` → `人形机器人`
- `大模型` / `大语言模型` → `llm`
- `ai-agents` → `ai-agent`

## ANTI-PATTERNS

- 不要修改 `themes/hugo-theme-ladder/` 或 `themes/ananke/`（仅作参考）
- 不要在 `content/blog/zh/` 目录创建内容（当前使用根级 `.zh.md`）

## GIT 工作流

```bash
# 子模块修改需要单独提交
cd themes/hugo-theme-ladder-skycatc && git add layouts/ && git commit -m "fix: ..." && git push

# 主仓库提交（排除噪声文件）
git add config/ content/blog/archetypes/
git diff --cached --stat  # 先预览
git commit -m "fix: ..."
git push
```

**噪声文件（不提交）**：
- `.playwright-mcp/` - 浏览器测试日志
- `*.png` - 截图
- `*.log` - 临时日志

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

## HUGO 注意点

- **长 Summary 截断**：在 `head.html` 中截断前必须检查长度，否则 `substr` 会越界崩溃
- **子模块提交**：子模块内的修改需要单独 commit + push，主仓库不会自动包含
- **空 tags**：文章 tags 不能为空，至少填一个（默认 `daily-digest`）
- **格式检查**：`tags: [[a, b]]` 是错误格式，正确为 `tags: [a, b]`