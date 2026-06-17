<!-- generated: 2026-06-18T03:00:16.683211+09:00 -->
<!-- primary_topic: wiki/maps/okf-adoption-for-knowledge-base-llm.md -->
# OKF Adoption for knowledge-base-llm

- Date: 2026-06-18
- Primary topic: `wiki/maps/okf-adoption-for-knowledge-base-llm.md`
- Purpose: KB由来の材料を、人間がHTMLで読んで理解しやすい読み物にする

## 今日のランダムテーマ

OKF Adoption for knowledge-base-llm を入口に、関連するKBノートをつないで実務上の論点を整理する。

## 主要ソース抜粋

### OKF Adoption for knowledge-base-llm

---
type: Map
title: OKF adoption for knowledge-base-llm
description: Decision memo on whether this KB should adopt Open Knowledge Format v0.1 conventions.
tags: [okf, compiled-wiki, knowledge-base, interoperability]
timestamp: 2026-06-17T11:30:00Z
---

# OKF Adoption for knowledge-base-llm

## Verdict
Adopt OKF v0.1 conventions incrementally, not as a repo-wide conversion yet.

This KB already follows the important OKF shape: Markdown files, directories as navigation, source/concept/map separation, and cross-links. The gap is mostly metadata: most wiki files do not carry OKF frontmatter, and existing frontmatter lacks the required `type` field.

## Primary Sources Checked
- [[../sources/google-cloud-open-knowledge-format.md]]
- [[../sources/classmethod-open-knowledge-format-okf-v01-guide.md]]
- GoogleCloudPlatform/knowledge-catalog `okf/SPEC.md`

## What OKF Adds
- A minimal interoperability contract: non-reserved Markdown concept files have YAML frontmatter with non-empty `type`.
- Optional but useful fields: `title`, `description`, `resource`, `tags`, `timestamp`.
- Reserved `index.md` and `log.md` semantics for progressive disclosure and change history.
- Normal Markdown links as untyped graph edges.

## Fit With This KB
Strong fit:
- The KB is already a compiled Markdown wiki, not a database-first RAG store.
- Agents already start from `wiki/INDEX.md`, `wiki/navigation/`, maps, concepts, and source notes.
- OKF would make the current structure easier to validate, visualize, export, and consume from other agents.

Weak fit / caution:
- OKF v0.1 is intentionally minimal and does not solve provenance, confidence, permissions, freshness, or evidence-quality semantics.
- The official visualizer is early; a practitioner test found a mismatch where the spec recommends bundle-absolute links but the visualizer skipped `/`-prefixed links.
- Adding frontmatter everywhere creates maintenance cost unless automated and linted.

## Current Compliance Snapshot
Measured against `wiki/` on 2026-06-17:
- Markdown files: 572
- Non-reserved concept documents: 571
- Files with YAML frontmatter: 85
- Files with required `type`: 0
- Missing frontmatter: 486

So the KB is architecturally OKF-like but not OKF-conformant.

## Recommended Adoption Path
1. Define a local type vocabulary before mass edits:
   - `Source`
   - `Concept`
   - `Map`
   - `Navigation`
   - `Glossary`
   - `Open Questions`
   - `Index`
2. Pilot on new and touched notes only.
3. Add a lightweight conformance checker for `wiki/`.
4. Convert existing notes by category in small batches after the checker i

## 関連ノートからの補助材料

### Open Knowledge Format

Source: `wiki/concepts/open-knowledge-format.md`

---
aliases:
  - OKF
  - Open Knowledge Format
---

# Open Knowledge Format

## Definition
Open Knowledge Format (OKF) is a proposed open specification for packaging knowledge as Markdown files with YAML frontmatter, filesystem paths, and Markdown links so humans, agents, catalogs, and visualizers can exchange LLM-wiki style context without a vendor-specific service or SDK.

## Why It Matters
OKF makes the compiled-wiki pattern portable. Instead of each team building a bespoke agent knowledge repo, a minimal common bundle format can let one system produce knowledge and another system consume, inspect, index, visualize, or reason over it.

## Related Concepts
- [[compiled-wiki.md]]
- [[agent-knowledge-loop.md]]
- [[context-file-system.md]]
- [[context-graph.md]]
- [[company-brain.md]]
- [[navigable-agent-skills.md]]
- [[evidence-quality.md]]
- [[loop-engineering.md]]
- [[knowledge-base-linting.md]]

## Supporting Sources
- [[../sources/google-cloud-open-knowledge-format.md]]
- [[../sources/classmethod-open-knowledge-format-okf-v01-guide.md]]
- [[../sources/karpathy-personal-llm-kb.md]]
- [[../sources/nori-handa-karpathy-llm-wiki-zenn.md]]
- [[../sources/googlecloudjp-agent-skills-repository.md]]

## Design Notes
- OKF treats file paths as concept identity and Markdown links as the relationship layer.
- The v0.1 proposal is deliberately minimal: the article says `type` is the req

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

### Google Cloud - Introducing the Open Knowledge Format

Source: `wiki/sources/google-cloud-open-knowledge-format.md`

# Google Cloud - Introducing the Open Knowledge Format

## Source metadata
- Raw path: raw/articles/google-cloud-open-knowledge-format-blog-2026-06-12.md
- Original URL: https://cloud.google.com/blog/products/data-analytics/how-the-open-knowledge-format-can-improve-data-sharing/?hl=en
- Published: 2026-06-12
- Authors: Sam McVeety; Amir Hormati
- Publisher: Google Cloud Blog
- Type: vendor primary source / open specification announcement
- Evidence strength: high for Google Cloud's OKF design intent and shipped reference artifacts; early for ecosystem adoption

## Summary
Google Cloud introduces Open Knowledge Format (OKF) v0.1, an open specification for packaging LLM-wiki style knowledge as portable Markdown files with YAML frontmatter and normal Markdown links. The article argues that agentic systems are bottlenecked by fragmented organizational context and that the missing layer is not another knowledge service, but a simple interoperable format that producers and consumers can share.

## Key claims
- Agent usefulness is often limited by missing relevant context rather than model capability alone.
- Organizational context is fragmented across catalogs, wikis, drives, code comments, notebooks, and individual expertise.
- OKF formalizes the emerging LLM-wiki pattern into a vendor-neutral, agent- and human-friendly bundle format.
- The core bundle is "just" Markdown files, a fi

## 次に考えるとよさそうな問い

- このテーマは、どの現場課題を減らすための考え方か？
- 人間が見るべき判断軸と、エージェントに任せられる作業はどう分かれるか？
- 導入するときに失敗しやすい雑な抽象化は何か？
- 既存の開発・レビュー・ナレッジ運用にどう接続できるか？
