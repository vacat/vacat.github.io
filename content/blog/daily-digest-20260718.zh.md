---
title: "AI 博客每日精选 — 2026-07-18"
date: 2026-07-18T00:23:11+08:00
tags: [文章摘要, 日报, openai, llm, apple]
categories: ["技术日报"]
series: []
featured: false
summary: "今日AI领域密集发布多款大模型：Moonshot推出首个开放3T参数的Kimi K3，Thinking Machines Lab开源混合专家模型Inkling，苹果智能获批入华并携手阿里百度，反映"
---

今日AI领域密集发布多款大模型：Moonshot推出首个开放3T参数的Kimi K3，Thinking Machines Lab开源混合专家模型Inkling，苹果智能获批入华并携手阿里百度，反映出模型开源与多端部署成为竞争新焦点。平台生态方面，谷歌与Epic和解意味着Android将向第三方应用商店开放，同时苹果与OpenAI的法律纠纷持续发酵，显示AI落地面临监管与商业利益的多重博弈。

<!--more-->


> 来自 Karpathy 推荐的 92 个顶级技术博客，AI 精选 Top 10

## 🏆 今日必读

🥇 **Kimi K3：首个开放3T参数模型与Pelican基准的启示**

[Kimi K3, and what we can still learn from the pelican benchmark](https://simonwillison.net/2026/Jul/16/kimi-k3/#atom-everything) — simonwillison.net · 20 小时前 · 🤖 AI / ML

> Moonshot AI发布Kimi K3，参数规模达2.8万亿，被称为首个"开放3T级模型"。根据其自报基准测试，Kimi K3在多数指标上超越Claude Opus 4.8 max和GPT-5.5 high，但落后于Claude Fable 5和GPT-5.6 Sol。在私有长时知识工作评估中，Kimi K3达到Elo 1547分。

💡 **为什么值得读**: 了解中国AI实验室最新大模型进展及开放权重策略的重要参考

🏷️ Kimi K3, Moonshot AI, LLM, parameters

🥈 **Inkling：Thinking Machines Lab发布的开源权重模型**

[Inkling: Our open-weights model](https://simonwillison.net/2026/Jul/16/inkling/#atom-everything) — simonwillison.net · 1 天前 · 🤖 AI / ML

> 由Mira Murati创立的Thinking Machines Lab发布首个开源权重模型Inkling，这是一个拥有975B总参数（41B活跃）的混合专家Transformer，采用Apache-2.0许可，支持多模态（文本、图像、音频、视频），训练数据达45万亿token。团队还承诺发布Inkling-Small（276B/12B活跃），但仍在测试中。

💡 **为什么值得读**: 前OpenAI高管创业后的首个开源大模型，了解其技术路线和数据透明度

🏷️ Inkling, open-weights, MoE, LLM

🥉 **Putering Firefox：浏览器在WebAssembly中运行**

[Firefox in WebAssembly](https://simonwillison.net/2026/Jul/16/firefox-in-webassembly/#atom-everything) — simonwillison.net · 16 小时前 · 🛠 工具 / 开源

> Puter团队成功将Firefox编译为WebAssembly，使整个浏览器能在另一个浏览器中运行。该项目选择Firefox/Gecko因其强大的单进程支持，消耗约25000美元的Claude Opus和Fable令牌，但通过Max订阅计划实际成本更低。演示通过Wisp协议经WebSocket传输所有流量。

💡 **为什么值得读**: WebAssembly能力的极致展示，了解浏览器虚拟化技术的最新突破

🏷️ Firefox, WebAssembly, browser

---

## 📊 数据概览

| 扫描源 | 抓取文章 | 时间范围 | 精选 |
|:---:|:---:|:---:|:---:|
| 87/92 | 2586 篇 → 40 篇 | 48h | **10 篇** |

### 分类分布

```mermaid
pie showData
    title "文章分类分布"
    "🤖 AI / ML" : 6
    "🛠 工具 / 开源" : 2
    "⚙️ 工程" : 2
```

### 高频关键词

```mermaid
xychart-beta horizontal
    title "高频关键词"
    x-axis ["openai", "llm", "apple", "kimi k3", "moonshot ai", "parameters", "inkling", "open-weights", "moe", "firefox", "webassembly", "browser"]
    y-axis "出现次数" 0 --> 5
    bar [3, 2, 2, 1, 1, 1, 1, 1, 1, 1, 1, 1]
```

<details>
<summary>📈 纯文本关键词图（终端友好）</summary>

```
openai       │ ████████████████████ 3
llm          │ █████████████░░░░░░░ 2
apple        │ █████████████░░░░░░░ 2
kimi k3      │ ███████░░░░░░░░░░░░░ 1
moonshot ai  │ ███████░░░░░░░░░░░░░ 1
parameters   │ ███████░░░░░░░░░░░░░ 1
inkling      │ ███████░░░░░░░░░░░░░ 1
open-weights │ ███████░░░░░░░░░░░░░ 1
moe          │ ███████░░░░░░░░░░░░░ 1
firefox      │ ███████░░░░░░░░░░░░░ 1
```

</details>

### 🏷️ 话题标签

**openai**(3) · **llm**(2) · **apple**(2) · kimi k3(1) · moonshot ai(1) · parameters(1) · inkling(1) · open-weights(1) · moe(1) · firefox(1) · webassembly(1) · browser(1) · lawsuit(1) · apple intelligence(1) · china(1) · baidu(1) · alibaba(1) · grok-build(1) · open source(1) · cli(1)

---

## 🤖 AI / ML

### 1. Kimi K3：首个开放3T参数模型与Pelican基准的启示

[Kimi K3, and what we can still learn from the pelican benchmark](https://simonwillison.net/2026/Jul/16/kimi-k3/#atom-everything) — **simonwillison.net** · 20 小时前 · ⭐ 25/30

> Moonshot AI发布Kimi K3，参数规模达2.8万亿，被称为首个"开放3T级模型"。根据其自报基准测试，Kimi K3在多数指标上超越Claude Opus 4.8 max和GPT-5.5 high，但落后于Claude Fable 5和GPT-5.6 Sol。在私有长时知识工作评估中，Kimi K3达到Elo 1547分。

🏷️ Kimi K3, Moonshot AI, LLM, parameters

---

### 2. Inkling：Thinking Machines Lab发布的开源权重模型

[Inkling: Our open-weights model](https://simonwillison.net/2026/Jul/16/inkling/#atom-everything) — **simonwillison.net** · 1 天前 · ⭐ 25/30

> 由Mira Murati创立的Thinking Machines Lab发布首个开源权重模型Inkling，这是一个拥有975B总参数（41B活跃）的混合专家Transformer，采用Apache-2.0许可，支持多模态（文本、图像、音频、视频），训练数据达45万亿token。团队还承诺发布Inkling-Small（276B/12B活跃），但仍在测试中。

🏷️ Inkling, open-weights, MoE, LLM

---

### 3. Dithering播客：苹果起诉OpenAI的不同视角

[Dithering: ‘Apple Sues OpenAI’](https://dithering.passport.online/member/episode/apple-sues-open-ai) — **daringfireball.net** · 16 小时前 · ⭐ 24/30

> Dithering播客探讨苹果对OpenAI的诉讼，主持人提供了与主流不同的分析观点。该播客每周两集，每集15分钟，平时需付费订阅，此次特别免费发布。

🏷️ Apple, OpenAI, lawsuit

---

### 4. 苹果智能获准进入中国：采用阿里百度AI模型

[Apple Intelligence OK’d to Launch in China, Using AI Models from Baidu and Alibaba](https://www.scmp.com/tech/policy/article/3360685/china-approves-apple-intelligence-phones-alibaba-baidu-emerging-partners) — **daringfireball.net** · 1 天前 · ⭐ 24/30

> 中国监管机构批准苹果在中国iPhone上推出Apple Intelligence服务，阿里巴巴和百度成为技术合作伙伴。阿里Qwen大模型将被整合到iOS、iPadOS、macOS和visionOS中，提供文本和图像生成等功能。该许可与三星、华为等六个智能手机AI服务一同批准。

🏷️ Apple Intelligence, China, Baidu, Alibaba

---

### 5. OpenAI回应苹果商业秘密诉讼

[OpenAI Takes a Second Crack at a Response to Apple’s Trade Secret Theft Lawsuit](https://www.bloomberg.com/news/articles/2026-07-14/openai-says-it-s-not-aware-of-any-evidence-that-apple-lawsuit-has-merit) — **daringfireball.net** · 20 小时前 · ⭐ 23/30

> OpenAI就苹果的诉讼发表声明，称"不了解任何证据表明该诉讼有依据"，但未直接否认诉讼有效性。声明强调相信公平竞争和人们的工作自由选择，专注于构建赋能用户的创新技术。

🏷️ OpenAI, Apple, response

---

### 6. OpenAI研发可移动无屏幕AI伴侣音箱

[Gurman on OpenAI’s Upcoming Hardware Product: ‘Movable, Screenless Speaker Built as AI Companion’](https://www.bloomberg.com/news/articles/2026-07-14/openai-s-first-device-will-be-moveable-screenless-speaker-built-as-ai-companion?accessToken=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJzb3VyY2UiOiJTdWJzY3JpYmVyR2lmdGVkQXJ0aWNsZSIsImlhdCI6MTc4NDA2MjAxMywiZXhwIjoxNzg0NjY2ODEzLCJhcnRpY2xlSWQiOiJUSTYwSllUOU5KTFMwMCIsImJjb25uZWN0SWQiOiJDNEVEQ0FFMUZBMDU0MEJFQTI0QTlGMjExQzFFOTA4MCJ9.DfRN0afk0TFIaHFw9zEKYjehnfMsZfKC7gPoVos8WPI&amp;leadSource=article-gifting) — **daringfireball.net** · 1 天前 · ⭐ 23/30

> 据彭博社报道，OpenAI首款硬件产品是可移动、无屏幕的音箱，定位为AI伴侣，具备类似人类的个性和连接能力。设备包含可自主移动的机械元件，创造"有生命"的感觉，还可读取个人邮件等信息以更好理解用户。配备可充电电池，可在家中各房间移动。

🏷️ OpenAI, hardware, AI companion

---

## 🛠 工具 / 开源

### 7. Putering Firefox：浏览器在WebAssembly中运行

[Firefox in WebAssembly](https://simonwillison.net/2026/Jul/16/firefox-in-webassembly/#atom-everything) — **simonwillison.net** · 16 小时前 · ⭐ 24/30

> Puter团队成功将Firefox编译为WebAssembly，使整个浏览器能在另一个浏览器中运行。该项目选择Firefox/Gecko因其强大的单进程支持，消耗约25000美元的Claude Opus和Fable令牌，但通过Max订阅计划实际成本更低。演示通过Wisp协议经WebSocket传输所有流量。

🏷️ Firefox, WebAssembly, browser

---

### 8. Mermaid转ASCII艺术图工具发布

[Mermaid to ASCII art (mermaid-ascii)](https://simonwillison.net/2026/Jul/16/mermaid-ascii/#atom-everything) — **simonwillison.net** · 1 天前 · ⭐ 21/30

> Simon Willison基于AlexanderGrooff的Go库创建了Mermaid转ASCII工具，支持颜色显示。该工具可将Mermaid图表转换为ASCII艺术图，支持流程图、子图、多行标签、序列图、循环和并行等多种图表类型。

🏷️ Mermaid, ASCII art, converter

---

## ⚙️ 工程

### 9. xAI开源grok-build应对隐私争议

[xai-org/grok-build, now open source](https://simonwillison.net/2026/Jul/15/grok-build/#atom-everything) — **simonwillison.net** · 1 天前 · ⭐ 23/30

> xAI的grok CLI工具因运行时会将整个目录上传到Google Cloud存储桶而引发社区强烈反对，用户报告SSH密钥、密码库、照片等全部被上传。xAI随后删除了这些数据，并宣布将grok-build整个代码库以Apache 2.0许可证开源，试图平息争议。

🏷️ grok-build, open source, CLI

---

### 10. 谷歌与Epic和解：第三方应用商店下周上线

[Google and Epic Give Up Fighting — Third-Party Android App Stores Are Coming Next Week](https://www.theverge.com/policy/965792/google-epic-withdraw-injunction-third-party-app-stores-coming-google-play?view_token=eyJhbGciOiJIUzI1NiJ9.eyJpZCI6IkZpdmhlVXFoV0giLCJwIjoiL3BvbGljeS85NjU3OTIvZ29vZ2xlLWVwaWMtd2l0aGRyYXctaW5qdW5jdGlvbi10aGlyZC1wYXJ0eS1hcHAtc3RvcmVzLWNvbWluZy1nb29nbGUtcGxheSIsImV4cCI6MTc4NDczNTA1NSwiaWF0IjoxNzg0MzAzMDU1fQ.zPHCDeRVkCOK73sdt6bKC2evAofTI582EsJ0N-rk79g) — **daringfireball.net** · 29 分钟前 · ⭐ 23/30

> 谷歌与Epic达成协议，撤回修改禁令的动议，允许第三方应用商店进入Android生态。谷歌此前宣布将在今年晚些时候在全球推出侧载注册应用商店计划，最先从新版Android开始。这意味着用户将获得更多应用分发渠道选择和更低价格。

🏷️ Android, app stores, Epic, Google

---

*生成于 2026-07-18 16:23 | 扫描 87 源 → 获取 2586 篇 → 精选 10 篇*
*基于 [Hacker News Popularity Contest 2025](https://refactoringenglish.com/tools/hn-popularity/) RSS 源列表，由 [Andrej Karpathy](https://x.com/karpathy) 推荐*
*由「懂点儿AI」制作，欢迎关注同名微信公众号获取更多 AI 实用技巧 💡*
