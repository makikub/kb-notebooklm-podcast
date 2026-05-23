<!-- generated: 2026-05-24T03:00:32.264643+09:00 -->
<!-- primary_topic: wiki/maps/context-management-decisions.md -->
# Context Management Decision Map

- Date: 2026-05-24
- Primary topic: `wiki/maps/context-management-decisions.md`
- Purpose: KB由来の材料を、人間がHTMLで読んで理解しやすい読み物にする

## 今日のランダムテーマ

Context Management Decision Map を入口に、関連するKBノートをつないで実務上の論点を整理する。

## 主要ソース抜粋

### Context Management Decision Map

# Context Management Decision Map

## Purpose
Compare the main recovery and continuity moves available to long-running agent systems.

## Core moves

### Continue
- Keep the current session and context as-is.
- Best when the session is still coherent and the next task is closely related.

### Rewind
- Remove a failed branch and restart from the last good point.
- Best when the current line of reasoning is clearly wrong but the session still has useful surrounding state.

### Clear
- Explicitly wipe the session context and start over from artifacts.
- Best when the human wants tight control over what remains visible.

### Compact
- Condense the current session into a shorter summary.
- Best when the work is still relevant but the raw history is too large or noisy.

### Delegate
- Spawn a subagent or separate worker for a noisy or specialized subtask.
- Best when the subtask should not pollute the parent context.

### Reset
- Rebuild state from explicit handoff artifacts in a fresh session.
- Best when the current session has accumulated too much drift or hidden confusion.

### Loop / wake
- Use a scheduled loop or Monitor-style wakeup to revisit work over time.
- Best for recurring maintenance, long waits, or state-dependent follow-up.
- Heartbeat-style loops can be thread-local automations that monitor external surfaces, update artifacts, and adjust cadence until a condition is met.

## Source contributions

### Anthropic session management
Defines the continue / rewind / clear / compact / delegate decision surface directly and shows that context-window decisions are part of harness design.

### Anthropic long-running harnesses
Shows why explicit handoff artifacts and incremental progress make resets workable. The companion repo operationalizes this with `PROGRESS.md`, git commits, one-feature-per-session discipline, and a stop hook that commits tracked changes as a handoff backstop.

### Anthropic multi-agent harness design
Strengthens the case for separate evaluators and context resets when tasks become subjective or long-horizon.

### Anthropic dynamic /loop docs
Shows scheduled loops as an explicit harness primitive and points toward Monitor-based wakeups for recurring work.

### Jason Liu / Codex-maxxing
Shows heartbeat loops as a practical operator pattern: chief-of-staff inbox checks, feedback monitors that re-render artifacts, refund/customer-support polling, and vault updates that turn recurring work into explicit memory.

### Context-management practice notes
External workflow notes around Claude Code and context management show these moves tur

## 関連ノートからの補助材料

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

## 次に考えるとよさそうな問い

- このテーマは、どの現場課題を減らすための考え方か？
- 人間が見るべき判断軸と、エージェントに任せられる作業はどう分かれるか？
- 導入するときに失敗しやすい雑な抽象化は何か？
- 既存の開発・レビュー・ナレッジ運用にどう接続できるか？
