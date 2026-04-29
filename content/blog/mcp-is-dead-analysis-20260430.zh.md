---
title: "MCP 没死，但它不再是万能药"
date: 2026-04-30T10:00:00+08:00
tags: ["MCP", "AI Agent", "技术分析", "Anthropic"]
categories: ["技术"]
featured: true
summary: "深度调研「MCP is Dead」现象的来龙去脉：它批评了什么、反驳了什么、最终说明了什么"
---

> *"Agents are only as useful as the systems they can reach."* — Anthropic

![](https://v3b.fal.media/files/b/0a9838ab/ZpAWhUCclpYq_Wkp0MoWv_U1GMrohH.png)

今年3月，AI 圈突然刮起一股"MCP is Dead"的风。Perplexity CTO 公开批评 MCP 的 context overhead 和笨重认证；LinkedIn 上多位从业者吐槽 MCP auth 繁琐、context 膨胀；几篇技术博客直接用"MCP is Dead"做标题——而与此同时，MCP SDK 月下载量刚突破 3 亿次，Anthropic 还在发博文讲"如何构建优秀的 MCP Server"。

这到底是怎么回事？

<!--more-->

## 一、声音从哪来？

"MCP is Dead"的说法在 **2026 年 3 月** 开始发酵，几个关键节点：

| 来源 | 核心观点 |
|---|---|
| **Perplexity CTO** | MCP 的 context overhead 太大，auth 机制笨重 |
| **chrlschn.dev** | MCP 对 CLI 类场景是错误选择，但"死"的说法是深刻误解 |
| **Medium (Micheal Lanham)** | MCP 在 2026 年 3 月达到拐点，不再是万能默认答案 |
| **arXiv 2508.12566** | 系统性实证研究揭示 MCP 集成的四个关键局限 |
| 多位从业者（LinkedIn）| 直言 MCP auth 繁琐、context 膨胀 |

有意思的是，Anthropic 4月底发布的那篇 [《Building agents that reach production systems with MCP》](https://claude.com/blog/building-agents-that-reach-production-systems-with-mcp)，某种程度上正是对这场批评的正面回应。

---

## 二、MCP 被批评的六个致命缺陷

### 1. Context Overhead（上下文膨胀）— 最核心问题

多个活跃 MCP 连接会把**大量工具定义和返回结果灌入 LLM context**，导致上下文爆炸。Perplexity CTO 直言：**"MCP has too much context overhead and clunky auth."**

一篇技术博客的标题直接点名：**"MCP's Overengineered Transport and Protocol Design"**。

### 2. Auth 机制笨重

OAuth 认证流程在云端 Agent 场景下弹窗频繁、首次认证摩擦大。虽然 Anthropic 推出了 CIMD（Client ID Metadata Documents）作为解法，但实际落地仍不顺畅。

### 3. 无法评估检索内容相关性

MCP 最大的设计缺陷：**把信息获取回来了，但 LLM 无法判断这些信息是否真的与问题相关**。标准 RAG 也存在这个问题，但 MCP 的多工具场景放大了它。

### 4. 工具发现与选择没有标准化

Agent 在运行时面对数十个 MCP Server、数百个工具时，**难以判断该用哪个工具、什么时候用**。Proactivity（主动工具调用）和 Compliance（遵循指令）两个维度上，LLM 表现远不如预期。

### 5. 安全边界模糊

工具权限范围不清晰——MCP Server 拿到 token 后能做什么、不能做什么，没有严格隔离。多个研究专门讨论了 MCP 安全问题。

### 6. 实证数据：效果并不总是正向

arXiv 论文 MCPGauge（2508.12566）是目前最系统的实证研究：

> **6个商业LLM × 30套MCP工具 × 约20,000次API调用 = $6,000+ 成本**

核心发现：

| 维度 | 发现 |
|---|---|
| **Proactivity（主动调用）** | LLM 经常该用工具时不用，不该用时乱用 |
| **Compliance（指令遵循）** | 不总是按照 tool-use 指令操作 |
| **Effectiveness（任务效果）** | MCP 集成**并不总是**提升任务性能 |
| **Overhead（计算成本）** | 实际成本远超预期 |

---

## 三、"MCP 没死"的反驳

### chrlschn.dev 的核心辩护

> *"If you want to deliver standard planning prompts (skills) and standard docs across all repositories, all workflows, all teams, and all agent front-ends consistently and always up-to-date with server telemetry, then MCP prompts and resources IS that delivery mechanism."*

他指出"MCP is dead"说法的**认知偏差**：

- 对于 solo vibe-coder（个人快速原型），Direct API / CLI 确实更简单
- 但**对于企业和团队**，MCP 的以下特性无可替代：
  - **Telemetry**：工具使用数据可观测，能衡量哪些工具真正有效
  - **Security governance**：集中管理认证和权限
  - **Schema + standards**：跨团队一致性
  - **Automatic content sync**：Server 更新后 Client 自动同步

### Medium 文章的修正立场

标题就是答案：**"MCP Isn't Dead. But It's Not the Default Answer Anymore."**

意思是：MCP 不再是"所有 Agent 集成问题的默认解"，但它在自己适合的战场（企业级、云端、多团队协作）依然坚挺。

---

## 四、nuance 的最终判断

**"MCP is dead" 是一个过度简化的叙事**，更准确的描述是：

> **MCP 作为"万能 Agent 集成方案"已经死亡；但作为"企业级标准化协议层"依然活着，而且是目前最好的选择。**

| 场景 | 结论 |
|---|---|
| Solo 开发者快速集成 1-2 个服务 | Direct API / CLI 更轻量 |
| 云端多 Agent + 多服务 + 企业团队 | **MCP 仍是最佳选择**，且壁垒会越来越高 |
| 超大规模 API（AWS、Cloudflare） | Code Orchestration 模式绕开 MCP 的局限 |
| 需要强安全审计和可观测性 | **MCP 的 telemetry 是刚需**，其他方案做不到 |
| 简单的一次性脚本任务 | MCP 的前期投入不划算 |

---

## 五、对 Anthropic 博文的影响

回到 Anthropic 那篇 [《Building agents that reach production systems with MCP》](https://claude.com/blog/building-agents-that-reach-production-systems-with-mcp)——它描述的那些**设计模式**（Tool Search 节省 85% tokens、Programmatic Tool Calling 节省 37%、CIMD 认证、MCP Apps），其实正是对上述批评的直接回应。

Anthropic 的立场是：**问题存在，解法也在进化，MCP 的 compound effect 会在协议扩展中持续显现。**

但客观说，这更像是一场**防御性叙事**：MCP 在消费级/solo 场景的优势确实在被侵蚀，它正在收缩到企业市场这个它真正擅长的阵地。

---

## 六、结语

对在国内使用 Claude/MCP 的开发者而言，还有一个现实挑战：很多海外服务（GitHub、Slack、Google）在国内访问受限，MCP Server 的远程连接往往不稳定。这也是为什么国内 AI Agent 生态（Coze、Dify、FastGPT 等）更多走 API 直连路线的原因。

但在**有条件访问海外服务**的场景下，选择其实很清楚：

- **个人快速原型** → Direct API / CLI，别用大炮打蚊子
- **企业级云端 Agent** → MCP，而且要按 Anthropic 的设计模式把它做优秀

"MCP is dead"这波讨论，本质上是一场关于**边界在哪里**的重新校准。它没死，但它需要重新证明自己。

---

**参考来源**

- [Anthropic: Building agents that reach production systems with MCP](https://claude.com/blog/building-agents-that-reach-production-systems-with-mcp)
- [chrlschn.dev: MCP is Dead; Long Live MCP!](https://chrlschn.dev/blog/2026/03/mcp-is-dead-long-live-mcp/)
- [Medium: MCP Isn't Dead. But It's Not the Default Answer Anymore.](https://medium.com/@Micheal-Lanham/mcp-isnt-dead-but-it-s-not-the-default-answer-anymore-8b88f4ce3224)
- [arXiv: Help or Hurdle? Rethinking Model Context Protocol-Augmented LLMs (2508.12566)](https://arxiv.org/abs/2508.12566)
- [Scalifiai: Six Fatal Flaws of the Model Context Protocol](https://www.scalifiai.com/blog/model-context-protocol-flaws-2025)
- [AmberSearch: 4 Drawbacks of MCP](https://ambersearch.de/en/limitations-model-context-protocol)
