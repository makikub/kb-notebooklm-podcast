<!-- generated: 2026-05-17T13:01:13.902059+00:00 -->
<!-- kb_daily_digest_date: 2026-05-17 -->
# KB Daily Digest Source — 2026-05-17

このページは、knowledge-base-llm の日次更新を NotebookLM に読み込ませるための公開向けソースページです。
Discord通知よりも文脈を厚めに残し、Podcast化しやすいように、今日追加・更新されたソース、概念、地図を文章中心で整理します。

## 今日の全体像

<!-- public_page_url: https://makikub.github.io/kb-notebooklm-podcast/digest/2026-05-17/ -->
<!-- public_source_url: https://makikub.github.io/kb-notebooklm-podcast/digest/2026-05-17/source.md -->

# KB Daily Digest — 2026-05-17

2026-05-17 UTC の `knowledge-base-llm` では、新規 raw / wiki / sources の追加が実質的にありました。今日の更新はかなりまとまっていて、中心テーマは「ハーネスをコード生成の周辺技術ではなく、組織・知識・レビュー・安全性まで含む運用基盤として見る」ことです。昨日の ARIS で強まった「もっともらしいが根拠が薄い成功をどう疑うか」という流れが、今日は Claude Code の大規模コードベース運用、agent-first organization、ハーネス定義の整理、memory と skills の統合まで広がりました。

重要ソースの1本目は、Vasilije / @tricalt の X Article「Memory isn't a plugin. Skills aren't a plugin. They're the same harness.」です。直接本文の完全取得はできなかったため、X API metadata と xAI 抽出サマリを根拠にした中程度 confidence の source note ですが、KBへの寄与は大きいです。ここから新規概念 `memory-skill harness` が立ち、memory を単なる保存済み事実、skills を単なるプロンプト断片として分けるのではなく、環境を観察し、手順を選び、古くなった手順を修正し、次の実行で評価する同じループとして扱う見方が追加されました。

重要ソースの2本目は、aweb.ai の「How to set up an AI-native organization」と companion template repo です。これは、AI-native company を「社員がチャットボットを使う会社」ではなく、named agents が persistent context、taskboard、decision records、handoffs、status files を持ち、builder / reviewer split で作業する運用モデルとして説明しています。KBでは新規概念 `agent-first organization` を追加し、`company-brain`、`multi-agent-orchestration`、`structured-handoff-artifacts`、`agent-management` に接続しました。小規模企業の practitioner case study なので汎用ROIの証拠ではありませんが、「組織をqueryableにするためのartifact discipline」という観点ではかなり実用的です。

重要ソースの3本目は、NewsPicks Topic の「ハーネスエンジニアリングとは一体何なのか」です。このソースは、日本語圏で混ざりがちな「evaluation harness」と「agent harness」を分け、さらに agent harness を runtime / context / safety の層に分ける説明として取り込みました。KBの `agent-harness-control-taxonomy` では、before-action / in-loop / after-action controls と deterministic / inferential controls の整理に加えて、evaluation、runtime、context、safety という scope split が強化されました。これで「ハーネス」という語を使うときに、モデル評価の話なのか、エージェント実行系なのか、コンテキスト供給なのか、安全境界なのかを分けて読めるようになっています。

そのほか、Izanami の Claude Code 大規模コードベース記事は、Anthropic 公式ガイダンスを日本語の運用チェックリストに落としたものとして追加されました。薄い root CLAUDE.md、サブディレクトリ単位のルール、hooks による自己改善、古いルールの棚卸し、agent-manager / DRI の必要性が整理され、`agent-recognizable-repository`、`context-engineering`、`rule-update-loop`、`coding-agent-harness-patterns` が更新されています。これは今日の全体トレンドの中では、「ハーネスを足す」より先に、リポジトリとルールをエージェントが読める形に保つ話です。

