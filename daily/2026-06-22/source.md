<!-- generated: 2026-06-22T03:00:13.908431+09:00 -->
<!-- primary_topic: wiki/maps/x-bookmarks-backfill-2026-05-10.md -->
# X Bookmarks Backfill — 2026-05-10

- Date: 2026-06-22
- Primary topic: `wiki/maps/x-bookmarks-backfill-2026-05-10.md`
- Purpose: KB由来の材料を、人間がHTMLで読んで理解しやすい読み物にする

## 今日のランダムテーマ

X Bookmarks Backfill — 2026-05-10 を入口に、関連するKBノートをつないで実務上の論点を整理する。

## 主要ソース抜粋

### X Bookmarks Backfill — 2026-05-10

# X Bookmarks Backfill — 2026-05-10

## Scope
- Requested by Masaki: ingest past X bookmarks, aiming for roughly six months where possible.
- Raw capture: `raw/x-bookmarks/2026-05-10/`
- X API result: 199 unique bookmarked posts across 2 pages.
- API stop condition: no `next_token` after page 2. The API response did **not** expose bookmark-created timestamps, so this backfill cannot prove six calendar months of bookmark actions.
- Tweet-created date range in returned data: 2026-02-19T19:54:49.000Z → 2026-05-10T01:22:53.000Z.
- Existing compiled source notes detected by post id: 91.
- New bookmark-level source notes created: 108.

## Synthesis
Masaki's bookmark signal remains heavily centered on agent harnesses, coding-agent operation, context/memory systems, evaluation/safety, and AI adoption patterns. The backfill adds breadth rather than a single new thesis: many sources are lightweight pointers that should be enriched only when they become relevant to a question or daily digest.

## Backfill clusters

### Agent harness / coding-agent operations
- ParseBench: A Document Parsing Benchmark for AI Agents — @yohei_kikuta (2026-05-10) https://x.com/yohei_kikuta/status/2053284607098052989
- Install These Skills Before Codex Touches Your Xcode Project — @PaulSolt (2026-04-10) https://x.com/PaulSolt/status/2042716870512353294
- Agent Harness Engineering — @addyosmani (2026-05-09) https://x.com/addyosmani/status/2053231239721885918
- Peekaboo documentation — Peekaboo — @steipete (2026-05-09) https://x.com/steipete/status/2053114837698249190
- HTML is the new markdown. I've stopped writing markdown files for almost everything and sw… — @trq212 (2026-05-08) https://x.com/trq212/status/2052811606032269638
- LLM Wikis + HTML Artifacts are insanely powerful. You should seriously consider this in yo… — @omarsar0 (2026-05-08) https://x.com/omarsar0/status/2052850591584383177
- Using Claude Code: The Unreasonable Effectiveness of HTML — @trq212 (2026-05-08) https://x.com/trq212/status/2052809885763747935
- Introducing GPT-Realtime-2 in the API: our most intelligent voice model yet, bringing GPT-… — @OpenAI (2026-05-07) https://x.com/OpenAI/status/2052438194625593804
- Our new voice models are now available in the Realtime API: 🎙️ GPT-Realtime-2: Build produ… — @OpenAI (2026-05-07) https://x.com/OpenAI/status/2052438196454379986
- gemini 3.1 flash-lite is here it's our most cost-efficient model, optimized for high-volum… — @GoogleAIStudio (2026-05-07) https://x.com/GoogleAIStudio/status/2052453828272812310
- Codex can now take on more of your browser dev work. With the 

## 関連ノートからの補助材料

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

### Coding-Agent Harness Patterns

Source: `wiki/maps/coding-agent-harness-patterns.md`

# Coding-Agent Harness Patterns

## Purpose
Synthesize practical harness patterns for coding-agent workflows using the KB's control vocabulary plus a concrete real-world operator example.

## Core claim
A coding-agent workflow becomes harness engineering when quality and reliability depend on the surrounding artifacts, controls, and review loops rather than on the model prompt alone.

## Pattern 1. Plan as handoff artifact
Use a session-scoped plan file such as `plan.md` as a durable handoff contract.

Why it matters:
- makes intent inspectable
- supports context resets and reviewer alignment
- creates a stable object for verifier agents to critique

