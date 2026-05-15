<!-- generated: 2026-05-16T03:00:21.139570+09:00 -->
<!-- primary_topic: wiki/maps/agent-onboarding-kb-codebase.md -->
# NotebookLM Podcast Source: Agent Onboarding with Domain KB + Codebase

- Date: 2026-05-16
- Primary topic: `wiki/maps/agent-onboarding-kb-codebase.md`
- Purpose: NotebookLM Audio Overviewに読ませるためのKB由来ソースページ

## 今日のランダムテーマ

Agent Onboarding with Domain KB + Codebase を入口に、関連するKBノートをつないで実務上の論点を整理する。

## 主要ソース抜粋

### Agent Onboarding with Domain KB + Codebase

# Agent Onboarding with Domain KB + Codebase

## Purpose
Capture the pattern where a maintained knowledge base becomes an onboarding, memory, and question-answering substrate for agents, especially when paired with direct codebase access.

## Thesis
An agent becomes materially more useful when it can read both:

1. **Domain KB** — product/domain concepts, decisions, terminology, user expectations, operating rules, known failure modes.
2. **Codebase** — actual implementation, tests, architecture, constraints, naming, runtime behavior.

The KB explains what the system is supposed to mean. The codebase shows what the system actually does. The agent's advantage comes from continuously comparing the two and writing useful deltas back.

## Onboarding Shape

### Always-read pack
Keep this small and stable:
- KB index / current focus
- glossary and core domain concepts
- architecture or system map
- coding conventions and safety boundaries
- latest open questions / active risks

### Just-in-time retrieval
Load deeper notes only when the task needs them:
- feature-specific domain notes
- previous PR or issue decisions
- failure modes and support incidents
- source notes with provenance
- relevant implementation maps

### Codebase grounding
For any non-trivial implementation task, agents should pair KB reading with code inspection:
- verify whether a KB claim is reflected in code
- identify drift between product/domain intent and implementation
- update the KB when implementation reality teaches something durable
- file open questions when the mismatch is unresolved

## Feedback Loop
1. Agent receives task.
2. Agent reads onboarding pack.
3. Agent queries KB for task-specific context.
4. Agent inspects codebase and tests.
5. Agent acts: plan, implement, review, or answer.
6. Agent writes back durable findings: decisions, mismatches, test insights, naming conventions, review heuristics, or TODOs.
7. Periodic lint checks stale notes, weak provenance, missing backlinks, and code/knowledge drift.

## Why It Could Outperform Human-Only Output
Humans often leave domain context scattered across memory, Slack/Discord, issues, PR comments, and implicit conventions. A maintained KB plus codebase loop gives agents a structured way to:
- preserve tacit decisions;
- reuse prior reasoning;
- discover implementation drift;
- synthesize cross-source patterns;
- onboard repeatedly without losing state;
- produce artifacts that become future training material for the next run.

The compounding effect is the key: each useful output should make the next agent run cheaper, better grou

## 関連ノートからの補助材料

### Masaki — Agent onboarding with domain KB plus codebase

Source: `wiki/sources/masaki-agent-onboarding-kb-codebase-idea.md`

# Masaki — Agent onboarding with domain KB plus codebase

## Source Metadata
- Origin: Discord thread `Clawdbotの可能性深掘り`
- Date captured: 2026-04-27
- Type: practitioner hypothesis / product idea
- Evidence strength: user hypothesis grounded in active KB and coding-agent workflow exploration

## Summary
Masaki proposed using a maintained knowledge-base repository as an agent education layer: agents can periodically read it as memory training, query it when uncertain, and combine it with the target codebase to understand both domain knowledge and implementation reality. The hypothesis is that this pairing can make agents onboard faster and eventually produce outputs that exceed what humans manually write, because they can continuously traverse, compare, and update the domain map plus implementation state.

## Core Idea
- A domain KB should not only answer ad hoc questions; it should serve as an onboarding curriculum for agents.
- The useful unit is **domain knowledge + codebase**, not either one alone.
- Periodic KB loading can provide baseline memory, while retrieval / Q&A can provide just-in-time detail.
- Agents should compare the KB's conceptual model against the codebase's actual implementation.
- Work products, PR judgments, gaps, and design decisions should be written back into the KB so onboarding improves over time.

## Why This Matters
This reframes a KB from a passive 

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

## Podcastで掘るとよい問い

- このテーマは、どの現場課題を減らすための考え方か？
- 人間が見るべき判断軸と、エージェントに任せられる作業はどう分かれるか？
- 導入するときに失敗しやすい雑な抽象化は何か？
- 既存の開発・レビュー・ナレッジ運用にどう接続できるか？

## NotebookLMに期待する話し方メモ

- 日本語の自然な技術雑談。硬い講義ではなく、実務で悩む2人の会話にする。
- 単なる要約ではなく、具体的な現場の使いどころ、危ない誤解、次の一手まで話す。
- 結論を急ぎすぎず、問いを立てながら深掘りする。
