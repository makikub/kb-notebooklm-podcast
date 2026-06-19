<!-- generated: 2026-06-19T13:01:35.443594+00:00 -->
<!-- kb_daily_digest_date: 2026-06-19 -->
# KB Daily Digest Source — 2026-06-19

このページは、knowledge-base-llm の日次更新を NotebookLM に読み込ませるための公開向けソースページです。
Discord通知よりも文脈を厚めに残し、Podcast化しやすいように、今日追加・更新されたソース、概念、地図を文章中心で整理します。

## 今日の全体像

# KB Daily Digest 2026-06-19

UTC 2026-06-19 の knowledge-base-llm 更新は、Dan Farrelly の X Article「The Agent Loop Architecture」の partial capture を中心にした小さめだが焦点のはっきりした ingest だった。新規 raw は `raw/articles/djfarrelly-agent-loop-architecture-x-2026-06-18.md`、新規 wiki source は `wiki/sources/djfarrelly-agent-loop-architecture-x.md`。あわせて `loop-engineering`、`agent-harness-landscape`、`operations` navigation、`INDEX`、source README が更新され、KB上では「loop をどう設計するか」から一歩進んで「その loop を何が走らせるのか」という運用ランタイム側の問いが補強された。

今回の重要ソースは1本だけだが、既存KB内の関連ソースと合わせると、今日の読みどころは3点に整理できる。第一に Dan Farrelly の新規 source note は、agent loop を単なる「LLM + tools」や while-loop 的な推論パターンとしてではなく、永続化・リトライ・再開・人間チェックポイントを含む durable orchestration の問題として扱う。第二に Addy Osmani の「Loop Engineering」は、agent に成果へ向かう反復構造を与える設計面の語彙を提供しており、Farrelly の問いはそこに runtime / runner のレイヤーを足す位置づけになる。第三に Lance Martin / Fable 5 系の loop design notes は、大きめのタスク、worker loop、grading、effort selection、停止条件という実践側の設計課題を示していて、Farrelly の「what runs the loop?」と自然に接続する。

ただし証拠品質には注意が必要。今回の raw capture は X の公開カードと検索スニペットに基づく partial capture で、本文全文はログインが必要だった。X API 側も `CreditsDepleted` で取得できていないため、KB note では「公開カードと検索-visible snippets で確認できる範囲」に主張を限定している。特に「durable orchestration is fundamental」という方向性は見えているが、Farrelly が具体的にどの orchestration primitives を推奨しているか、決定論的 workflow engine と model-directed loop control をどう分けているかは、今後全文を取得できたら再確認すべき open question として残った。

全体トレンドとしては、KB内の agent harness landscape がさらに「内側の agent loop」から「外側の実行基盤」へ重心を移している。ここ数日の KB では loop engineering、Fable 5、dynamic workflows、project loop、self-improving system など、反復構造そのものを語るソースが増えていた。今日の更新は、その反復構造が実務システムになる瞬間に必要な、状態の置き場所、失敗時の復帰、非同期イベント、監視、権限境界、human checkpoint をまとめて扱う視点を足している。

概念更新では `wiki/concepts/loop-engineering.md` に、async gap、retry、human checkpoint、external event をまたぐ loop には prompt pattern だけでなく runner / runtime が必要だ、という一文が追加された。これにより、loop engineering は「プロンプトや評価器の設計」だけでなく、「loop がどこで継続し、どこで止まり、どの証拠で再開するか」を扱う概念として少し広がった。安定した高頻度 loop は将来的に workflow compilation の候補になりうる、という既存の論点とも相性がよい。

地図更新では `wiki/maps/agent-harness-landscape.md` に Dan Farrelly / Agent loop architecture のセクションが追加された。ここでは「what runs the loop?」が、inner loop の話から durable orchestration、persistence、retry、event resumption、operational runtime へのシフトとして位置づけられている。`wiki/navigation/operations.md` にも source entrypoint が追加され、長時間稼働、scheduled work、monitoring、handoff、context reset などの運用系の問いからこのソースに辿れるようになった。

実務上の示唆は、agent loop を導入するときに「ループの形」だけを設計しても足りないという点にある。1回のセッションで完結する探索なら、LLMに tools を渡して self-check させる程度で十分なこともある。しかし、外部イベントを待つ、数時間後に再開する、失敗時に再試行する、人間承認を挟む、複数の worker / reviewer / grader を使う、といった条件が入ると、設計対象は prompt から orchestration substrate に移る。どの状態を durable にするか、どのログを evidence として残すか、retry budget と停止条件をどこに置くかが、品質と安全性を左右する。

Podcastで掘るなら、今日は「loop は agent の思考様式なのか、それとも運用システムなのか」という問いを中心にすると話しやすい。まず Addy Osmani 的な loop engineering の背景を置き、次に Fable 5 / dynamic workflow 系の実践例を挟み、最後に Farrelly の「what runs the loop?」で runner / runtime / durable orchestration の話へ広げる構成がよい。明日以降の追跡ポイントは、Farrelly 本文の full capture、durable orchestration primitives の具体例、そして ephemeral loop と durable loop を分ける判断基準の3つ。

公開HTML: https://makikub.github.io/kb-notebooklm-podcast/digest/2026-06-19/

