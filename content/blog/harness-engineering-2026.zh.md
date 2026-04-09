---
title: "Harness 工程：AI Agent 时代的基础设施思维"
date: 2026-04-09T22:30:00+08:00
tags: [AI, Agent, 工程]
series: []
featured: true
---

> **题记：** "Agents aren't hard; the Harness is hard."  
> — Ryan Lopopolo，OpenAI Codex 团队

<!--more-->

## 引言：当模型不是瓶颈

过去两年，AI 工程师们花了大量时间优化 prompt、设计 context window、调试 RAG 方案。但越来越多团队发现：**换了更强模型之后，问题并没有消失。**

真正的问题不在模型本身，而在**包裹模型的那层基础设施**——社区给它起了一个名字：**Harness（挽具/马具）**。

2026 年 2 月，这个概念集中爆发：Mitchell Hashimoto（Terraform 创始人）发表博客，OpenAI 发布 Codex 5 个月的实验报告，Martin Fowler 网站出现专题文章。所有人指向同一个结论——**AI Agent 的军备竞赛，本质上是 Harness 的工程竞争。**

---

## 一、什么是 Harness？

### 直观理解

想象你要教会一个人完成软件工程任务：

- **Prompt 工程** → 教他"说什么话"
- **Context 工程** → 教他"看什么资料"
- **Harness 工程** → 教他"在什么样的系统里工作"

如果用驾驶来比喻：

| 层级 | 驾驶类比 |
|:---:|:---|
| Prompt | 告诉司机"向前开" |
| Context | 给他地图、路标、仪表盘 |
| Harness | 修好路、设好护栏、装好后视镜，连刹车油门的响应曲线都调好 |

模型再强，给它一条泥泞小路也跑不快。

### 正式定义

**Harness** = 围绕 AI Agent 的一整套**脚手架、约束机制和反馈循环**。它包括：

- 代码库结构和 CI 配置
- 代码规范和格式化规则
- Linter、测试、类型检查等反馈系统
- 外部工具集成（MCP 服务器）
- 知识文档体系（AGENTS.md 等）
- 错误恢复机制

### 一句话总结

> **Harness 决定了 agent 的解决方案空间长什么样。** 约束越精确，agent 越快收敛到正确答案。

---

## 二、为什么是现在？三层演进史

```
2023-2024  │ Prompt 工程时代
           │ 优化单次输入 → 单次输出
           │ 关键词：few-shot、CoT、角色扮演
           │
Mid-2025   │ Context 工程时代
           │ Andrej Karpathy 推动
           │ RAG、MCP、Memory 成为标配
           │ 核心问题：给模型看什么？
           │
2026.02    │ Harness 工程时代
           │ Hashimoto 博客（2月5日）
           │ OpenAI Codex 实验报告（2月11日）
           │ 核心问题：整个环境怎么设计？
```

---

## 三、核心设计原则：来自一线团队的验证

### OpenAI Codex：5 个月，0 行手写代码

OpenAI 团队用 Codex 从零开始构建了一个内部产品：

| 指标 | 数据 |
|:---|:---|
| 时间 | 2025.08 - 2026.01（约5个月）|
| 团队规模 | 3 → 7 名工程师 |
| 代码量 | ~100 万行 |
| PR 数量 | ~1500 个 |
| 人工代码 | **0 行** |
| 开发速度 | ~10x 传统方式 |

**关键经验（来自 OpenAI 工程师 Ryan Lopopolo）：**

> "失败之后，修复方案几乎从来不是'再试一次'。唯一能推进工作的方式是问自己：**'缺了什么能力？如何让 agent 能理解并遵守它？**"

### Mitchell Hashimoto：99.9% 可用率

Hashimoto 在博文中给出的核心方法论：

> **每次发现 agent 犯了一个错误，就花时间工程化地解决这个问题——使它再也不会犯这个错误。**

这不是在调 prompt，这是在**持续改进系统本身**。

### Anthropic：解耦大脑与手

Anthropic 官方工程博客描述的 Managed Agents 架构，将 Agent 分解为三个独立组件：

```
┌─────────────────────────────────────────┐
│  Session（日志/记忆）  ←─ 外置，持久化    │
│  Harness（编排循环）  ←─ 无状态，可重启  │
│  Sandbox（执行环境）  ←─ 按需创建/销毁    │
└─────────────────────────────────────────┘
```

