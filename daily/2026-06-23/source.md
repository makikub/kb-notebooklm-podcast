<!-- generated: 2026-06-23T03:00:12.086144+09:00 -->
<!-- primary_topic: wiki/maps/ai-adoption-roi-and-capability-investment.md -->
# AI Adoption ROI and Capability Investment

- Date: 2026-06-23
- Primary topic: `wiki/maps/ai-adoption-roi-and-capability-investment.md`
- Purpose: KB由来の材料を、人間がHTMLで読んで理解しやすい読み物にする

## 今日のランダムテーマ

AI Adoption ROI and Capability Investment を入口に、関連するKBノートをつないで実務上の論点を整理する。

## 主要ソース抜粋

### AI Adoption ROI and Capability Investment

# AI Adoption ROI and Capability Investment

## Purpose
Map how AI-assisted software development becomes financial value only when capability investments let the organization absorb faster generation safely.

## Core thesis
AI ROI is not a direct function of model quality or code volume. It is a system outcome: AI adoption must be mediated by internal platforms, context/data quality, trust, user focus, verification guardrails, and delivery metrics before it can become durable business value. The strongest upside case is not only cheaper execution of existing backlog, but Jevons-style expansion in software demand when new tools, experiments, and automations become economical.

## Path from AI adoption to ROI

### 1. Capability investment first
The first question is not “which tool?” but “can the system absorb the tool?” DORA's report emphasizes quality internal developer platforms, AI-accessible internal data, clear AI stance/trust, context engineering, user-centric focus, and automated guardrails.

### 1a. Adoption phase before transformation
Shin Suga's AI-Ops roadmap adds a rollout operator's lens: the right move changes with actual AI usage rate. At low usage, measure and activate early adopters; at medium usage, build literacy and strong department-specific use cases; once usage is broad enough, context/data loops and workflow transformation become more credible. This prevents ROI models from assuming workflow redesign before the organization has enough lived AI literacy to specify realistic changes.

### 2. Leading engineering indicators
Software delivery metrics provide the bridge from local productivity to business value:
- throughput: lead time, deployment frequency, feature flow
- instability: change failure rate, failed deployment recovery time, rework, downtime

### 3. J-Curve, verification tax, and instability tax
Early adoption can produce a temporary productivity dip. The dip is driven by learning, workflow adaptation, the verification tax created by more generated output, and the instability tax from failed changes, rework, downtime, or recovery work. This should be budgeted and monitored rather than hidden.

### 4. Demand expansion / option value
If agentic engineering lowers the cost of producing software, organizations may request more software: internal tools, workflow automation, prototypes, customer-specific features, and experiments that previously did not clear the cost threshold. This is [[../concepts/agentic-jevons-paradox.md]]. Treat it as an upside scenario, not a default assumption, because platform vendors benefit from this n

## 関連ノートからの補助材料

### DORA — The ROI of AI-assisted Software Development

Source: `wiki/sources/dora-roi-ai-assisted-software-development.md`

# DORA — The ROI of AI-assisted Software Development

## Metadata
- Raw path: `raw/articles/dora-roi-ai-assisted-software-development-2026.md`
- Original/source URL: attached Markdown export; report points to latest-version page `https://dora.dev/vc/airoi/?v=2026.1` and calculator `https://dora.dev/ai/roi/calculator`
- Authors/contributors: DORA + Google Cloud delta team; named authors include Eva Dong, Andre Ellis Jr., Nathen Harvey, Vivian Hu, Ursula Löbbert-Passing, Eric Maxwell, and Aaron Wanjala
- Published/version: v2026.1; citations retrieved February 2026
- Fetched/ingested: 2026-05-07 from uploaded Markdown file
- License: CC BY-NC-SA 4.0 as stated in the report
- Source type: industry research / ROI modeling report / practitioner framework
- Evidence strength: high for DORA/Google's stated framework and reported 2025 DORA findings; medium for ROI calculator assumptions because the report explicitly frames them as high-uncertainty conversation starters

## Summary
DORA and Google Cloud argue that AI-assisted software development ROI depends less on buying AI tools and more on the health of the engineering system that absorbs them. AI is treated as an amplifier: it magnifies strong internal platforms, clear workflows, user focus, and automated guardrails, but also magnifies brittle pipelines, manual review bottlenecks, fragmented data, and organizational friction. The r

### Anthropic — 2026 Agentic Coding Trends Report

Source: `wiki/sources/anthropic-2026-agentic-coding-trends-report.md`

# Anthropic — 2026 Agentic Coding Trends Report