NotebookLM用 source.md: https://makikub.github.io/kb-notebooklm-podcast/digest/2026-06-19/source.md


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
- [[simon-willison-product-market-fit.md]] — Simon Willison's market analysis that Anthropic/OpenAI have found product-market fit through coding/general-purpose agents, API-aligned enterprise pricing, and high-value professional usage.
- [[simon-willison-gitlab-act-2.md]] — Simon Willison on GitLab's Act 2 announcement, organization flattening, smaller empowered R&D teams, and the agentic-era Jevons-style software demand thesis.
- [[google-research-nested-learning-continual-learning.md]] — Google Research on Nested Learning, continuum memory systems, and Hope as a model-internal continual-learning architecture.
- [[anthropic-claude-code-large-codebases.md]] — Anthropic on Claude Code at large-codebase scale: live-code navigation, harness extension points, layered context files, LSP/subagents, and org ownership.
- [[about-hiroppy-founders-playbook.md]] — Anthropic's official founder playbook PDF: AI-native startup lifecycle across Idea, MVP, Launch, and Scale, with Claude Chat/Cowork/Code stage usage, validation gates, agentic technical debt risks, founder bottleneck removal, and moat formation.
- [[izanami-claude-code-large-codebase-best-practices.md]] — Japanese practitioner explainer on Claude Code large-codebase setup: live repo search, thin layered CLAUDE.md, subdirectory startup, hooks, stale-rule pruning, and adoption ownership.
- [[newspicks-harness-engineering-what-is-it.md]] — Japanese explainer separating evalua

### Dan Farrelly - The Agent Loop Architecture

Source note: `wiki/sources/djfarrelly-agent-loop-architecture-x.md`

# Dan Farrelly - The Agent Loop Architecture

## Metadata
- Source: X post linking to X Article
- URL: https://x.com/djfarrelly/status/2067677007140278630
- Article URL: https://x.com/i/article/2067632189865365504
- Author: Dan Farrelly | Inngest.com (@djfarrelly)
- Date: 2026-06-18
- Raw capture: [[../../raw/articles/djfarrelly-agent-loop-architecture-x-2026-06-18.md]]
- Evidence quality: partial capture; public X card and search snippets only, because X API returned `CreditsDepleted` and the full article required login.

## Summary
Farrelly's article card frames "The Agent Loop Architecture" around a sharper question than "what is a loop?": what runs the loop? The available snippets suggest the answer is durable orchestration. This makes the source useful as a bridge between [[../concepts/loop-engineering.md]] and [[../concepts/harness-engineering.md]]: agent loops are not just a reasoning pattern, but a runtime architecture that needs persistence, retries, observability, and operational boundaries.

## Key Claims
- The AI-agent discussion has converged on loops as a core primitive, but the design question shifts to the system that runs the loop.
- A bare "LLM + tools" framing is too thin for practical agent-loop architecture.
- Durable orchestration is a central ingredient for building agent loops that survive beyond a single prompt-response interaction.

## Evidence / Examples
- The X card explicitly says the article asks "what runs the loop?" after noting that the discourse has converged on loops.
- Search snippets expose the phrase "durable orchestration is fundamental to building your agent loop architecture."
- The source is affiliated with Inngest, so the durable-orchestration emphasis likely reflects workflow-runtime concerns, but that is an inference from aff

## 更新された概念・地図

### Loop Engineering

KB note: `wiki/concepts/loop-engineering.md`

---
aliases:
  - Loop Engineering
  - Agent Loop Design
---

# Loop Engineering

## Definition
Loop engineering is the practice of designing the repeatable work loop an agent runs inside: objective, context, worker roles, tool access, effort level, checkpoints, grading, retries, and stopping conditions.

## Origin / Framing
The term was popularized in June 2026 by Addy Osmani's "Loop Engineering" article. Osmani framed it around two public practitioner signals: Peter Steinberger's claim that developers should design loops that prompt coding agents, and Boris Cherny's claim that his job had shifted from prompting Claude directly to writing loops.

## Why It Matters
As models handle larger tasks, the operator's leverage shifts from writing one perfect prompt toward defining a loop that can generate work, evaluate it, and converge. This makes loop design a practical sub-surface of [[harness-engineering.md]].

## Related Concepts
- [[harness-engineering.md]]
- [[generator-evaluator-loop.md

### Agent Harness Landscape

KB note: `wiki/maps/agent-harness-landscape.md`

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
- machine-c

### Navigation: Operations / Long-Running Work

KB note: `wiki/navigation/operations.md`

# Navigation: Operations / Long-Running Work

## Use When
The question is about running agents over time: background agents, routines, scheduled work, handoffs, context resets, delegation, or monitoring.
It also covers whether a recurring workflow should stay explicit or be compiled into model behavior.

## Start Maps
- [[../maps/ai-adoption-roi-and-capability-investment.md]]
- [[../maps/context-management-decisions.md]]
- [[../maps/orchestration-patterns-faq.md]]
- [[../maps/approval-policy-patterns-and-escalation.md]]

## Core Concepts
- [[../concepts/ai-adoption-j-curve.md]]
- [[../concepts/agentic-product-market-fit.md]]
- [[../concepts/ai-native-startup-lifecycle.md]]
- [[../concepts/verification-tax.md]]
- [[../concepts/ai-roi-model.md]]
- [[../concepts/agentic-jevons-paradox.md]]
- [[../concepts/long-running-agents.md]]
- [[../concepts/background-agents.md]]
- [[../concepts/agent-first-organization.md]]
- [[../concepts/managed-agents.md]]
- [[../concepts/agent-dreaming.md]]
- [[

## NotebookLM Podcast用メモ

- まず今日の全体トレンドを話してから、重要ソースを3本に絞って深掘りする。
- ソース単体の紹介で終わらせず、既存KBの概念や地図がどう更新されたかを会話に含める。
- 最後に、明日以降の調査問いを2〜3個提示する。