X bookmarks 由来では、Peter Steinberger の Clawpatch automated code review、Claude Code champion kit、Hermes daily brief workflow も取り込まれました。Clawpatch は semantic work unit に分けて review / report / fix / revalidate するコードレビュー harness の具体例、champion kit は組織内の adoption surface、Hermes は daily brief を通じた chief-of-staff / background-agent 的な情報集約の例として扱っています。ここから `verification-tax`、`long-running-agents`、`background-agents`、`agent-captain`、`ai-adoption-j-curve` などの概念が補強されました。

全体トレンドとして、今日の KB は「ハーネス = モデルの外側にある便利な補助」から一段進んで、「ハーネス = 組織とエージェントが継続的に仕事をするための運用OS」に近づいています。コードレビューでは findings と revalidation、Claude Code 運用では repo-local context と hooks、agent-first organization では taskboard / decision / handoff、memory-skill harness では手順の自己更新、NewsPicks の taxonomy では runtime / context / safety の切り分けが出てきました。どれも、単発の生成結果ではなく、繰り返し作業をどう観察し、制御し、改善するかに寄っています。

NotebookLM Podcast で掘るなら、「memory と skills はなぜ同じ harness と言えるのか」から入ると面白そうです。次に、Claude Code の CLAUDE.md / hooks / skills / plugins / MCP の順序や、aweb.ai の named agents / shared artifacts とつなげると、個人の開発環境から小さな組織運用まで同じ設計原理で見えます。最後に NewsPicks の taxonomy を使って、これは context harness なのか、runtime harness なのか、safety harness なのかを整理すると、言葉だけが広がって実装判断が曖昧になるリスクを抑えられます。

公開HTML: https://makikub.github.io/kb-notebooklm-podcast/digest/2026-05-17/

NotebookLM用 source.md: https://makikub.github.io/kb-notebooklm-podcast/digest/2026-05-17/source.md


## 重要ソース

### Source Notes

Source note: `wiki/sources/README.md`

# Source Notes

Each note in this folder should summarize one source from `raw/`.

Recommended structure:
- source metadata
- short summary
- key claims
- evidence / examples
- evidence quality when the source is anecdotal, preview-only, benchmark-heavy, or captured from truncated material
- related concepts
- open questions
- backlinks to raw material
- [[simon-willison-gitlab-act-2.md]] — Simon Willison on GitLab's Act 2 announcement, organization flattening, smaller empowered R&D teams, and the agentic-era Jevons-style software demand thesis.
- [[google-research-nested-learning-continual-learning.md]] — Google Research on Nested Learning, continuum memory systems, and Hope as a model-internal continual-learning architecture.
- [[anthropic-claude-code-large-codebases.md]] — Anthropic on Claude Code at large-codebase scale: live-code navigation, harness extension points, layered context files, LSP/subagents, and org ownership.
- [[izanami-claude-code-large-codebase-best-practices.md]] — Japanese practitioner explainer on Claude Code large-codebase setup: live repo search, thin layered CLAUDE.md, subdirectory startup, hooks, stale-rule pruning, and adoption ownership.
- [[newspicks-harness-engineering-what-is-it.md]] — Japanese explainer separating evaluation harnesses from agent harnesses and decomposing agent harnesses into runtime, context, and safety layers.
- [[tricalt-memory-skills-same-harness-x.md]] — Vasilije / tricalt X Article framing memory and skills as one evolving harness/world-model loop.

### Vasilije / tricalt — Memory and skills as the same harness

Source note: `wiki/sources/tricalt-memory-skills-same-harness-x.md`

# Vasilije / tricalt — Memory and skills as the same harness

## Source Metadata
- Raw path: raw/articles/tricalt-memory-skills-same-harness-x-2026-05-17.md
- Original URL: https://x.com/tricalt/status/2055876832797581406
- Article URL: https://x.com/i/article/2053986800050524160
- Author: Vasilije / @tricalt
- Date: 2026-05-17
- Type: X post linking to X Article
- Capture method: X API metadata plus xAI-extracted article summary

