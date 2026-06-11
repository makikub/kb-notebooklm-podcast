<!-- generated: 2026-06-12T03:00:10.186139+09:00 -->
<!-- primary_topic: wiki/maps/coding-agent-cognitive-debt-and-review-capacity.md -->
# Coding-Agent Cognitive Debt and Review Capacity

- Date: 2026-06-12
- Primary topic: `wiki/maps/coding-agent-cognitive-debt-and-review-capacity.md`
- Purpose: KB由来の材料を、人間がHTMLで読んで理解しやすい読み物にする

## 今日のランダムテーマ

Coding-Agent Cognitive Debt and Review Capacity を入口に、関連するKBノートをつないで実務上の論点を整理する。

## 主要ソース抜粋

### Coding-Agent Cognitive Debt and Review Capacity

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

### 4. Vendor and cost dependency
If teams depend on provider-specific agents as their default coding capability, outages, model behavior changes, and token-cost shifts become operational risks.

### 5. Human energy budget
AI-assisted work may reduce typing while increasing the density of supervision, decision-making, and verification. If teams ignore recovery and attention limits, review capacity can fail even when the generated code is technically fast.

### 6. Verification tax as financial drag
DORA's ROI framing treats expanded review, testing, and instability as measurable adoption costs. This turns review capacity from a local engineering concern into a financial variable that can erase projected AI returns.

### 7. Intention debt vs comprehension debt
Kawasima's Scrapbox note separates “the code is not understood” from “the code is understood but the reason for the rule is gone.” The first is comprehension/cognitive debt; the second is [[../concepts/intention-debt.md]]. Agents make this distinction sharper because they can only use externalized specs, ADRs, tests, constraints, and docs, not the team's tacit memory.

### 8. Offloading vs surrender
Osmani's cognitive-surrender framing distinguishes usef

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

### AI Adoption ROI and Capability Investment

Source: `wiki/maps/ai-adoption-roi-and-capability-investment.md`

# AI Adoption ROI and Capability Investment

## Purpose
Map how AI-assisted software development becomes financial value only when capability investments let the organization absorb faster generation safely.

## Core thesis
AI ROI is not a direct function of model quality or code volume. It is a system outcome: AI adoption must be mediated by internal platforms, context/data quality, trust, user focus, verification guardrails, and delivery metrics before it can become durable business value. The strongest upside case is not only cheaper execution of existing backlog, but Jevons-style expansion in software demand when new tools, experiments, and automations become economical.

## Path from AI adoption to ROI

### 1. Capability investment first
The first question is not “which tool?” but “can the system absorb the tool?” DORA's report emphasizes quality internal developer platforms, AI-accessible internal data, clear AI stance/trust, context engineering, user-centric focus, and automated guardrails.

### 1a. Adoption phase before transformation
Shin Suga's AI-Ops roadmap adds a rollout operator's lens: the right move changes with actual AI usage rate. At low usage, measure and activate early adopters; at medium usage, build literacy and strong department-specific use cases; once usage is broad enough, context/data loops and workflow transformation become more credible. This preve

### Lars Faye — Agentic Coding is a Trap

Source: `wiki/sources/lars-faye-agentic-coding-is-a-trap.md`

# Lars Faye — Agentic Coding is a Trap

## Metadata
- Raw path: `raw/articles/lars-faye-agentic-coding-is-a-trap-2026.md`
- Original URL: https://larsfaye.com/articles/agentic-coding-is-a-trap
- Author: Lars Faye
- Published/fetched: fetched 2026-05-04
- Source type: practitioner essay / argument
- Evidence strength: medium for practitioner workflow critique; low-to-medium for cited empirical claims unless followed through to the referenced studies

## Summary
Faye argues that fully agentic coding workflows risk moving humans too far away from implementation. The article accepts coding agents as useful tools, but criticizes the “human as orchestrator, AI as coder” pattern because it can generate more code than reviewers can understand, erode the very skills needed to supervise agents, and create vendor/cost dependencies around what used to be an internal engineering capability.

## Key claims
- Agentic coding is not simply “moving up the stack”; increased ambiguity is not the same thing as a higher abstraction.
- The skilled-orchestrator role depends on architectural, coding, and debugging judgment, but heavy delegation can weaken those same abilities.
- LLMs often accelerate code volume and turnaround time rather than understanding, concision, or codebase fit.
- Coding is itself a planning medium for many developers; types, pseudo-code, function boundaries, and folder structur

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
