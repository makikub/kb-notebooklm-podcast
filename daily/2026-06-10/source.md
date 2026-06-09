<!-- generated: 2026-06-10T03:00:14.735669+09:00 -->
<!-- primary_topic: wiki/maps/harness-engineering-vendor-comparison.md -->
# Harness Engineering Vendor / Practitioner Comparison

- Date: 2026-06-10
- Primary topic: `wiki/maps/harness-engineering-vendor-comparison.md`
- Purpose: KB由来の材料を、人間がHTMLで読んで理解しやすい読み物にする

## 今日のランダムテーマ

Harness Engineering Vendor / Practitioner Comparison を入口に、関連するKBノートをつないで実務上の論点を整理する。

## 主要ソース抜粋

### Harness Engineering Vendor / Practitioner Comparison

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
- Distinctive emphasis: microVM isolation, hypervisor snapshotting across async gaps, warm-pool orchestration, permission inheritance, audit trails, and engineering-process redesign
- Main contribution: grounds cloud agents in concrete runtime and governance requirements rather than treating them as just remote CLI wrappers

### Anthropic
- Focus: long-running agents, structured handoffs, initializer agents, context resets, multi-agent evaluator patterns, cloud execution, scheduled tasks, reusable skills, MCP as the production integration layer, dedicated workspaces like Claude Design, managed-agent memory/dreaming/outcomes, and teams shipping at model-speed
- Distinctive emphasis: session-to-session continuity, feature lists, progress artifacts, planner/generator/evaluator split, progressive disclosure, model-managed orchestration, environment controls, careful tool boundaries, standardized auth, remote tool distribution, task-specific UI surfaces, rubric-driven outcomes, cross-session memory curation, and model-upgrade-driven harness cleanup
- Main contribution: strongest articulation of long-horizon harness design plus a clear argument that harness responsibilities should shift as model capabilities improve while productizing many of those mechanisms directly

### LangChain
- Focus: measu

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