**核心效果：**
- 容器死了 ≠ 会话丢了
- Harness 可以无状态重启，从 Session 恢复
- Sandbox 变成"牛"，死了换一只就行
- **TTFT 延迟（用户感知最明显的指标）下降 60-90%**

---

## 四、Harness 的两大控制机制

Martin Fowler 的文章把这套机制类比为**控制论中的调节器**，分为前馈（Feedforward）和反馈（Feedback）。

### 前馈（Feedforward）—— 行动之前

**目的：** 预判 agent 行为，提前引导。

**典型手段：**
- `AGENTS.md` / `CLAUDE.md`：项目规范文档
- Skill 文件：重复性工作的标准流程
- 架构原则文件（如 `ARCHITECTURE.md`）
- MCP 服务器：让 agent 能访问外部工具

### 反馈（Feedback）—— 行动之后

**目的：** 观察行为结果，触发自我修正。

**典型手段：**
- Linter：代码风格违规时，直接在错误信息里注入修复提示
- 测试套件：运行测试，失败则让 agent 重新理解需求
- AI 代码审查：用另一个 agent 审查第一个 agent 的代码
- 人工 review：兜底的安全网

### 两种执行模式

| 类型 | 特点 | 例子 |
|:---|:---|:---|
| **计算型** | 确定性、毫秒级、CPU执行 | Linter、类型检查、单元测试 |
| **推理型** | 语义分析、GPU/NPU、较慢 | AI review、"LLM as judge" |

**关键洞察：** 计算型传感器足够便宜，可以每次变更都运行；推理型传感器用于建立信任，但成本较高。

### 两者缺一不可

- **只有前馈** → 规则得不到验证，变成死去的文档
- **只有反馈** → 同样的错误会重复发生

---

## 五、最佳实践

### 1. 不要把 AGENTS.md 写成百科全书

OpenAI 踩过的坑：

- 文档太大 → 关键信息被稀释
- 什么都标记为"重要" → 等于什么都没标记
- 文档会过时 → 变成规则墓地

**正确做法：把它当成目录（Table of Contents），不是说明书。**

```
docs/
├── design-docs/
│   ├── index.md
│   └── core-beliefs.md
├── exec-plans/
│   ├── active/
│   └── completed/
├── references/
└── ARCHITECTURE.md      # ~100行，顶层地图
```

Agent 从小处着手，需要时顺着目录找到更多信息。

### 2. 用机械执行代替口头规则

> 写在文档里的规则，agent 可以违反。  
> 在系统层面 enforcing 的规则，agent 无法绕过。

**例子：** 如果想保持模块之间的依赖方向：

```
Types → Config → Repo → Service → Runtime → UI
```

用 linter 在 CI 层强制执行，违规直接 block 并触发修复循环。

### 3. 出了问题先改 Harness

OpenAI 工程师有个工作原则：

> **如果一个 PR 需要大量人工介入才能完成，责任不在 agent——在 Harness。**

这改变了团队的问题解决心态：不是让 agent 更努力，而是让系统更好。

### 4. 让知识存在于 agent 能读到的地方

> 从 agent 的视角看，**任何它运行时读不到的东西等于不存在。**

- Slack 讨论 → 写成文档进代码库
- 口头约定 → 写成 `AGENTS.md`
- Google Doc → 进代码库或 MCP 知识库

### 5. 渐进式信任，分阶段放权

不要一开始就给 agent 全部权限。用 gates（门控）分阶段：

```
Stage 1: 只读 + lint 反馈
Stage 2: 小文件编辑
Stage 3: 重要文件修改
Stage 4: 独立提交 PR
Stage 5: 自主合并（需 CI green）
```

Stripe 的 Minions 系统在每次 agent 修复失败两次后，**立即升级给人类处理**——而不是让它无限重试。

---

## 六、真实案例：Claude Code 的 Harness 架构

2026 年 3 月，Claude Code 源代码意外泄露（512,000 行 TypeScript），让我们得以一窥 Anthropic 自己的 harness 设计。

### 三层架构

