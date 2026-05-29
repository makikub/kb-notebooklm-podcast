<!-- generated: 2026-05-30T03:00:09.796709+09:00 -->
<!-- primary_topic: wiki/maps/approval-policy-patterns-and-escalation.md -->
# Approval Policy Patterns and Escalation

- Date: 2026-05-30
- Primary topic: `wiki/maps/approval-policy-patterns-and-escalation.md`
- Purpose: KB由来の材料を、人間がHTMLで読んで理解しやすい読み物にする

## 今日のランダムテーマ

Approval Policy Patterns and Escalation を入口に、関連するKBノートをつないで実務上の論点を整理する。

## 主要ソース抜粋

### Approval Policy Patterns and Escalation

# Approval Policy Patterns and Escalation

## Purpose
Connect approval policy from a vague safety setting into a concrete design space: what gets auto-approved, what gets reviewed, what gets blocked, and how escalation changes throughput.

## Core idea
Approval policy is not one binary switch between autonomy and safety. In practice it is a stack of gates across action type, environment, review path, and failure handling.

## Common escalation ladder

### 1. Auto-allowed actions
- low-risk reads
- bounded searches
- local analysis that does not mutate durable state

### 2. Advisory review
- agent proceeds, but another agent or tool reviews before completion
- useful when the main risk is missed issues rather than immediate damage
- example pattern: optional review commands such as Codex review inside Claude Code

### 3. Blocking review
- work cannot complete or merge until a reviewer or gate approves it
- useful when risk is concentrated near handoff, deploy, or publish boundaries
- example pattern: stop-hook review gates or required PR checks

### 4. Human-only execution
- irreversible, externally visible, or high-blast-radius actions remain human-triggered
- examples: production deploys, destructive writes, outbound messaging, broad connector scope changes
- delegation of delegation itself, when the downstream agent would gain authority to assign tasks or permissions to others

## Design dimensions

### Action risk
- read vs write
- local vs external
- reversible vs irreversible
- narrow scope vs broad blast radius

### Review timing
- pre-action approval
- post-action advisory review
- stop-path blocking review
- periodic audit after scheduled or background execution

### Policy mechanism
- static allow/deny rules
- classifier-mediated auto approval
- branch and environment restrictions
- concurrency, nesting, or runtime limits on delegated workers

## Source contributions

### Anthropic auto mode
Frames approval friction as a product and safety problem, and introduces classifier-mediated auto approval as a middle ground between constant prompts and full bypass.

### Codex subagents docs
Shows that approval policy extends into delegation itself through inherited sandboxing, explicit concurrency limits, and maximum nesting depth.

### OpenAI Codex plugin for Claude Code
Adds the distinction between advisory review and blocking review. The same cross-agent reviewer can either suggest fixes or block completion depending on where it sits in the path.

### Anthropic scheduled tasks docs
Shows that recurring autonomous work needs environment, connector, and

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

## 次に考えるとよさそうな問い

- このテーマは、どの現場課題を減らすための考え方か？
- 人間が見るべき判断軸と、エージェントに任せられる作業はどう分かれるか？
- 導入するときに失敗しやすい雑な抽象化は何か？
- 既存の開発・レビュー・ナレッジ運用にどう接続できるか？
