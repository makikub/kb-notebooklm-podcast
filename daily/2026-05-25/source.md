<!-- generated: 2026-05-25T03:00:32.862653+09:00 -->
<!-- primary_topic: wiki/maps/eval-review-reliability.md -->
# Eval and Review Reliability

- Date: 2026-05-25
- Primary topic: `wiki/maps/eval-review-reliability.md`
- Purpose: KB由来の材料を、人間がHTMLで読んで理解しやすい読み物にする

## 今日のランダムテーマ

Eval and Review Reliability を入口に、関連するKBノートをつないで実務上の論点を整理する。

## 主要ソース抜粋

### Eval and Review Reliability

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

Related concepts: [[../concepts/generator-evaluator-loop.md]], [[../concepts/self-evaluation-bias.md]], [[../concepts/human-in-the-loop.md]].

### 4. Trace-driven improvement
Convert repeated review failures into stronger harness rules:
- new tests
- clearer instructions
- new repo rules
- updated rubrics
- new lint checks

Related concepts: [[../concepts/trace-driven-improvement.md]], [[../concepts/knowledge-base-linting.md]].

## Source synthesis

### OpenAI
Supports the repo-structure and machine-checkable-invariant side: make the desired work shape legible and enforceable before human review.

### Martin Fowler
Provides vocabulary for guide/sensor design and the distinction between feedforward and feedback controls.

### Anthropic long-running harnesses
Supports bounded increments, environment verification, handoff artifacts, and evaluator separation for longer work. The `cwc-long-running-agents` companion repo makes this concrete with a default-FAIL results file, evidence-read tracking, a write gate over `test-results.json`, and a fresh-context evaluator subagent.

### OpenAI Codex plugin for Claude Code
Shows independent model review as a callable tool inside another coding-agent harness.

### Spillwave and Boris Tane
Warn that faster code generation can overwhelm review and produce system

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

### Agent Deployment Gates and Operational Risk

Source: `wiki/maps/agent-deployment-gates-and-operational-risk.md`

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
Frames the main operational danger as review discipline collapsing under h

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
