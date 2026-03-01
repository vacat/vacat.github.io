---
title: "AI 博客每日精选 — 2026-02-28"
date: 2026-02-28T18:00:00+08:00
tags: [文章摘要, 日报, AI, 安全, TechBeacon]
series: []
featured: false
---

# 📰 AI 博客每日精选 — 2026-02-28

> 来自 Karpathy 推荐的 92 个顶级技术博客，AI 精选 Top 10

## 📝 今日看点

今日技术圈焦点集中在AI伦理争议与安全挑战两方面。AI领域，Anthropic公开拒绝美国国防部修改平台支持战争罪的要求，同时有开发者因抗议AI军事化而注销ChatGPT账户，反映出技术公司与用户对AI武器化的高度警惕；安全层面，passkey密钥绑定导致数据不可恢复的隐患引发讨论，Kimwheel僵尸网络主犯身份曝光以及苹果CSAM扫描引发的隐私法律争议也持续发酵。此外，Anthropic推出开源项目维护者免费额度计划，AI编码工具正逐步进入开发者实际工作流。

---

## 🏆 今日必读

🥇 **给达里奥的饼干？——Anthropic 与贩卖死亡**

[A Cookie for Dario? — Anthropic and selling death](https://anildash.com/2026/02/27/a-cookie-for-dario/) — anildash.com · 22 小时前 · 🤖 AI / ML

> Anthropic（Claude 的开发商）拒绝美国国防部长Pete Hegseth 要求修改其平台以支持战争罪的要求。Anthropic 首席执行官 Dario Amodei 公开表示拒绝，尽管政府将这一请求包装成用于"合法目的"，但鉴于政府此前将犯罪行为描述为合法，这一说法受到广泛质疑。

💡 **为什么值得读**: 这是关于 AI 公司如何应对政府不当技术请求的重要案例，展示科技巨头在道德抉择中的立场。

🏷️ Anthropic, AI, military, ethics

🥈 **请务必停止使用 passkey 加密用户数据**

[Please, please, please stop using passkeys for encrypting user data](https://simonwillison.net/2026/Feb/27/passkeys/#atom-everything) — simonwillison.net · 23 小时前 · 🔒 安全

> passkey 作为 FIDO 标准已广泛用于无密码登录，但其密钥绑定特性意味着用户一旦丢失 passkey，将无法恢复用它加密的数据。安全专家 Tim Cappalli 呼吁业界停止使用 passkey 加密用户数据，因为用户经常会丢失 passkey 且可能不理解他们的数据已被不可逆地加密。这与登录认证是不同场景，passkey 应仅用于身份验证而非数据加密。

💡 **为什么值得读**: 揭示了一个常见但危险的误用场景，帮助开发者避免将 passkey 应用于不适合的数据保护场景。

🏷️ passkeys, encryption, security, user data

🥉 **AI 编码怀疑论者尝试 AI 编码的详尽记录**

[An AI agent coding skeptic tries AI agent coding, in excessive detail](https://simonwillison.net/2026/Feb/27/ai-agent-coding-in-excessive-detail/#atom-everything) — simonwillison.net · 1 天前 · 🤖 AI / ML

> Max Woolf 从怀疑态度转变为实际使用 AI 编码代理，记录了一系列越来越复杂的项目：从简单的 YouTube 元数据抓取工具，逐步演进到更复杂的项目。他详细描述了每个阶段的尝试过程、遇到的问题以及 AI 代理的能力边界。

💡 **为什么值得读**: 提供了真实的 AI 编码代理实战经验，适合想了解当前 AI 编程工具实际能力的开发者参考。

🏷️ AI agents, coding, LLM, development

---

## 📊 数据概览

| 扫描源 | 抓取文章 | 时间范围 | 精选 |
|:---:|:---:|:---:|:---:|
| 81/92 | 2354 篇 → 35 篇 | 48h | **10 篇** |

### 分类分布

- 🤖 AI / ML: 4 篇
- 🔒 安全: 3 篇
- ⚙️ 工程: 2 篇
- 🛠 工具 / 开源: 1 篇

### 🏷️ 话题标签

**anthropic**(2) · **security**(2) · **ai agents**(2) · coding(2) · llm(2) · open source(2) · ai(1) · military(1) · ethics(1) · passkeys(1) · encryption(1) · user data(1) · development(1) · botnet(1) · kimwolf(1) · threat actor(1) · software development(1) · claude(1) · free(1) · apple(1)

---

## 🤖 AI / ML

### 1. 给达里奥的饼干？——Anthropic 与贩卖死亡

[A Cookie for Dario? — Anthropic and selling death](https://anildash.com/2026/02/27/a-cookie-for-dario/) — **anildash.com** · 22 小时前 · ⭐ 26/30

> Anthropic（Claude 的开发商）拒绝美国国防部长Pete Hegseth 要求修改其平台以支持战争罪的要求。Anthropic 首席执行官 Dario Amodei 公开表示拒绝，尽管政府将这一请求包装成用于"合法目的"，但鉴于政府此前将犯罪行为描述为合法，这一说法受到广泛质疑。

🏷️ Anthropic, AI, military, ethics

---

### 2. AI 编码怀疑论者尝试 AI 编码的详尽记录

[An AI agent coding skeptic tries AI agent coding, in excessive detail](https://simonwillison.net/2026/Feb/27/ai-agent-coding-in-excessive-detail/#atom-everything) — **simonwillison.net** · 1 天前 · ⭐ 24/30

> Max Woolf 从怀疑态度转变为实际使用 AI 编码代理，记录了一系列越来越复杂的项目：从简单的 YouTube 元数据抓取工具，逐步演进到更复杂的项目。他详细描述了每个阶段的尝试过程、遇到的问题以及 AI 代理的能力边界。

🏷️ AI agents, coding, LLM, development

---

### 3. AI 编码怀疑论者尝试 AI 编码的详尽记录

[An AI agent coding skeptic tries AI agent coding, in excessive detail](https://minimaxir.com/2026/02/ai-agent-coding/) — **minimaxir.com** · 1 天前 · ⭐ 24/30

> Max Woolf 从怀疑态度转变为实际使用 AI 编码代理，记录了一系列越来越复杂的项目：从简单的 YouTube 元数据抓取工具，逐步演进到更复杂的项目。他详细描述了每个阶段的尝试过程、遇到的问题以及 AI 代理的能力边界。

🏷️ AI agents, coding, LLM, software development

---

### 4. 就这样，我注销了我的 ChatGPT

[That's it, I'm cancelling my ChatGPT](https://idiallo.com/byte-size/im-cancelling-my-chatgpt-openai-account?src=feed) — **idiallo.com** · 4 小时前 · ⭐ 20/30

> 作者在阅读 Sam Altman 关于加入"战争部"、在 DoD 机密网络使用 ChatGPT 的推文后，决定注销自己的 ChatGPT 账户。作者认为这是大规模监控的入口，也是将技术用于武器部署的开端，与此前 Anthropic CEO 拒绝与 DoD 合作的立场形成对比。

🏷️ ChatGPT, surveillance, AI weapons, DoW

---

## 🔒 安全

### 5. 请务必停止使用 passkey 加密用户数据

[Please, please, please stop using passkeys for encrypting user data](https://simonwillison.net/2026/Feb/27/passkeys/#atom-everything) — **simonwillison.net** · 23 小时前 · ⭐ 24/30

> passkey 作为 FIDO 标准已广泛用于无密码登录，但其密钥绑定特性意味着用户一旦丢失 passkey，将无法恢复用它加密的数据。安全专家 Tim Cappalli 呼吁业界停止使用 passkey 加密用户数据，因为用户经常会丢失 passkey 且可能不理解他们的数据已被不可逆地加密。这与登录认证是不同场景，passkey 应仅用于身份验证而非数据加密。

🏷️ passkeys, encryption, security, user data

---

### 6. Kimwolf 僵尸网络主犯 "Dort" 是谁？

[Who is the Kimwolf Botmaster "Dort"?](https://krebsonsecurity.com/2026/02/who-is-the-kimwolf-botmaster-dort/) — **krebsonsecurity.com** · 10 小时前 · ⭐ 24/30

> 2026年1月初，KrebsOnSecurity 揭露了一名安全研究员披露的漏洞如何被用于构建 Kimwolf（全球最大最具破坏性的僵尸网络）。此后，Kimwolf 的控制者 "Dort" 对该研究员和作者发动了 DDoS、人肉搜索和邮件轰炸攻击，甚至导致特警队被派往研究员家中。本文调查了 "Dort" 的真实身份。

🏷️ botnet, security, Kimwolf, threat actor

---

### 7. 西弗吉尼亚反苹果 CSAM 诉讼将帮助恋童癖者逃脱

[West Virginia's Anti-Apple CSAM Lawsuit Would Help Child Predators Walk Free](https://www.techdirt.com/2026/02/25/west-virginias-anti-apple-csam-lawsuit-would-help-child-predators-walk-free/) — **daringfireball.net** · 1 天前 · ⭐ 22/30

> Techdirt 分析指出，如果西弗吉尼亚州胜诉并迫使苹果扫描 iCloud 上的 CSAM 内容，所有被标记的图片将成为无证政府搜索获得的证据。根据第四修正案的排除规则，辩护律师可以要求法院排除这些证据，最终反而帮助犯罪者逃脱法律制裁。

🏷️ Apple, CSAM, privacy, legal

---

## ⚙️ 工程

### 8. 利用 HTTP Range 请求二分搜索构建 Unicode 浏览器

[Unicode Explorer using binary search over fetch() HTTP range requests](https://simonwillison.net/2026/Feb/27/unicode-explorer/#atom-everything) — **simonwillison.net** · 1 天前 · ⭐ 20/30

> Simon Willison 从手机端构建了一个实验性工具，通过 HTTP Range 请求和二分搜索算法探索 Unicode 字符集。这是他在 HTTP Range 技巧方面长期研究的实际应用，也是利用 LLM 满足个人好奇心的案例。

🏷️ Unicode, HTTP, binary search, web

---

### 9. 用 Frigate 升级我的开源 Pi 监控服务器

[Upgrading my Open Source Pi Surveillance Server with Frigate](https://www.jeffgeerling.com/blog/2026/upgrading-my-open-source-pi-surveillance-server-frigate/) — **jeffgeerling.com** · 1 天前 · ⭐ 19/30

> 作者在 2024 年使用 Coral TPU 和 Axzez Interceptor 1U 机箱构建了 Pi Frigate NVR，实现 100% 本地化监控。2026年通过升级 Frigate 软件进一步提升了功能，延续了完全本地化、无云服务、无账户的隐私保护理念。

🏷️ Raspberry Pi, Frigate, NVR, open source

---

## 🛠 工具 / 开源

### 10. 大型开源项目维护者免费使用 Claude Max

[Free Claude Max for (large project) open source maintainers](https://simonwillison.net/2026/Feb/27/claude-max-oss-six-months/#atom-everything) — **simonwillison.net** · 1 天前 · ⭐ 23/30

> Anthropic 宣布为开源项目维护者免费提供价值 200美元/月的 Claude Max 20倍额度套餐，为期六个月。申请条件包括：维护 GitHub 5000+ stars 或 NPM 月下载量 100万+ 的公共仓库，或 5000+ stars 的 npm 包。

🏷️ Claude, Anthropic, open source, free

---

*生成于 2026-02-28 22:38 | 扫描 81 源 → 获取 2354 篇 → 精选 10 篇*
*基于 [Hacker News Popularity Contest 2025](https://refactoringenglish.com/tools/hn-popularity/) RSS 源列表，由 [Andrej Karpathy](https://x.com/karpathy) 推荐*
