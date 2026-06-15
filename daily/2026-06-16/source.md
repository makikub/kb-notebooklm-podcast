<!-- generated: 2026-06-16T03:00:13.031346+09:00 -->
<!-- primary_topic: wiki/maps/agent-deployment-gates-and-operational-risk.md -->
# Agent Deployment Gates and Operational Risk

- Date: 2026-06-16
- Primary topic: `wiki/maps/agent-deployment-gates-and-operational-risk.md`
- Purpose: KB由来の材料を、人間がHTMLで読んで理解しやすい読み物にする

## 今日のランダムテーマ

Agent Deployment Gates and Operational Risk を入口に、関連するKBノートをつないで実務上の論点を整理する。

## 主要ソース抜粋

### Agent Deployment Gates and Operational Risk

# Agent Deployment Gates and Operational Risk

## Purpose
Connect harness engineering ideas to the specific problem of keeping agent-generated work from outrunning review, testing, and production safety.

## Core thesis
Once agents can generate code, configuration changes, or exploit findings faster than humans can inspect them, the harness needs explicit deployment gates. Otherwise the dominant failure shifts from isolated model mistakes to system-level review collapse.

## Main gate layers

### 1. Pre-merge structural gates
- machine-checkable invariants
- repo structure checks
- lint and test requirements
- architecture constraints that agents can read before editing

### 2. Pre-deploy verification gates
- end-to-end tests
- runtime smoke tests
- browser or environment verification
- explicit rollback readiness and observability checks

### 3. Human escalation gates
- approval policy for risky actions
- human-in-the-loop checkpoints for deploys, destructive actions, and ambiguous fixes
- adversarial or independent review when the agent is operating near the blast radius boundary

### 4. Post-deploy feedback gates
- production observability
- regression detection
- trace review for recurring failure modes
- recurring cleanup tasks when drift starts accumulating

## Cross-source synthesis

### Spillwave
Frames the main operational danger as review discipline collapsing under higher code volume. The strongest contribution is the argument that deployment safeguards must evolve with agent throughput, not after outages.

### OpenAI
Provides the repo-side view: map-like docs, custom linters, structured plans, and machine-checkable constraints that reduce what reaches later gates.

### Anthropic long-running harnesses
Adds environment verification, bounded increments, and explicit clean-state handoffs so that risky work is easier to inspect before shipping.

### OpenAI Codex plugin for Claude Code
Shows that independent review can itself become a callable gate rather than only a human habit.

### LangChain
Supports the idea that middleware hooks, verification prompts, and trace analysis can materially improve outcomes without changing the model.

### Boris Tane
Adds a concrete quality-drift failure mode: locally correct agent changes can still create system-wide decay if one-way-door architectural choices are not constrained and reviewed tightly.

### Lars Faye
Adds the comprehension-debt angle: deployment gates should not only catch defects, but also prevent generated throughput from exceeding the team’s ability to understand, review, and keep implementation

## 関連ノートからの補助材料

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

## 次に考えるとよさそうな問い

- このテーマは、どの現場課題を減らすための考え方か？
- 人間が見るべき判断軸と、エージェントに任せられる作業はどう分かれるか？
- 導入するときに失敗しやすい雑な抽象化は何か？
- 既存の開発・レビュー・ナレッジ運用にどう接続できるか？
