<!-- generated: 2026-08-02T03:00:13.080297+09:00 -->
<!-- primary_topic: wiki/maps/harness-engineering-vendor-comparison.md -->
# Harness Engineering Vendor / Practitioner Comparison

- Date: 2026-08-02
- Primary topic: `wiki/maps/harness-engineering-vendor-comparison.md`
- Purpose: KB由来の材料を、人間がHTMLで読んで理解しやすい読み物にする

## 今日のランダムテーマ

Harness Engineering Vendor / Practitioner Comparison を入口に、関連するKBノートをつないで実務上の論点を整理する。

## 主要ソース抜粋

### Harness Engineering Vendor / Practitioner Comparison

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
- Main contribution: shows harness engineering as both a production engineering discipline and a composable ecosystem where one agent can check or extend another

### Cursor
- Focus: agent-first coding workspace design plus model-training environment bootstrapping
- Distinctive emphasis: multi-agent visibility, local/cloud handoff, multi-repo operation, review surfaces, harness measurement, and autoinstall loops that use earlier models to create runnable RL environments for later models
- Main contribution: shows how harness mechanisms become both product UI and training infrastructure rather than remaining hidden implementation detail

### Cognition / Devin
- Focus: cloud-agent runtime substrate and organizational rollout
- Distinctive emphasis: microVM isolation, hypervisor snapshotting across async gaps, warm-pool orchestration, permission inheritance, audit trails, engineering-process redesign, macOS/Xcode execution, stacked PR support, devbox-environment partnerships, and explicit orchestration/execution-plane separation through Devin Outposts workers
- Main contribution: grounds cloud agents in concrete runtime and governance requirements rather than treating them as just remote CLI wrappers; the latest Namespace documentation turns that into a documented architecture where Devin Cloud handles planning/inference while fresh per

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
- [[../sources/openai-chatgpt-voice-desktop-app-x-2026-07-23.md]]
- [[../sources/apple-speechanalyzer-x-2026-07-28.md]]
- [[../sources/figma-figma-mcp-server-slides-figjam-make-x-2026-06-16.md]]
- [[../sources/emilkowalski-ski

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

### Eval and Review Reliability

Source: `wiki/maps/eval-review-reliability.md`

# Eval and Review Reliability

## Purpose
Collect the KB's evaluation and review ideas into one map focused on practical reliability: how to know whether an agent-produced artifact is good enough, and how to keep review load from becoming the bottleneck.

## Core thesis
Agent output quality improves when evaluation is treated as a separate harness layer, not as an informal final glance by the same agent that produced the work.

## Reliability layers

### 1. Deterministic checks first
Use cheap checks before semantic review:
- lint and typecheck
- tests and smoke tests
- formatting and structural checks
- repository-specific machine-checkable invariants

Related concepts: [[../concepts/machine-checkable-invariants.md]], [[../concepts/feedback-controls.md]].

### 2. Task-fit review
Check whether the work actually satisfies the request:
- requirements coverage
- edge cases
- backward compatibility
- user-facing behavior
- maintainability

Related maps: [[coding-agent-review-rubric.md]], [[agent-deployment-gates-and-operational-risk.md]].

### 3. Independent evaluator loop
Separate generation from judgment when quality is fuzzy or high-stakes:
- subagent review
- adversarial review
- blocking review gates
- human escalation for ambiguous or high-blast-radius changes

Related concepts: [[../concepts/generator-evaluator-loop.md]], [[../concepts/self-evaluation-bias.md]], [[../concept

## 次に考えるとよさそうな問い

- このテーマは、どの現場課題を減らすための考え方か？
- 人間が見るべき判断軸と、エージェントに任せられる作業はどう分かれるか？
- 導入するときに失敗しやすい雑な抽象化は何か？
- 既存の開発・レビュー・ナレッジ運用にどう接続できるか？
