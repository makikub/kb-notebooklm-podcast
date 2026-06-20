<!-- generated: 2026-06-21T03:00:12.600155+09:00 -->
<!-- primary_topic: wiki/maps/evidence-quality-and-source-trust.md -->
# Evidence Quality and Source Trust

- Date: 2026-06-21
- Primary topic: `wiki/maps/evidence-quality-and-source-trust.md`
- Purpose: KB由来の材料を、人間がHTMLで読んで理解しやすい読み物にする

## 今日のランダムテーマ

Evidence Quality and Source Trust を入口に、関連するKBノートをつないで実務上の論点を整理する。

## 主要ソース抜粋

### Evidence Quality and Source Trust

# Evidence Quality and Source Trust

## Purpose
Turn the KB from a flat summary collection into a research OS that can reason about claim strength, provenance, and safe reuse.

## Core thesis
The wiki should not only answer "what does this source say?" It should answer "how much should we trust this source for this specific claim, and what can it safely support?"

## Evidence tiers

### Tier 1: Direct primary evidence
Use for definitions, product behavior, and hard constraints.
- official docs
- source repositories
- papers with clear methods
- reproducible examples or code

Typical confidence: high, unless the capture is partial or outdated.

### Tier 2: Practitioner operational evidence
Use for workflow patterns, heuristics, and lived failure modes.
- first-person engineering reports
- postmortems
- detailed implementation notes
- Masaki operation notes

Typical confidence: medium to high for "this pattern worked in this setting," lower for broad generalization.

### Tier 3: Public synthesis and commentary
Use as weak signals, vocabulary, or leads for deeper research.
- X threads
- podcast summaries
- product announcements
- second-order summaries

Typical confidence: low to medium. These should not anchor core claims without stronger support.

### Tier 4: KB synthesis
Use for repo-local interpretation, roadmaps, and hypothesis formation.
- map notes
- comparison notes
- durable answers
- lint reports

Typical confidence depends on cited support. Synthesis should expose which sources it depends on.

## Source note convention
Important source notes should include:
- `Source type:` what kind of evidence this is
- `Confidence:` high / medium / low
- `Supports:` directly supported concepts or map claims
- `Main limitations:` why not to overuse it
- `Best use:` definition / implementation pattern / warning / weak signal / comparison input

## Claim support relationship
Use lightweight relationship language in map notes:
- `supports` — source directly backs the claim
- `illustrates` — source gives an example but not a general proof
- `contradicts` — source pushes against another claim
- `extends` — source adds a new dimension to an existing concept
- `depends_on` — a synthesis claim relies on a concept or prior map

## Initial backfill priorities
1. Core harness sources: OpenAI, Fowler, Anthropic long-running harnesses.
2. Deployment and review-risk sources: Spillwave, Boris Tane, Anthropic quality postmortem, Codex plugin.
3. Memory/context sources: Karpathy, context graph, Company Brain, Obsidian / Field Theory notes.
4. Product surfaces that expose proven

## 関連ノートからの補助材料

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

### Evidence Quality

Source: `wiki/concepts/evidence-quality.md`

---
aliases:
  - Evidence Quality
  - Source Trust
---

# Evidence Quality

## Definition
Evidence quality is the explicit confidence layer attached to a source note or synthesis claim: what kind of source it is, how directly it supports a claim, what limitations apply, and which concepts it can safely support.

## Why It Matters
A compiled wiki becomes dangerous when all notes look equally authoritative. Evidence quality lets the KB distinguish primary docs, research papers, implementation repos, practitioner reports, product announcements, social threads, and speculative synthesis before those notes are reused in maps or answers.

## Operational Fields
Use these fields when a source anchors an important concept or map:
- Source type: primary docs, official blog, paper, repository, practitioner report, X thread, second-order summary, internal operation note, speculative synthesis.
- Confidence: high / medium / low.
- Supports: concepts or map claims the source can directly support.
- Limitations: missing context, second-order interpretation, product-marketing bias, anecdotal scope, truncated capture, no reproducible artifacts.
- Best use: definition, example, implementation pattern, warning, comparison input, weak signal, follow-up lead.

## Related Concepts
- [[compiled-wiki.md]]
- [[knowledge-base-linting.md]]
- [[context-graph.md]]
- [[real-world-evaluation.md]]

## Support

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