## Summary
This source argues that memory and skills are two views of the same agent harness. Memory is the broad world model an agent uses to act, while skills are compressed procedures and traces of what has worked before. The article's central claim is that separating them into static product primitives misses the important loop: observe the environment, inspect whether the current skill/memory still fits, amend it, and evaluate the next run.

## Key Claims
- Agent memory is not only saved facts; it includes the codebase, tools, filesystem, conversation history, preferences, and observations that shape action.
- Skills are not merely static Markdown prompts; they are reusable, task-specific memory about how to act.
- Skills degrade when the environment changes, so skill maintenance needs an active improvement loop.
- A useful memory system should route, inspect, and revise skills as part of the same world model.
- Cognee is presented as an example where skills are ingested as first-class memory nodes and skill changes become memory events.

## Evidence / Examples
- The X API exposes the linked article title and post metadata.
- xAI extraction summarizes the article's Cognee example: cognee.remember("skills/") treats skill files as memory nodes shared by retrieval and self-improvement runtime.
- The source points to a broader convergence aro

### NewsPicks Topic - ハーネスエンジニアリングとは一体何なのか

Source note: `wiki/sources/newspicks-harness-engineering-what-is-it.md`

# NewsPicks Topic - ハーネスエンジニアリングとは一体何なのか

## Source Metadata
- Raw path: raw/articles/newspicks-harness-engineering-what-is-it-2026-05-17.md
- Original URL: https://newspicks.com/news/16607103/body/
- Author / publisher: NewsPicks Topic owner / NewsPicks topic page
- Date: not visible in capture
- Type: Japanese explainer article / topic post
- Capture date: 2026-05-17

## Summary
This article is a Japanese explainer on the overloaded meaning of "harness engineering." Its main contribution is separating the older evaluation-harness meaning from the newer agent-harness meaning, then decomposing agent harnesses into runtime, context, and safety layers. It also warns against two common mistakes: treating harness engineering as merely prompt engineering, and treating harness wins as evidence that model capability no longer matters.

## Key Claims
- Harness engineering became prominent because multiple sources reported large performance differences from changing the system around a fixed model.
- Evaluation harnesses and agent harnesses should be kept distinct: the former grade model/task performance, while the latter shape real operational behavior.
- The agent-harness term currently bundles at least three layers: runtime harness, context harness, and safety harness.
- Context-harness examples include instructions, rule files, memory, retrieval indexes, MCP tools, hooks, skills, and AGENTS.md-style files.
- Safety-harness examples include sandboxes, permissions, approval flows, and audit logs.
- Harness engineering is not just prompt collection; deterministic constraints, repo-local documents, linters, CI, observability, handoff files, and review loops are core parts of the practice.
- Model quality still matters: models set the ceiling, while harnesses determine how much o

### Izanami - Claude Code を大規模コードベースで使うベストプラクティス

Source note: `wiki/sources/izanami-claude-code-large-codebase-best-practices.md`

# Izanami - Claude Code を大規模コードベースで使うベストプラクティス

## Source Metadata
- Raw path: raw/articles/izanami-claude-code-large-codebase-best-practices-2026-05-16.md
- Original URL: https://izanami.dev/post/af045ef8-eff9-4317-b05a-abce17e14f55
- Author / publisher: コムテ / izanami.dev
- Date: 2026-05-16
- Type: Japanese practitioner explainer / commentary on official Anthropic guidance
- Capture date: 2026-05-17
- Primary referenced source: [[anthropic-claude-code-large-codebases.md]]

## Summary
The article translates Anthropic's Claude Code large-codebase guidance into an operator checklist: because Claude Code searches the live repository rather than relying on a prebuilt RAG index, large-repo performance depends on harness quality. It emphasizes thin and hierarchical CLAUDE.md files, starting work from relevant subdirectories, using hooks for self-improvement and deterministic checks, pruning stale rules after capability changes, and assigning an owner for organization-wide agent configuration.

