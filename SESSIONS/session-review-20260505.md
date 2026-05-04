# 博客优化复盘 | 2026-05-05

## 一、做了什么

### 1. Tag 系统规范化

**问题**：混乱的大小写、多义词重复、无效格式

**操作**：
- 统一英文 tag 小写：`Llm→llm`, `Ai-Agent→ai-agent`, `Kv-Cache→kv-cache`, `Mcp→mcp`
- 合并同义 tag：`外卖业务`→`外卖`, `机器人`→`人形机器人`, `大模型`/`大语言模型`→`llm`
- 修复格式：`tags: [[...]]` → `tags: [...]`，空 tag → `daily-digest`
- 消除内容噪点：`人形人形机器人` → `人形机器人`，`ai-agents` → `ai-agent`

**结果**：tag 目录从 73+ 精简至 44 个

---

### 2. Hugo 构建修复

**问题**：长 Summary 截断越界崩溃

**操作**：在 `head.html` 中添加 bounds check

```go
{{- $summary := .Summary }}
{{- if gt (len $summary) 300 }}
{{- $summary = substr $summary 0 300 }}
{{- end }}
```

**结果**：消除 `slice bounds out of range` 错误

---

### 3. 配置优化

| 配置项 | 修改 |
|--------|------|
| `enableMultiLang` | `true` → `false`（移除语言切换入口） |
| Menu | 移除 生活、历史（无内容） |
| Categories | 添加 taxonomy 定义 |
| featured flags | 清除无 Featured 属性的标记 |

---

### 4. 提交规范

**教训**：使用 `git add -A` 前必须排除临时文件

**正确流程**：
1. `git add <specific files>` - 只加需要提交的
2. `git diff --cached --stat` - 确认前先预览
3. `git commit -m "..."`
4. 有噪声文件 → `git reset HEAD <file>` 撤销

**噪声文件列表**：
- `.playwright-mcp/` - 浏览器测试日志
- `category-*.png`, `tags-page.png` - 截图
- `*.log` - 临时日志

---

## 二、沉淀的规范

### 1. Tag 命名规范

```
英文 tag：全小写，空格用 - 连接
  ai, llm, mcp, kv-cache, ai-agent, ai-coding, daily-digest

中文 tag：保留中文公司名和专有概念
  阿里巴巴, 美团, 京东, 财报分析, 具身智能, 外卖

禁止：
  - 重复词：人形人形机器人
  - 大小写混乱：ai-agents, Ai-Agent, LLM
  - 双重括号格式：tags: [[a, b]]
```

### 2. 文章 frontmatter 格式

```yaml
---
title: "标题"
date: 2026-03-01T08:00:00+08:00
draft: true  # 草稿不发布
categories:
  - 技术日报  # 或 技术洞察 / 商业分析
tags:
  - ai
  - llm
---
```

### 3. Hugo 注意点

- **子模块修改** 需要在子模块目录内单独 commit + push
- **长 Summary** 截断前必须检查长度
- **enableMultiLang** 控制语言切换 UI

---

## 三、Git 工作流

```bash
# 1. 查看变更
git status --short

# 2. 选择性暂存（排除噪声）
git add config/ content/blog/archetypes/

# 3. 预览统计
git diff --cached --stat

# 4. 提交
git commit -m "fix: ..."

# 5. 推送
git push

# 子模块单独推送
cd themes/hugo-theme-ladder-skycatc && git push
```

---

## 四、后续优化建议

1. **Tag 数量监控**：定期 `ls public/tags/` 检查异常增长
2. **Hugo CI**：添加 `--minify` 构建检查，防止长 Summary 错误逃逸
3. **featured 标志清理**：考虑自动化（当前手动清理）
4. **内容质量**：日报类文章存在大量 `<!--more-->` 截断标记，内容重复度高，可考虑合并或精简