## Metadata
- Raw PDF: `raw/pdfs/anthropic-2026-agentic-coding-trends-report.pdf`
- Extracted text: `raw/pdfs/anthropic-2026-agentic-coding-trends-report.txt`
- Original URL: https://resources.anthropic.com/hubfs/2026%20Agentic%20Coding%20Trends%20Report.pdf
- Landing page: https://resources.anthropic.com/2026-agentic-coding-trends-report
- Publisher: Anthropic
- Source type: vendor trend report / customer-case narrative
- Pages: 18
- Extracted: 2026-05-04
- Evidence strength: medium for Anthropic's product/market framing and named case studies; low-to-medium for forward-looking predictions because they are explicitly predictions, not certainties

## Summary
Anthropic predicts that agentic coding in 2026 will move software development from direct code-writing toward orchestrating coding agents, while still requiring active supervision, validation, and human judgment. The report groups eight trends into foundation, capability, and impact categories: SDLC changes, multi-agent coordination, long-running agents, scaled human oversight, new surfaces and users, productivity economics, non-technical adoption, and dual-use security risk.

The report's most important nuance is collaborative rather than replacement framing: developers reportedly use AI in roughly 60% of their work, but can fully delegate only 0–20% of tasks. Anthropic argu

### Agent Harness Landscape

Source: `wiki/maps/agent-harness-landscape.md`

# Agent Harness Landscape

## Purpose
This map connects the emerging idea of harness engineering across several sources and shows how it fits into the broader LLM agents knowledge base.

## Core thesis
Agent performance is not just a function of the model. It depends heavily on the harness: the repository structure, controls, artifacts, tests, review loops, and orchestration patterns around the model.

## Source anchors
- [[../sources/karpathy-personal-llm-kb.md]]
- [[../sources/openai-harness-engineering.md]]
- [[../sources/anthropic-effective-harnesses-long-running-agents.md]]
- [[../sources/anthropic-harness-design-long-running-apps.md]]
- [[../sources/anthropic-claude-code-on-the-web-docs.md]]
- [[../sources/aws-japan-aws-blocks-ai-agent-intro-zenn.md]]
- [[../sources/gargetisha-openclaw-under-the-hood-x-article.md]]
- [[../sources/djfarrelly-agent-loop-architecture-x.md]]
- [[../sources/jason-liu-codex-maxxing-heartbeats.md]]
- [[../sources/openai-chatgpt-memory-dreaming-x-2026-06-04.md]]
- [[../sources/voxyz-ai-openclaw-memory-wiki-x.md]]
- [[../sources/claudeai-introducing-claude-design-by-anthropic-labs-make-prototypes-slides-and-x-2026-04-17.md]]
- [[../sources/figma-figma-mcp-server-slides-figjam-make-x-2026-06-16.md]]

## Main dimensions

### 1. Guidance before action
- feedforward controls
- short map-like instructions
- architecture docs
- explicit plans
- feature 

### AI ROI Model

Source: `wiki/concepts/ai-roi-model.md`

---
aliases:
  - AI ROI Model
  - ROI of AI-assisted Software Development
  - AI Value Model
---

# AI ROI Model

## Definition
A structured way to estimate the return on AI-assisted software development by linking AI adoption to delivery metrics, business value, and adoption costs.

## Why It Matters
AI productivity claims are not enough for enterprise adoption. A credible model connects engineering indicators to financial outcomes while accounting for hard costs, learning costs, instability, and uncertainty.

## Related Concepts
- [[ai-adoption-j-curve]]
- [[verification-tax]]
- [[evidence-quality]]
- [[organizational-intent-clarity]]
- [[product-responsibility-distribution]]
- [[sustainable-ai-work]]
- [[agentic-jevons-paradox]]

## Supporting Sources
- [[../sources/dora-roi-ai-assisted-software-development.md]]
- [[../sources/simon-willison-gitlab-act-2.md]]
- [[../sources/simon-willison-product-market-fit.md]]
- [[../sources/tsunoda-legalon-ai-driven-hiring-token-budget-x-2026-05-20.md]]
- [[../sources/itmedia-github-copilot-pricing-backlash-x-2026-06-03.md]]
- [[../sources/shin-suge-ai-ops-roadmap-behavior-change-note-2026-06-09.md]]

## Model Shape
- Value: headcount reinvestment capacity, revenue from extra feature deployments, and revenue/cost avoided from downtime changes.
- Investment: direct hard costs for licenses, usage, infrastructure, and enablement, plus J-Curv

## 次に考えるとよさそうな問い

- このテーマは、どの現場課題を減らすための考え方か？
- 人間が見るべき判断軸と、エージェントに任せられる作業はどう分かれるか？
- 導入するときに失敗しやすい雑な抽象化は何か？
- 既存の開発・レビュー・ナレッジ運用にどう接続できるか？