## Key Claims
- Claude Code's live file-tree and grep-style navigation avoids stale indexes but needs repo-local hints about where to look.
- The useful harness layering order is CLAUDE.md -> hooks -> skills -> plugins -> MCP; teams should stabilize context files and hooks before adding heavier extension surfaces.
- A thin root CLAUDE.md plus local subdirectory rules improves context precision more than one large global instruction file.
- Starting Claude Code from the task-relevant subdirectory is a context-engineering move: it narrows search space while still inheriting parent context.
- Stop hooks can turn recent session learnings into proposed CLAUDE.md updates, making rule maintenance part of normal work.
- Rules and hooks are perishable. Teams should audit them every 3-6 months, a

### awebai/agent-first-company-template

Source note: `wiki/sources/aweb-agent-first-company-template.md`

# awebai/agent-first-company-template

## Source Metadata
- Raw path: raw/repos/aweb-agent-first-company-template-2026-05-17.md
- Original URL: https://github.com/awebai/agent-first-company-template
- Author: aweb.ai
- Date: 2026-05-17 capture
- Type: GitHub repository / operating-model template

## Summary
The repository is the companion template for aweb.ai's agent-first company model. It provides a forkable directory structure for company-level agent instructions, team roles, invariants, decision logs, voice notes, status files, and per-agent role directories.

The template emphasizes staged adoption: first add a reviewer voice and durable decision records without new tools; then adapt role docs and persistent contexts; finally add direct AI-to-AI messaging through aweb CLI or hosted MCP when human relay overhead becomes painful.

## Key Claims
- Agent-first operating discipline can start before direct AI-to-AI messaging.
- The core template surfaces are company instructions, team role map, decision log, status files, and per-agent role directories.
- Tools are secondary to habits: decision records, per-surface status, written handoffs, build/ship boundaries, and two-voice review.
- The template is intentionally provider- and stack-agnostic.

## Evidence / Examples
- Visible structure includes CLAUDE.md, AGENTS.md, docs/team.md, docs/decisions.md, status/weekly.md, and example agents/lead, agents/builder, agents/runner directories.
- README positions the repo as forkable scaffolding rather than a prescriptive org chart.