| 组件 | 职责 |
|:---|:---|
| **Orchestration Loop** | 规划与执行管理（QueryEngine.ts ~46k行）|
| **Permission-Gated Tools** | ~40 种离散能力，独立权限门控 |
| **Multi-Layer Memory** | Session 持久化 + 验证机制 |

### 五种 Context 管理策略

Claude Code 将 context 管理列为**一等公民**：

1. 基于时间的旧工具结果清理
2. 对话摘要
3. Session 记忆提取
4. 完整历史摘要
5. 最旧消息截断

### 权限系统三阶段

```
┌────────────────────────────────────────┐
│ 1. 项目加载时建立信任                    │
│ 2. 每个工具执行前权限检查                │
│ 3. 高风险操作需用户显式确认              │
└────────────────────────────────────────┘
```

**架构原则：** "模型决定做什么，但工具系统决定什么被允许。这两件事在架构上是分离的。"

### 多 Agent 协调模式

| 模式 | 机制 | 适用场景 |
|:---|:---|:---|
| **Fork** | 父上下文完整副本，吃到 prompt cache | 并行工作，缓存复用近乎免费 |
| **Teammate** | tmux/iTerm 中的独立 pane，文件邮箱通信 | 松耦合的工作流协调 |
| **Worktree** | 独立 git worktree，隔离分支 | 探索性或有风险的工作 |

### Memory 三层设计

```
Layer 1 │ MEMORY.md   │ 轻量索引指针，始终加载 (~150字符/条)
Layer 2 │ Topic files │ 按需调入的详细项目笔记
Layer 3 │ Raw transcripts │ 仅搜索访问，从不整体加载
```

**核心原则：** agent 被要求把自身记忆当作"提示"而非"事实"，行动前必须对照真实代码库验证。

---

## 七、Evaluator Agent：让 QA 重新变得重要

### 问题

Agent **无法可靠地评估自己的输出**。被要求审查自己的代码时，模型几乎总是表示满意——即使代码有问题。

### GAN 思路的借鉴

OpenAI 和 Anthropic 都发现了一个关键洞察：

| Agent | 角色 |
|:---|:---|
| **Generator Agent** | 写代码、做 UI、执行主要任务 |
| **Evaluator Agent** | QA 工程师，用 Playwright 验证行为，检查 API，确认 DB 状态 |

**关键发现：** 用 stock Claude 4 做 evaluator 效果很差——太宽松，容易被说服"这不是关键 bug"。但**单独训练一个 evaluator agent 变得极其严格，比教 generator agent 学会自我批评要容易得多。**

---

## 八、趋势与展望

### 1. 企业级 Harness：语义图谱

Epsilla 提出的"语义图谱"（Semantic Graph）方向：

- 将 agent 的全部操作现实表示为一张**结构化图**
- Schema 本身就是约束——agent 不会走进死胡同
- 修正被编码为结构变更，永久改变 agent 的世界模型

### 2. "宠物 vs 牛" 的隐喻将持续

在基础设施层面，把 agent 组件当作"可替换的牛"而非"不能死的宠物"，是系统设计的关键思维转变。

- Harness 应该是**无状态的**
- Session 是**持久的**
- Sandbox 是**按需创建的**

### 3. 工程师角色的转变

OpenAI 的实验揭示了一个深刻变化：

> **工程师不再写代码，而是设计反馈系统和约束机制。**

这不是说编程知识不再重要——而是说**核心工作从"产出代码"变成了"构建让代码可靠产出的系统"**。

---

## 结语

Harness 工程的核心洞察其实非常朴素：

**AI Agent 的瓶颈很少是模型本身，而几乎总是环境设计。**

就像操作系统抽象了硬件一样，Harness 正在成为 AI 时代的新抽象层。它决定了一个强大的模型能发挥多少潜力，也决定了一个系统能否从"演示"走向"生产"。

> 下次你的 agent 又出问题了，别急着换模型。  
> 先问：**Harness 够不够好？**

---

*本文综合自 Anthropic Engineering Blog（2026.01）、OpenAI Codex Field Report（2026.02）、Martin Fowler "Harness Engineering for Coding Agent Users"（2026.04）、Mitchell Hashimoto 博客、Claude Code 源码泄露分析，以及 Epsilla/Louis Bouchard 等技术博客。所有来源均为 2026 年初的最新资料。*
