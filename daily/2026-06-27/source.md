<!-- generated: 2026-06-27T03:00:18.043554+09:00 -->
<!-- primary_topic: wiki/maps/coding-agent-review-rubric.md -->
# Coding-Agent Review Rubric

- Date: 2026-06-27
- Primary topic: `wiki/maps/coding-agent-review-rubric.md`
- Purpose: KB由来の材料を、人間がHTMLで読んで理解しやすい読み物にする

## 今日のランダムテーマ

Coding-Agent Review Rubric を入口に、関連するKBノートをつないで実務上の論点を整理する。

## 主要ソース抜粋

### Coding-Agent Review Rubric

# Coding-Agent Review Rubric

## Purpose
Provide a lightweight reusable review rubric for coding-agent workflows so reviewer agents, human reviewers, and automated review routines use the same judgment axes.

## Why this note exists
The current KB has strong vocabulary for harness controls, but it does not yet turn that vocabulary into a compact operational review standard. This note bridges that gap.

## Recommended core rubric
### 1. Correctness
- Does the change satisfy the intended requirement?
- Does it avoid regressions in existing behavior?
- Are edge cases or failure paths obviously mishandled?

### 2. Safety / Blast Radius
- Is the scope of change proportionate to the task?
- Could it create dangerous side effects, permission mistakes, data corruption, or risky automation behavior?
- Are rollback and containment concerns reasonable?

### 3. Maintainability / Simplicity
- Is the change understandable and locally coherent?
- Are responsibilities separated cleanly?
- Did the implementation avoid unnecessary complexity?

### 4. Test Adequacy
- Are tests proportional to the change?
- Do they cover more than only the happy path?
- Is the claimed behavior actually exercised by deterministic checks where possible?

### 5. Repo Fit / Harness Fit
- Does the change fit existing repository conventions, naming, structure, and architecture?
- Does it align with the intent recorded in plan or handoff artifacts?
- Does it respect the existing lint, hook, pre-commit, or review harness?

### 6. Comprehension / Reviewability
- Can a responsible reviewer explain the design and failure modes after reviewing the change?
- Is the diff small enough to inspect deeply, or should it be split?
- Did generated code outpace tests, documentation, or human mental-model maintenance?

## Suggested verdict format
- `PASS`
- `PASS WITH NITS`
- `NEEDS FIX`

## Suggested output structure
- Verdict
- Critical issues
- Nits
- Suggested fix
- Confidence

## Why this works as a harness component
- It gives verifier agents explicit grading criteria.
- It reduces drift across different review passes.
- It makes semantic review more comparable across humans and models.
- It complements deterministic checks instead of replacing them.

## Relationship to KB concepts
- It operationalizes [[../concepts/guides-and-sensors.md]] into a concrete review tool.
- It complements [[../concepts/machine-checkable-invariants.md]] by covering what linters and tests cannot fully judge.
- It fits Fowler's split between computational and inferential controls.

## Tradeoffs / Tensions
- A short rubric is easy 

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

### Harness Engineering Vendor / Practitioner Comparison

Source: `wiki/maps/harness-engineering-vendor-comparison.md`

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
- Main contribution: shows harness engineering as both a production engineering discipline and a composable ecosystem where one agent can check or extend a

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
- [[../sources/figma-figma-mcp-server-slides-figjam-make-x-2026-06-16.md]]

## Main dimensions

### 1. Guidance before action
- feedforward controls
- short map-like instructions
- architecture docs
- explicit plans
- feature 

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
