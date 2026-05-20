<!-- generated: 2026-05-21T03:00:24.661671+09:00 -->
<!-- primary_topic: wiki/maps/ai-adoption-roi-and-capability-investment.md -->
# NotebookLM Podcast Source: AI Adoption ROI and Capability Investment

- Date: 2026-05-21
- Primary topic: `wiki/maps/ai-adoption-roi-and-capability-investment.md`
- Purpose: NotebookLM Audio Overviewに読ませるためのKB由来ソースページ

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

### 2. Leading engineering indicators
Software delivery metrics provide the bridge from local productivity to business value:
- throughput: lead time, deployment frequency, feature flow
- instability: change failure rate, failed deployment recovery time, rework, downtime

### 3. J-Curve, verification tax, and instability tax
Early adoption can produce a temporary productivity dip. The dip is driven by learning, workflow adaptation, the verification tax created by more generated output, and the instability tax from failed changes, rework, downtime, or recovery work. This should be budgeted and monitored rather than hidden.

### 4. Demand expansion / option value
If agentic engineering lowers the cost of producing software, organizations may request more software: internal tools, workflow automation, prototypes, customer-specific features, and experiments that previously did not clear the cost threshold. This is [[../concepts/agentic-jevons-paradox.md]]. Treat it as an upside scenario, not a default assumption, because platform vendors benefit from this narrative.

### 5. Value drivers
The DORA model translates engineering changes into:
- headcount reinvestment capacity / avoided hiring
- revenue from extra successful feature deployments
- revenue or cost avoided by reducing downtime
- qualitative developer-experience and retention arguments

### 6. Scenario discipline
The model should be treated as a high-uncertainty conversation starter. Conservative, base, and optimistic scenarios are safer than a single ROI number.

## Relation to existing maps
- Extends [[e

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

### Simon Willison — Thoughts on GitLab Act 2

Source: `wiki/sources/simon-willison-gitlab-act-2.md`

# Simon Willison — Thoughts on GitLab Act 2

## Metadata
- Raw path: `raw/articles/simon-willison-gitlab-act-2-2026-05-11.md`
- Original/source URL: https://simonwillison.net/2026/May/11/gitlab-act-2/
- Linked primary announcement: https://about.gitlab.com/blog/gitlab-act-2/
- Author: Simon Willison
- Published: 2026-05-11
- Fetched/ingested: 2026-05-12
- Source type: link-blog commentary on GitLab strategy announcement
- Evidence strength: medium for Simon's interpretation and the quoted GitLab claims; lower for forward-looking market predictions because they are strategic/business forecasts and GitLab has a direct commercial incentive

## Summary
Simon Willison reads GitLab's “Act 2” announcement as more than a workforce-reduction note: it is also an organizational redesign and market thesis for the agentic engineering era. The key useful frame is GitLab's belief that cheaper software production will expand demand for software and for developer-platform seats, not merely reduce developer headcount. Simon connects this to a Jevons-paradox-style optimism while explicitly warning that GitLab's incentives make the claim worth discounting.

## Key claims
- GitLab's agentic-era restructuring combines workforce reduction, geographic consolidation, fewer management layers, smaller empowered R&D teams, and a new values framework.
- Flattening management and “player-coach” management a

### Coding-Agent Cognitive Debt and Review Capacity

Source: `wiki/maps/coding-agent-cognitive-debt-and-review-capacity.md`

# Coding-Agent Cognitive Debt and Review Capacity

## Purpose
Map sources that warn coding-agent throughput can outrun human comprehension, review skill, and implementation judgment.

## Core thesis
The central risk in agentic coding is not only that models make mistakes. It is that teams may produce and accept more code than they can understand, while also weakening the skills required to detect mistakes. Good harnesses must therefore preserve human review capacity and implementation contact, not merely automate more steps.

## Main patterns

### 1. Throughput beyond review capacity
Coding agents can generate large diffs quickly. If review remains shallow, the system shifts risk from typing speed to hidden architectural and maintainability debt.

### 2. Supervision paradox
The human supervisor needs coding, debugging, and architectural skill to judge agent output. Heavy agent use can reduce hands-on practice and erode the very skill required for supervision.

### 3. Coding as design discovery
Cheap implementation strengthens the case for using code as a probe: writing code surfaces choices and improves the spec, but only if the learning is captured.

For many developers, writing code is part of planning. Types, pseudo-code, module boundaries, and small implementation attempts are not low-level busywork; they are design probes that expose ambiguity.

### 4. Vendor and cost depe

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

## Podcastで掘るとよい問い

- このテーマは、どの現場課題を減らすための考え方か？
- 人間が見るべき判断軸と、エージェントに任せられる作業はどう分かれるか？
- 導入するときに失敗しやすい雑な抽象化は何か？
- 既存の開発・レビュー・ナレッジ運用にどう接続できるか？

## NotebookLMに期待する話し方メモ

- 日本語の自然な技術雑談。硬い講義ではなく、実務で悩む2人の会話にする。
- 単なる要約ではなく、具体的な現場の使いどころ、危ない誤解、次の一手まで話す。
- 結論を急ぎすぎず、問いを立てながら深掘りする。
