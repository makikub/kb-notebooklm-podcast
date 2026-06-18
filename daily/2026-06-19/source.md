<!-- generated: 2026-06-19T03:00:14.043314+09:00 -->
<!-- primary_topic: wiki/maps/context-graph-and-company-brain.md -->
# Context Graph and Company Brain

- Date: 2026-06-19
- Primary topic: `wiki/maps/context-graph-and-company-brain.md`
- Purpose: KB由来の材料を、人間がHTMLで読んで理解しやすい読み物にする

## 今日のランダムテーマ

Context Graph and Company Brain を入口に、関連するKBノートをつないで実務上の論点を整理する。

## 主要ソース抜粋

### Context Graph and Company Brain

# Context Graph and Company Brain

## Purpose
This map connects the emerging vocabulary around company-scale agent memory: compiled wiki, context graph, Company Brain, and context farming.

## Core Pattern
1. Raw organizational signals enter the system: docs, chat, logs, emails, tickets, meetings, and decisions.
2. A context layer extracts entities, relationships, rules, provenance, and validity windows.
3. Agents query the layer before acting, ideally receiving only context that is relevant, permitted, and still valid.
4. Humans maintain the layer through review, invalidation, conflict resolution, and context farming.
5. Dreaming-style background review can propose memory cleanup and cross-session pattern promotion, but should preserve provenance and review boundaries.

In an agent-first company, this context layer also becomes an operating surface: named agents read and update role docs, taskboards, status files, decision records, handoffs, and feedback-strength notes so the organization can be queried through artifacts rather than through human status routing.

Japanese adoption framing increasingly explains this as agents "gaining experience": memory stores the experience, and Dreaming consolidates repeated patterns across multiple agents. The metaphor is useful, but the implementation still needs permission scopes, concurrency handling, version history, and evidence quality.

## Concept Relationships
- [[../concepts/compiled-wiki.md]] is the inspectable Markdown version of compiled knowledge.
- [[../concepts/agent-knowledge-loop.md]] is the recurring ingest / compile / query / promote loop that turns the substrate into a compounding system.
- [[../concepts/open-knowledge-format.md]] is an attempt to standardize that Markdown knowledge layer so producers and consumers can exchange bundles.
- [[../concepts/context-graph.md]] adds explicit relationships, temporal validity, permissions, and decision traces.
- [[../concepts/company-brain.md]] is the organization-level product / operating model built on a shared context layer.
- [[../concepts/context-farming.md]] is the human maintenance practice that keeps the context layer useful.
- [[../concepts/loop-engineering.md]] describes how recurring maintenance, review, and wakeup loops can be designed around that substrate.
- [[../concepts/memory-skill-harness.md]] treats reusable procedures as part of the same context substrate rather than a separate prompt library.
- [[../concepts/compiled-wiki.md]] needs explicit lint and provenance controls because compiled errors can become durable organizational context.

## 関連ノートからの補助材料

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

### Research OS Query Paths

Source: `wiki/maps/research-os-query-paths.md`

# Research OS Query Paths

## Purpose
Define question-shaped entrypoints so the KB can be used as a research OS, not only as a list of source summaries.

## Core thesis
A useful compiled wiki should route recurring user questions through stable paths: start with a map, traverse concepts, inspect strongest evidence, then return a grounded answer or create a missing note.

## Query path template
For each recurring question:
1. Start map: the first synthesis note to open.
2. Concepts to inspect: reusable vocabulary needed for the answer.
3. Strongest sources: primary or high-confidence support.
4. Weak signals: X threads, practitioner anecdotes, or speculative leads.
5. Output shape: answer, comparison, checklist, roadmap, or follow-up research queue.
6. Repo writeback: where durable answers should be saved.

## Current query paths

### 1. "I want to introduce agents into a development workflow"
- Start map: [[agent-harness-landscape.md]]
- Concepts: [[../concepts/harness-engineering.md]], [[../concepts/agent-recognizable-repository.md]], [[../concepts/coding-agents.md]], [[../concepts/approval-policy.md]]
- Strongest sources: [[../sources/openai-harness-engineering.md]], [[../sources/martin-fowler-harness-engineering.md]], [[../sources/anthropic-effective-harnesses-long-running-agents.md]]
- Output shape: adoption roadmap + minimum viable harness checklist
- Writeback: `outputs/r

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