## Pattern 2. Verifier split without full multi-agent overhead
Use heavy thinking for hard, bounded reasoning: spawn independent temporary thinkers, then have one deliberator critique and synthesize their outputs.

Use a second agent or model mainly for plan review or implementation review instead of duplicating the whole execution role.

Why it matters:
- captures evaluator benefits cheaply
- reduces self-evaluation bias
- preserves a simple operator mental model

## Pattern 3. Environment bootstrapping before task work
Prepare a runnable repository baseline before asking an agent to solve future coding tasks.

Why it matters:
- prevents setup failures from consuming the task budget
- gives tests, linters, and smoke commands a mea

### Harness Engineering Vendor / Practitioner Comparison

Source: `wiki/maps/harness-engineering-vendor-comparison.md`

# Harness Engineering Vendor / Practitioner Comparison

## Purpose
Compare how different sources frame harness engineering, what they optimize for, and what distinctive mechanisms they emphasize.

## Source anchors
- [[../sources/openai-harness-engineering.md]]
- [[../sources/openai-codex-plugin-cc-github.md]]
- [[../sources/codex-subagents-docs.md]]
- [[../sources/anthropic-effective-harnesses-long-running-agents.md]]
- [[../sources/anthropic-harness-design-long-running-apps.md]]
- [[../sources/anthropic-claude-code-on-the-web-docs.md]]
- [[../sources/anthropic-claude-code-skills-docs.md]]
- [[../sources/anthropic-claude-code-web-scheduled-tasks-docs.md]]
- [[../sources/cursor-3-blog.md]]
- [[../sources/anthropic-claude-code-large-codebases.md]]
- [[../sources/anthropic-2026-agentic-coding-trends-report.md]]
- [[../sources/gargetisha-openclaw-under-the-hood-x-article.md]]

## Comparison axes

### OpenAI
- Focus: repository design, machine-enforced invariants, agent-recognizable context, continuous cleanup, and cross-agent review / delegation
- Distinctive emphasis: docs as map, custom linters, structured plans, architecture constraints, review loops, interoperable agent tooling, and explicit model-tier routing via subagents
- Main contribution: shows harness engineering as both a production engineering discipline and a composable ecosystem where one agent can check or extend a

### Harness Engineering

Source: `wiki/concepts/harness-engineering.md`

---
aliases:
  - Harness Engineering
---

# Harness Engineering

## Definition
The design of the environment, artifacts, controls, tooling, and feedback loops around an agent so that it can produce more reliable results over time.

## Why It Matters
As agents become more capable, performance depends less on the model alone and more on the structure that surrounds it.

## Related Concepts
- [[guides and sensors]]
- [[agent recognizable repository]]
- [[structured handoff artifacts]]
- [[machine-checkable invariants]]
- [[heavy-thinking.md]]

## Supporting Sources
- [[../sources/openai-harness-engineering.md]]
- [[../sources/martin-fowler-harness-engineering.md]]
- [[../sources/gota-purpose-first-harness-design-speakerdeck.md]]
- [[../sources/rkaga-how-to-approach-harness-engineering-speakerdeck.md]]
- [[../sources/rkaga-what-harness-engineering-is-and-is-not-zenn.md]]
- [[../sources/sergicalsix-harness-engineering-overview-design-philosophy-speakerdeck.md]]
- [[../sources/yuukiyo-ai-dlc-deep-dive-speakerdeck.md]]
- [[../sources/anthropic-effective-harnesses-long-running-agents.md]]
- [[../sources/anthropic-harness-design-long-running-apps.md]]
- [[../sources/spillwave-ai-coding-hangover-harness-engineering.md]]
- [[../sources/anthropic-harnessing-claudes-intelligence.md]]
- [[../sources/addyosmani-agent-harness-engineering-x-2026-05-09.md]]
- [[../sources/kevin-gu-autoagent-x-th

## 次に考えるとよさそうな問い

- このテーマは、どの現場課題を減らすための考え方か？
- 人間が見るべき判断軸と、エージェントに任せられる作業はどう分かれるか？
- 導入するときに失敗しやすい雑な抽象化は何か？
- 既存の開発・レビュー・ナレッジ運用にどう接続できるか？