## Evidence Quality
- Source type: public repository / template.
- Confidence: Medium for file structure and stated adoption path; low for effectiveness without external case evidence.
- Supports: [[../concepts/agent-first-organization.md]], [[../con

### aweb.ai - How to set up an AI-native organization

Source note: `wiki/sources/aweb-ai-first-company-howto.md`

# aweb.ai - How to set up an AI-native organization

## Source Metadata
- Raw path: raw/articles/aweb-ai-first-company-howto-2026-05-17.md
- Original URL: https://aweb.ai/blog/ai-first-company-howto
- Author: aweb.ai
- Date: 2026-05-17 capture
- Type: company operating-model article / practitioner case study

## Summary
The article argues that AI-native organization design is not just employees using chatbots faster. In an AI-native company, named agents own work surfaces, carry persistent context, message each other directly, and coordinate through durable artifacts such as tasks, decision records, handoffs, status files, release evidence, and signal notes. Humans keep founding judgment, direction, customer trust, hiring, and publishing authority.

The aweb.ai case study describes seven persistent agents plus ephemeral coding agents and two humans. Its main durable claim is not the exact role roster, but the operating discipline: agents need identities, addresses, role docs, a shared taskboard, learning mechanisms, builder/reviewer splits, and artifact-based shared state.

## Key Claims
- AI-assisted work speeds up individual workflows; AI-native organization changes coordination itself.
- Agents should be first-class citizens with stable identities, addresses, named responsibilities, and persistent context.
- Work that matters should produce durable artifacts, not disappear into chat.
- Substantial work needs at least two voices: builder and reviewer.
- Shared state beats status routing: the company should be queryable through taskboards, status files, decision records, and handoffs.
- Solo operators can start with builder+reviewer pairs; organizations should move to named roles when repeated decision surfaces need ownership.
- Feedback should be captured with strengt

### Hermes Daily Brief

Source note: `wiki/sources/itsolelehmann-hermes-daily-brief-x-2026-05-15.md`

# Hermes Daily Brief

## Source Metadata
- Raw path: `raw/articles/itsolelehmann-hermes-daily-brief-2026-05-17.md`
- Original URL: https://x.com/i/status/2055290989577753034
- Canonical URL: https://x.com/i/status/2055290989577753034
- Author: Ole Lehmann (@itsolelehmann)
- Date: 2026-05-15
- Type: X post

## Summary
The visible part of the post outlines a Hermes workflow that produces a morning daily brief: it collects calendar items, urgent email, weather, and a few interest-feed headlines into one scheduled digest. The post frames this as part of a larger chief-of-staff stack.

## Key Claims
- Hermes can be used as a recurring daily brief agent.
- The daily brief combines multiple personal context sources into one output.
- The workflow is meant to run on a schedule, at 7am in the example.
- The post suggests a broader Hermes workflow stack beyond the visible brief.

## Evidence / Examples
- Captured from xurl bookmarks snapshot on 2026-05-17; post id `2055290989577753034`.
- Only the first workflow in the thread is visible in the captured text.
- The visible workflow explicitly names calendar, urgent email, weather, and headlines as inputs.

## Evidence Quality
- Source type: X post.
- Confidence: Medium.
- Supports: background-agent scheduling, agent management, and chief-of-staff style workflows.
- Main limitations: the capture text is truncated and does not include the rest of the 9-workflow list.
- Best use: a compact example of a scheduled personal-agent digest workflow.

## Related Concepts
- [[../concepts/background-agents.md]]
- [[../concepts/agent-management.md]]
- [[../concepts/agent-captain.md]]
- [[../concepts/long-running-agents.md]]

## Related Sources
- [[../sources/mvanhorn-hermes-agent-real-world-workflows-x.md]]
- [[../sources/nyk-builderz-4-agent-

### Peter Steinberger - Clawpatch automated code review

Source note: `wiki/sources/steipete-clawpatch-automated-code-review-x-2026-05-16.md`

# Peter Steinberger - Clawpatch automated code review

## Source Metadata
- Raw path: `raw/articles/steipete-clawpatch-automated-code-review-2026-05-17.md`
- Original URL: https://x.com/i/status/2055657966515155293
- Canonical URL: https://x.com/i/status/2055657966515155293
- Author: Peter Steinberger (@steipete)
- Date: 2026-05-16
- Type: X post + product site
- Primary URL: https://clawpatch.ai

## Summary
Clawpatch is an automated code review tool that maps a repository into semantic work units, reviews bounded context, and persists findings for follow-up. The product page makes the review loop explicit: init, map, review, report, fix, and revalidate.

## Key Claims
- Clawpatch reviews code at the feature/work-unit level rather than by file only.
- Findings include severity, confidence, evidence, and a recommendation.
- The product is designed around an explicit review-and-revalidate loop.
- Local Codex is presented as the default provider path for review.

## Evidence / Examples
- Captured from xurl bookmarks snapshot on 2026-05-17; post id `2055657966515155293`.
- The bookmark points to the product site `https://clawpatch.ai`, which is the stronger source for feature details.
- The site describes `clawpatch init`, `map`, `review`, `report`, `fix`, and `revalidate`.

## Evidence Quality
- Source type: X post + product site.
- Confidence: High.
- Supports: harness design, review automation, and verification-cost analysis.
- Main limitations: the X post itself is brief; the product page is the real evidence layer.
- Best use: a concrete example of automated code review that turns verification into a repeatable loop.

## Related Concepts
- [[../concepts/harness-engineering.md]]
- [[../concepts/coding-agents.md]]
- [[../concepts/verification-tax.md]]
- [[../concepts/evi

## 更新された概念・地図

### Concept Notes

KB note: `wiki/concepts/README.md`

# Concept Notes

Each note in this folder should represent a reusable concept that appears across multiple sources.

Recommended structure:
- definition
- why it matters
- related concepts
- supporting sources
- tensions / tradeoffs
- open questions

- [Evidence Quality](evidence-quality.md)
- [Field-Deployed Engineer](field-deployed-engineer.md)
- [Product Responsibility Distribution](product-responsibility-distribution.md)
- [Conversion Packaging](conversion-packaging.md)
- [Organizational Intent Clarity](organizational-intent-clarity.md)
- [Exploratory Organization Lens](exploratory-organization-lens.md)
- [Intelligent Delegation](intelligent-delegation.md)
- [Conversational Feedback Learning](conversational-feedback-learning.md)
- [Spec-Code-Test Loop](spec-code-test-loop.md)
- [Heavy Thinking](heavy-thinking.md)
- [Sustainable AI Work](sustainable-ai-work.md)
- [AI Adoption J-Curve](ai-adoption-j-curve.md)
- [AI ROI Model](ai-roi-model.md)
- [Verification Tax](verification-tax.md)

### Agent Knowledge Loop

KB note: `wiki/concepts/agent-knowledge-loop.md`

---
aliases:
  - Agent Knowledge Loop
---

# Agent Knowledge Loop

## Definition
A recurring loop where an LLM ingests sources, compiles notes, answers questions over the resulting wiki, and files useful outputs back into the knowledge base.

## Why It Matters
This loop turns the knowledge base into a compounding system rather than a static archive.

## Related Concepts
- [[compiled-wiki.md]]
- [[knowledge-base-linting.md]]
- [[agent-autonomy.md]]

## Supporting Sources
- [[../sources/karpathy-personal-llm-kb.md]]
- [[../sources/coreyganim-karpathy-second-brain-clearly-explained-x.md]]
- [[../sources/coreyganim-second-brain-monthly-audit-x.md]]
- [[../sources/shannholmberg-llm-wikid-x.md]]
- [[../sources/artemxtech-llm-wiki-vs-notebooklm-x.md]]
- [[../sources/arxiv-externalization-in-llm-agents.md]]
- [[../sources/carnot-cyclist-continual-learning-desiderata-x.md]]
- [[../sources/google-research-nested-learning-continual-learning.md]]
- [[../sources/akshay-pachaar-wiki-plus-graph-db-kb

### Context File System

KB note: `wiki/concepts/context-file-system.md`

---
aliases:
  - Context File System
---

# Context File System

## Definition
A lightweight external-memory pattern where an assistant reads and updates a small set of durable files such as instructions, memory, and project context instead of relying only on chat history or product-native saved memory.

## Why It Matters
It offers a practical middle layer between built-in chat memory and a full knowledge graph or second-brain system. For many workflows, a few well-maintained files provide enough persistence, inspectability, and editability to improve consistency.

## Related Concepts
- [[compiled wiki]]
- [[obsidian as interface]]
- [[durability]]
- [[tool accessibility]]

## Supporting Sources
- [[../sources/gargetisha-openclaw-under-the-hood-x-article.md]]
- [[../sources/aiedge-supercharge-claude-memory-x.md]]
- [[../sources/obsidian-mind-github.md]]
- [[../sources/sukh-saroy-obsidian-mind-x.md]]
- [[../sources/karpathy-personal-llm-kb.md]]
- [[../sources/coreyganim-karpathy-second-

### Memory-Skill Harness

KB note: `wiki/concepts/memory-skill-harness.md`

---
aliases:
  - Unified Memory-Skill Harness
  - Memory-Skill Harness
---

# Memory-Skill Harness

## Definition
A harness pattern where memory and skills are treated as one evolving world model: memory stores the state and evidence an agent acts from, while skills store reusable procedures derived from successful or corrected traces.

## Why It Matters
Separating memory from skills can make both brittle. Memory becomes passive storage if it cannot route the right procedure, and skills become stale prompt snippets if they cannot observe environmental change, attach evidence, and update themselves. A unified memory-skill harness makes repeated work inspectable, revisable, and queryable.

## Related Concepts
- [[agent-knowledge-loop.md]]
- [[navigable-agent-skills.md]]
- [[context-file-system.md]]
- [[context-graph.md]]
- [[rule-update-loop.md]]
- [[harness-engineering.md]]

## Supporting Sources
- [[../sources/tricalt-memory-skills-same-harness-x.md]]
- [[../sources/knowledgesense-corp

### Navigable Agent Skills

KB note: `wiki/concepts/navigable-agent-skills.md`

---
aliases:
  - Navigable Agent Skills
  - Corpus2Skill
  - Hierarchical RAG
---

# Navigable Agent Skills

## Definition
A retrieval architecture where a corpus is compiled into a hierarchy of human/model-readable skill or index files, so an agent can navigate the corpus structure before retrieving underlying documents.

## Why It Matters
It changes the model’s role from passive consumer of search results to active navigator of an information architecture. This is especially useful for broad or completeness-oriented questions where top-k vector retrieval may miss scattered evidence.

## Related Concepts
- [[compiled-wiki.md]]
- [[agent-knowledge-loop.md]]
- [[context-graph.md]]
- [[tool-accessibility.md]]
- [[agent-recognizable-repository.md]]

## Supporting Sources
- [[../sources/coreyganim-karpathy-second-brain-clearly-explained-x.md]]
- [[../sources/knowledgesense-corpus2skill-zenn.md]]
- [[../sources/aws-agent-toolkit-for-aws-x.md]]
- [[../sources/googlecloudjp-agent-skills-repos

### Rule-Update Loop

KB note: `wiki/concepts/rule-update-loop.md`

---
aliases:
  - Rule-Update Loop
  - Mistake-to-Rule Loop
---

# Rule-Update Loop

## Definition
A lightweight harness pattern where repeated prompts, recurring corrections, or observed agent mistakes are converted into durable rules in files such as `CLAUDE.md`, `AGENTS.md`, skills, templates, or team playbooks.

## Why It Matters
It lowers repeated review cost. Instead of correcting the agent one chat at a time, the human improves the operating environment so future sessions start with better guidance.

## Related Concepts
- [[harness-engineering]]
- [[context-file-system]]
- [[behavioral-stability]]
- [[agent-recognizable-repository]]
- [[approval-policy]]

## Supporting Sources
- [[../sources/claudecode-love-boris-30-claude-code-tips-x.md]]
- [[../sources/gota-purpose-first-harness-design-speakerdeck.md]]
- [[../sources/rkaga-what-harness-engineering-is-and-is-not-zenn.md]]
- [[../sources/masaki-claude-md-rules-for-non-engineers.md]]
- [[../sources/mnilax-karpathy-claude-md-rules-

### Agent Harness Control Taxonomy

KB note: `wiki/maps/agent-harness-control-taxonomy.md`

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
- **Context harness**: instructions, rule files, memory, retrieval, tools, hooks, skills, MCP servers, an

### Context Graph and Company Brain

KB note: `wiki/maps/context-graph-and-company-brain.md`

# Context Graph and Company Brain

## Purpose
This map connects the emerging vocabulary around company-scale agent memory: compiled wiki, context graph, Company Brain, and context farming.

## Core Pattern
1. Raw organizational signals enter the system: docs, chat, logs, emails, tickets, meetings, and decisions.
2. A context layer extracts entities, relationships, rules, provenance, and validity windows.
3. Agents query the layer before acting, ideally receiving only context that is relevant, permitted, and still valid.
4. Humans maintain the layer through review, invalidation, conflict resolution, and context farming.
5. Dreaming-style background review can propose memory cleanup and cross-session pattern promotion, but should preserve provenance and review boundaries.

In an agent-first company, this context layer also becomes an operating surface: named agents read and update role docs, taskboards, status files, decision records, handoffs, and feedback-strength notes so the organiza

## NotebookLM Podcast用メモ

- まず今日の全体トレンドを話してから、重要ソースを3本に絞って深掘りする。
- ソース単体の紹介で終わらせず、既存KBの概念や地図がどう更新されたかを会話に含める。
- 最後に、明日以降の調査問いを2〜3個提示する。
