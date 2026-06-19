<!-- generated: 2026-06-20T03:00:13.801043+09:00 -->
<!-- primary_topic: wiki/maps/research-os-query-paths.md -->
# Research OS Query Paths

- Date: 2026-06-20
- Primary topic: `wiki/maps/research-os-query-paths.md`
- Purpose: KB由来の材料を、人間がHTMLで読んで理解しやすい読み物にする

## 今日のランダムテーマ

Research OS Query Paths を入口に、関連するKBノートをつないで実務上の論点を整理する。

## 主要ソース抜粋

### Research OS Query Paths

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
- Writeback: `outputs/reports/` or a new map if the answer generalizes

### 2. "I want long-running agents to stay stable"
- Start map: [[context-management-decisions.md]]
- Concepts: [[../concepts/long-running-agents.md]], [[../concepts/structured-handoff-artifacts.md]], [[../concepts/context-resets.md]], [[../concepts/incremental-progress.md]]
- Strongest sources: [[../sources/anthropic-effective-harnesses-long-running-agents.md]], [[../sources/anthropic-harness-design-long-running-apps.md]], [[../sources/anthropic-session-management-1m-context.md]]
- Output shape: continuation / reset / delegate decision tree
- Writeback: strengthen `context-management-decisions.md` when new cases appear

### 3. "I want to reduce review burden without losing safety"
- Start map: [[agent-deployment-gates-and-operational-risk.md]]
- Concepts: [[../concepts/machine-checkable-invariants.md]], [[../concepts/feedback-controls.md]], [[../concepts/self-verification.md]], [[../concepts/human-in-the-loop.md]]
- Strongest sources: [[../sources/openai-harness-engineering.md]], [[../sources/spillwave-ai-coding-hangover-harness-engineering.md]], [[../sources/openai-codex-plugin-cc-github.md]], [[../sources/anthropic-april-23-postmo

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

### Agent Harness Control Taxonomy

Source: `wiki/maps/agent-harness-control-taxonomy.md`

# Agent Harness Control Taxonomy

## Purpose
Normalize the control vocabulary used across the harness-engineering cluster so the KB can compare sources without collapsing distinct mechanisms into one vague idea of "guardrails."

## Core split
Harness controls fall along two practical axes:
1. **When they act** — before action, during action, or after action
2. **How they act** — deterministic/computational or semantic/inferential

This note treats those axes as complementary rather than mutually exclusive.

## Scope split: evaluation, runtime, context, safety
Use this split when a source says "harness" but means different machinery:
- **Evaluation harness**: infrastructure that scores models or task submissions, such as lm-evaluation-harness or SWE-bench-style graders.
- **Runtime harness**: the agent loop that alternates reasoning, tool use, observation, state, and retry behavior.
- **Context harness**: instructions, rule files, memory, retrieval, tools, hooks, skills, MCP servers, and other context surfaces exposed to the model.
- **Safety harness**: sandboxing, permission boundaries, approval flows, identity, audit logs, and other external risk controls.

These scopes cross-cut the timing/control axes below. For example, a hook can be an in-loop runtime control, a context-injection control, or a safety boundary depending on what it does.

The memory-skill harness framing sha

## 次に考えるとよさそうな問い

- このテーマは、どの現場課題を減らすための考え方か？
- 人間が見るべき判断軸と、エージェントに任せられる作業はどう分かれるか？
- 導入するときに失敗しやすい雑な抽象化は何か？
- 既存の開発・レビュー・ナレッジ運用にどう接続できるか？
