<!-- generated: 2026-06-07T03:00:10.776569+09:00 -->
<!-- primary_topic: wiki/maps/orchestration-patterns-faq.md -->
# Orchestration Patterns FAQ

- Date: 2026-06-07
- Primary topic: `wiki/maps/orchestration-patterns-faq.md`
- Purpose: KB由来の材料を、人間がHTMLで読んで理解しやすい読み物にする

## 今日のランダムテーマ

Orchestration Patterns FAQ を入口に、関連するKBノートをつないで実務上の論点を整理する。

## 主要ソース抜粋

### Orchestration Patterns FAQ

# Orchestration Patterns FAQ

## Purpose
Capture recurring practical questions that come up when explaining multi-agent coordination patterns, especially where abstract taxonomy breaks down in real usage.

## What is an orchestrator pattern in plain terms?
An orchestrator pattern uses a parent agent or workflow engine to break work into parts, assign bounded subtasks, gather results, and decide what happens next.

This is usually the most intuitive pattern for product work because it mirrors project management: one owner decomposes, delegates, checks, and integrates.

## Is it necessary to split every role into separate agents?
No. A narrower split is often enough.

A common practical pattern is to separate only verification:
- main agent plans and implements
- verifier agent reviews against explicit criteria
- parent or main worker decides whether to accept, revise, or retry

This is closer to a generator-verifier loop than a full multi-role team.

## What makes message bus different from orchestration?
Message bus is event-driven rather than parent-directed.

Instead of a parent saying:
- reviewer, inspect this PR
- security agent, check this change

an event is published, for example:
- `pr_opened`
- `ci_failed`
- `security_alert`

Agents subscribe to the events they care about and react when those events appear.

## Why is message bus hard to understand at first?
Because people often imagine the same system with more agents and assume that is enough.

The actual distinction is not the number of agents. It is the control flow:
- orchestrator = direct instruction flow
- message bus = published event flow

A simple mental model:
- orchestrator = manager assigning tasks
- message bus = shared incident board where specialists pick up relevant events

## Does message bus require continuous monitoring?
Yes, in the sense that some event-consumption layer must be active.

But that does not necessarily mean one agent sitting in a `while true` loop. In practice this is often implemented with:
- hooks
- webhooks
- queue consumers
- pub/sub subscribers
- cron-based pollers
- lightweight always-on workers

So the system needs active listeners, but the mechanism is usually infrastructure, not one constantly thinking agent.

## Is message bus useful for product development?
Yes, but usually as a supporting layer rather than the main implementation structure.

A practical split is:
- main product work = orchestrator-subagent or agent-team flow
- supporting automation = message bus reactions around CI, PRs, incidents, release events, docs updates, and alerts

## Where

## 関連ノートからの補助材料

### Multi-Agent Orchestration

Source: `wiki/concepts/multi-agent-orchestration.md`

---
aliases:
  - Multi-Agent Orchestration
---

# Multi-Agent Orchestration

## Definition
The deliberate assignment of different roles or subtasks to multiple cooperating agents within a larger workflow.

## Why It Matters
Some tasks benefit from separating planning, generation, evaluation, and execution rather than asking one agent to do everything.

## Related Concepts
- [[generator-evaluator-loop]]
- [[context-resets]]
- [[long-running-agents]]
- [[intelligent-delegation.md]]
- [[heavy-thinking.md]]
- [[managed-agents.md]]

## Supporting Sources
- [[../sources/anthropic-harness-design-long-running-apps.md]]
- [[../sources/claude-new-in-managed-agents-dreaming-outcomes-orchestration.md]]
- [[../sources/kevin-gu-autoagent-x-thread.md]]
- [[../sources/openai-codex-plugin-cc-github.md]]
- [[../sources/anthropic-claude-code-skills-docs.md]]
- [[../sources/cursor-3-x.md]]
- [[../sources/openai-gpt-5-4-mini-nano-blog.md]]
- [[../sources/codex-subagents-docs.md]]
- [[../sources/blader-adversarial-subagent-review-gate-goal-x-2026-05-23.md]]
- [[../sources/bcherny-auto-mode-multi-clauding-x-2026-05-24.md]]
- [[../sources/xjuntaro-planning-subagent-review-codex-x-2026-05-16.md]]
- [[../sources/anthropic-multi-agent-coordination-patterns.md]]
- [[../sources/arxiv-autogenesis-self-evolving-agent-protocol.md]]
- [[../sources/nyk-builderz-4-agent-hermes-operator-layer-x.md]]
- [[../source

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

### Agent Harness Landscape

Source: `wiki/maps/agent-harness-landscape.md`

# Agent Harness Landscape

## Purpose
This map connects the emerging idea of harness engineering across several sources and shows how it fits into the broader LLM agents knowledge base.

## Core thesis
Agent performance is not just a function of the model. It depends heavily on the harness: the repository structure, controls, artifacts, tests, review loops, and orchestration patterns around the model.

## Main dimensions

### 1. Guidance before action
- feedforward controls
- short map-like instructions
- architecture docs
- explicit plans
- feature lists
- templates and skills

### 2. Correction after action
- tests
- linters
- structural checks
- browser-based verification
- AI review / evaluator agents
- recurring cleanup tasks

### 3. Continuity across sessions
- progress logs
- commit history
- feature list artifacts
- initializer agent outputs
- context resets

### 4. Control of autonomy
- approval policy
- human-in-the-loop checkpoints
- classifier-mediated approvals
- machine-checkable invariants

### 5. Role separation
- planner
- generator
- evaluator
- maintenance / cleanup agents

## Source contributions

### Karpathy
Provides the raw → compiled wiki loop and the idea that LLM-maintained Markdown systems can become a working knowledge substrate.

### OpenAI
Shows harness engineering in a production-like coding environment, emphasizing repo structure, machine-enforce

### Harness Engineering Vendor / Practitioner Comparison

Source: `wiki/maps/harness-engineering-vendor-comparison.md`

# Harness Engineering Vendor / Practitioner Comparison

## Purpose
Compare how different sources frame harness engineering, what they optimize for, and what distinctive mechanisms they emphasize.

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
- Distinctive emphasis: microVM isolation, hypervisor snapshotting across async gaps, warm-pool orchestration, p

## 次に考えるとよさそうな問い

- このテーマは、どの現場課題を減らすための考え方か？
- 人間が見るべき判断軸と、エージェントに任せられる作業はどう分かれるか？
- 導入するときに失敗しやすい雑な抽象化は何か？
- 既存の開発・レビュー・ナレッジ運用にどう接続できるか？
