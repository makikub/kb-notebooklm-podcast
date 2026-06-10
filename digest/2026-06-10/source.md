<!-- generated: 2026-06-10T13:01:25.211014+00:00 -->
<!-- kb_daily_digest_date: 2026-06-10 -->
# KB Daily Digest Source — 2026-06-10

このページは、knowledge-base-llm の日次更新を NotebookLM に読み込ませるための公開向けソースページです。
Discord通知よりも文脈を厚めに残し、Podcast化しやすいように、今日追加・更新されたソース、概念、地図を文章中心で整理します。

## 今日の全体像

# KB Daily Digest 2026-06-10

2026-06-10 UTC の knowledge-base-llm では、Anthropic の Claude Fable 5 / Mythos 5 発表、NotebookLM の研究ワークスペース強化、Claude Code の nested subagent support、Fable 5 を前提にした loop design、そして組織AI推進ロードマップが新規 ingest された。全体のトレンドはかなり明確で、単体プロンプトや単発チャットではなく、「長く動くエージェント」「複数ワーカーを束ねるループ」「評価・検証を含むハーネス」「組織に定着させる行動変容」へ知識ベースの焦点が寄っている。

重要ソースの1本目は、Anthropic の Claude Fable 5 / Mythos 5 launch cluster。新モデルは難しい知識労働とコーディングを主戦場に置き、長めの自律作業、より良い不確実性の扱い、動的ワークフロー、並列 subagent、検証を前面に出している。KB上では long-running agents、agent autonomy、self-verification、multi-agent orchestration、harness engineering の周辺概念に接続された。これは「良いモデルを呼ぶ」から「モデルが走る仕事場を設計する」への移行を補強する材料になっている。

2本目は、RLanceMartin の “Designing loops with Fable 5”。取得できた本文は限定的だが、検索可視断片とメタデータから、Fable 5 級モデルでは小さな直接指示ではなく、より大きな目的、agent worker、grading step を含むループ設計が重要になる、という実務的な主張として整理された。この ingest により `loop-engineering.md` が新規作成され、generator-evaluator loop、harness engineering、task decomposition と結び直された。今日の更新の中では、技術トレンドを運用パターンに落とす中核ノードになっている。

3本目は、しんちゃん氏の note「組織のAI推進：完全ロードマップ」。このソースは、AI導入をツール配布ではなく利用率ごとの行動変容設計として扱っている。20%未満、20〜50%、50〜80%、80%以上という大まかな段階を置き、初期は利用実態の可視化と早期利用者の火付け、中盤はリテラシーと部門別ユースケース、高利用率ではAI前提の業務変革に進む、という筋立てだ。KBでは `ai-adoption-thresholds.md` が新規作成され、AI adoption J-curve、AI ROI model、organizational intent clarity、context file system、agent management に接続された。

Claude Code nested subagent support の短いリリースノートも重要な補助線になった。Boris Cherny 氏の投稿は、Claude Code に agent が agent を起動できる nested subagent support が入り、文脈管理のための実験として depth=5 から始める、という内容だった。これは multi-agent orchestration と coding agents の更新に反映され、1つの巨大なセッションに全作業を抱え込ませるのではなく、文脈を分割しながら階層的に作業する方向を示している。

NotebookLM の better research launch cluster は、KBの「compiled knowledge」側を強く支える更新だった。Gemini 3.5、モデルの思考過程の可視化、secure cloud computer、100以上の curated software skills という方向性は、NotebookLM を単なるQA付きノートではなく、出典つき調査・分析・成果物生成のワークスペースとして位置付けている。KBでは compiled wiki、agent knowledge loop、context graph、rich agent output artifact、evidence quality と接続され、今日のDigestページやPodcast生成そのものの背景にもなる。

概念・地図の更新としては、`loop-engineering.md` と `ai-adoption-thresholds.md` の追加が特に大きい。前者はモデル性能の進歩を、目的、文脈、役割、ツール、努力量、チェックポイント、評価、リトライ、停止条件の設計問題として捉える。後者は組織導入を、利用率という観測可能な状態に応じて打ち手を変える問題として捉える。片方はエージェントの作業ループ、もう片方は組織の学習ループであり、今日の更新はこの2つを同時に進めたと言える。

実務上の読みどころは、強いモデルの登場が自動的に成果を生むわけではなく、むしろ「どう走らせ、どう採点し、どう組織に定着させるか」の設計責任が増している点にある。技術側では subagent、grader、loop、harness が重要になり、組織側では利用率測定、行動変容、文脈ファイル化、業務テンプレート、slash command、review DB のような反復可能な仕組みが重要になる。今日のKB更新は、モデル発表をニュースとして処理するのではなく、現場で使える設計語彙に変換する方向で compile されている。

次に追う問いは3つある。第一に、nested subagent や大規模な並列 worker は、どの粒度のタスクで品質向上が coordination cost を上回るのか。第二に、loop engineering の rubric や grader は、どこまで汎用化でき、どこから領域固有に作り込むべきか。第三に、組織AI導入の利用率しきい値は、活動量ではなく成果・品質・持続性とどう結びつけて測るべきか。今日の更新は、この3点を今後のKB拡張テーマとしてかなりはっきり浮かび上がらせている。

## 重要ソース

- Anthropic - Claude Fable 5 / Mythos 5 launch cluster: `raw/articles/anthropic-fable-5-mythos-5-launch-cluster-x-2026-06-09.md`
- RLanceMartin - Designing loops with Fable 5: `raw/articles/rlancemartin-designing-loops-with-fable-5-x-2026-06-09.md`
- shin_suge - Organization AI rollout roadmap and behavior-change design: `raw/articles/shin-suge-ai-ops-roadmap-behavior-change-note-2026-06-09.md`

## 新規・更新された主なKBノード

- `wiki/concepts/loop-engineering.md`
- `wiki/concepts/ai-adoption-thresholds.md`
- `wiki/concepts/multi-agent-orchestration.md`
- `wiki/concepts/coding-agents.md`
- `wiki/concepts/generator-evaluator-loop.md`
- `wiki/concepts/harness-engineering.md`
- `wiki/maps/ai-adoption-roi-and-capability-investment.md`


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

### shin_suge - Organization AI rollout roadmap and behavior-change design

Source note: `wiki/sources/shin-suge-ai-ops-roadmap-behavior-change-note-2026-06-09.md`

# shin_suge - Organization AI rollout roadmap and behavior-change design

## Metadata
- Source: note.com article
- URL: https://note.com/shin_suge/n/ne89b086a3063
- Author: しんちゃん ｜ ログラス 社長室 AIOps / CursorAmbassador
- Published: 2026-06-09
- Raw capture: [[../../raw/articles/shin-suge-ai-ops-roadmap-behavior-change-note-2026-06-09.md]]
- Evidence quality: practitioner field report; strong for rollout heuristics and operating patterns, weaker for universal numeric thresholds because the article explicitly treats percentages as rough guides.

## Summary
This article presents an organization-level AI rollout roadmap from the perspective of an AI-Ops practitioner. Its central thesis is that AI adoption is less a tool-installation problem than a behavior-change and workflow-design problem. The recommended playbook changes by adoption phase: measure current usage, ignite early adopters, reach a majority with targeted use cases and literacy, then only after broad adoption move into deeper workflow transformation.

## Key Claims
- AI usage rate should guide rollout strategy. Under 20%, visualize usage and build early-adopter momentum; around 20-50%, focus on targeted use cases and behavior-change design; around 50-80%, let social proof and data/context loops compound; at 80%+, pursue workflow transformation.
- Starting from business-process improvement can fail when people lack lived understanding of what AI can and cannot do; literacy and personal usage need to come first.
- "Organization usage" is not just individual usage multiplied by headcount. Shared work patterns, context artifacts, and adoption roles matter.
- Cursor, Claude Code, Codex, and similar tools are useful not only as interfaces, but because they help accumulate reusable data and context.
- Internal constraints

### RLanceMartin - Designing loops with Fable 5

Source note: `wiki/sources/rlancemartin-designing-loops-with-fable-5-x-2026-06-09.md`

# RLanceMartin - Designing loops with Fable 5

## Metadata
- Source: X Article shared by Lance Martin
- URL: https://x.com/RLanceMartin/status/2064397389189071163
- Article URL: https://x.com/RLanceMartin/article/2064397389189071163
- Author: Lance Martin (@RLanceMartin)
- Date: 2026-06-09
- Raw capture: [[../../raw/articles/rlancemartin-designing-loops-with-fable-5-x-2026-06-09.md]]
- Evidence quality: partial capture; X API provided metadata and title, while content is inferred from public search snippets.

## Summary
Lance Martin's X Article is a practitioner signal that Claude Fable 5 usage should be organized around loops, not only better prompts. The available snippets say Mythos-class models changed work practices at Anthropic, recommend giving Fable 5 larger and more ambitious tasks, and point toward high-effort modes plus agent-worker/evaluator loops for best results.

## Key Claims
- Fable 5 makes larger task scopes more practical than earlier models, shifting the useful unit of work upward.
- The operator's job moves from direct instruction alone toward designing the loop the model runs inside.
- Evaluation or grading is part of the loop, not an afterthought, because ambitious tasks need convergence pressure.

## Evidence / Examples
- The X article title and share metadata are available through X API.
- Search snippets expose the core framing: "Designing loops with Fable 5", larger tasks, high/xhigh effort, and an agent-worker plus grading loop.
- The article sits in the same launch cluster as Anthropic's Fable 5 / Mythos 5 messaging around longer autonomous runs, dynamic workflows, and self-verification.

## Related Concepts
- [[../concepts/loop-engineering.md]]
- [[../concepts/harness-engineering.md]]
- [[../concepts/generator-evaluator-loop.md]]
- [[../con

### Boris Cherny — Claude Code nested subagent support

Source note: `wiki/sources/bcherny-claude-code-nested-subagents-x-2026-06-09.md`

# Boris Cherny — Claude Code nested subagent support

## Source Metadata
- Raw path: `raw/articles/bcherny-claude-code-nested-subagents-x-2026-06-09.md`
- Original URL: https://x.com/bcherny/status/2064327225504403752
- Author: Boris Cherny (`@bcherny`)
- Date: 2026-06-09
- Type: X post / product release note
- Evidence strength: High for feature announcement; low for operational outcomes

## Summary
Boris Cherny announced that Claude Code added nested subagent support, allowing agents to start other agents as an explicit context-management mechanism. The initial release caps nesting at depth 5.

## Key Claims
- Claude Code now supports nested subagents.
- Agent-to-agent spawning is being explored as a way to manage context.
- The first rollout constrains recursion with a depth cap of 5.

## Evidence / Examples
- The source is a direct public post from Boris Cherny, a Claude Code product leader.
- The post does not include docs, examples, pricing implications, or measured workflow outcomes.

## Evidence Quality
- Source type: first-party X announcement
- Confidence: High that the feature landed in the referenced release
- Main limitations: terse announcement; does not specify concurrency limits, permission inheritance, termination behavior, memory sharing, or best practices

## Related Concepts
- [[multi-agent-orchestration]]
- [[coding-agents]]
- [[context-resets]]
- [[background-agents]]

## Open Questions
- When does recursive subagent spawning improve context isolation versus merely increasing coordination overhead?
- What depth and concurrency limits keep nested delegation useful in real coding projects?
- How should nested agents inherit tools, permissions, memory, and approval boundaries from parent agents?
- What observability does a parent agent need to avoid l

### Anthropic - Claude Fable 5 / Mythos 5 launch cluster

Source note: `wiki/sources/anthropic-fable-5-mythos-5-launch-cluster-x-2026-06-09.md`

# Anthropic - Claude Fable 5 / Mythos 5 launch cluster

## Source Metadata
- Raw path: `raw/articles/anthropic-fable-5-mythos-5-launch-cluster-x-2026-06-09.md`
- Original URL: https://x.com/i/status/2064394146916229443
- Primary URL: https://www.anthropic.com/news/claude-fable-5-mythos-5
- Author: Claude / @claudeai
- Date: 2026-06-09
- Type: X post / release cluster
- Evidence strength: bookmark snapshot metadata plus official Anthropic launch article
- Capture source: xurl bookmarks capture
- Public metrics at capture: 10747 reposts, 3560 replies, 76499 likes, 6911 quotes, 14599 bookmarks, 18687414 impressions

## Summary

Anthropic introduces Claude Fable 5 and Claude Mythos 5 as a new top-end model release for the hardest knowledge work and coding problems. The launch messaging emphasizes longer autonomous runs, better honesty about uncertainty, and dynamic workflows that can spin up many parallel subagents and verify the result before reporting back.

## Key Claims

- Fable 5 and Mythos 5 are the newest Anthropic flagship models in this launch cluster.
- The release is framed around more autonomous work, stronger coding help, and better support for knowledge work.
- Anthropic is making dynamic workflows a first-class product surface in Claude Code.
- The model and product messaging both stress honesty and reduced unsupported claims.

## Evidence / Examples

- The official launch post says the models are safe for general use and exceed previous generally available models.
- The official Anthropic article says the models can work autonomously for longer and that dynamic workflows can coordinate hundreds of parallel subagents.
- The surrounding bookmarked commentary reinforces that the release is being read as a major step up in day-to-day Claude Code use.

## Evidenc

### NotebookLM - better research launch cluster

Source note: `wiki/sources/notebooklm-better-research-gemini-3-5-antigravity-x-2026-06-08.md`

# NotebookLM - better research launch cluster

## Source Metadata
- Raw path: `raw/articles/notebooklm-better-research-gemini-3-5-antigravity-x-2026-06-08.md`
- Original URL: https://x.com/i/status/2064084153533165588
- Primary URL: https://blog.google/innovation-and-ai/products/notebooklm/better-research-notebooklm/
- Author: NotebookLM / @NotebookLM
- Date: 2026-06-08
- Type: X post / launch cluster
- Evidence strength: bookmark snapshot metadata plus official Google blog launch article
- Capture source: xurl bookmarks capture
- Public metrics at capture: 216 reposts, 49 replies, 1760 likes, 35 quotes, 809 bookmarks, 170229 impressions

## Summary

NotebookLM upgrades its research experience with Gemini 3.5, better visibility into the model's thinking, a secure cloud computer, and a bundled set of more than 100 curated software skills. The product direction is clearly toward an agentic research workspace that can reason over sources, run code, and generate richer artifacts.

## Key Claims

- NotebookLM is moving deeper into an agentic research workflow.
- Gemini 3.5 and Antigravity are being used to improve visible reasoning and reliability.
- Each notebook now has access to a secure cloud computer for deeper analysis.
- Skills are packaged as part of the product surface, not as a separate afterthought.

## Evidence / Examples

- The bookmark text says the launch adds better visibility into the AI's thinking process.
- The official Google blog article says each notebook gets a secure cloud computer and more than 100 curated software skills.
- The article positions the change as a more thoughtful chat and research experience rather than a narrow notebook editor.

## Evidence Quality

- Source type: X launch cluster plus official Google product blog
- Confidence: high f

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
- [AI Adoption Thresholds](ai-adoption-thresholds.md) — usage-rate bands th

### Agent Management

KB note: `wiki/concepts/agent-management.md`

---
aliases:
  - Agent Management
---

# Agent Management

## Definition
The human work of assigning tasks, monitoring progress, adjusting the environment, and deciding when to intervene in agent workflows.

## Why It Matters
As agents become more capable, value comes not just from using them but from managing them well. The current source set suggests that workflow design, escalation choices, and background-task supervision are becoming durable human responsibilities rather than temporary scaffolding.

## Related Concepts
- [[agent-captain]]
- [[background-agents]]
- [[harness-engineering]]

## Supporting Sources
- [[../sources/ignorance-ai-emerging-harness-engineering-playbook.md]]
- [[../sources/mitchell-hashimoto-ai-adoption-journey.md]]
- [[../sources/anthropic-claude-code-web-scheduled-tasks-docs.md]]
- [[../sources/nyk-builderz-4-agent-hermes-operator-layer-x.md]]
- [[../sources/sydneyrunkle-agent-harness-vs-runtime-production-x.md]]
- [[../sources/brett-goldstein-agentic-micro-

### AI Adoption J-Curve

KB note: `wiki/concepts/ai-adoption-j-curve.md`

---
aliases:
  - AI Adoption J-Curve
  - J-Curve of AI Value Realization
  - Tuition Cost of AI Adoption
---

# AI Adoption J-Curve

## Definition
A temporary productivity dip and instability period that can occur when teams adopt AI-assisted development before later realizing higher throughput and value.

## Why It Matters
AI adoption changes workflows, review load, context practices, and deployment pipelines. Treating the initial dip as failure can cause leaders to cut funding too early; ignoring it can make ROI forecasts unrealistic.

## Related Concepts
- [[ai-roi-model]]
- [[verification-tax]]
- [[harness-engineering]]
- [[context-engineering]]
- [[sustainable-ai-work]]
- [[human-in-the-loop]]

## Supporting Sources
- [[../sources/dora-roi-ai-assisted-software-development.md]]
- [[../sources/iwashi86-ai-lowers-barrier-to-starting-coding-work-x.md]]
- [[../sources/suna_gaku-claude-code-champion-kit-x-2026-05-16.md]]
- [[../sources/itmedia-github-copilot-pricing-backlash-x-2026-06-0

### AI Adoption Thresholds

KB note: `wiki/concepts/ai-adoption-thresholds.md`

---
aliases:
  - AI Adoption Thresholds
  - AI Usage Rate Thresholds
  - Adoption-Phase AI Rollout
---

# AI Adoption Thresholds

## Definition
AI adoption thresholds are rough usage-rate bands that change which organization-level AI rollout moves are appropriate.

## Why It Matters
AI rollout failures often come from applying the wrong move at the wrong maturity level: buying tools before measuring usage, pushing workflow transformation before literacy, or treating individual experimentation as organization-wide adoption. Thresholds make adoption strategy conditional on observed behavior.

## Related Concepts
- [[ai-adoption-j-curve.md]]
- [[ai-roi-model.md]]
- [[organizational-intent-clarity.md]]
- [[agent-management.md]]
- [[context-engineering.md]]
- [[loop-engineering.md]]

## Supporting Sources
- [[../sources/shin-suge-ai-ops-roadmap-behavior-change-note-2026-06-09.md]]
- [[../sources/dora-roi-ai-assisted-software-development.md]]
- [[../sources/suna_gaku-claude-code-champion-kit

### AI ROI Model

KB note: `wiki/concepts/ai-roi-model.md`

---
aliases:
  - AI ROI Model
  - ROI of AI-assisted Software Development
  - AI Value Model
---

# AI ROI Model

## Definition
A structured way to estimate the return on AI-assisted software development by linking AI adoption to delivery metrics, business value, and adoption costs.

## Why It Matters
AI productivity claims are not enough for enterprise adoption. A credible model connects engineering indicators to financial outcomes while accounting for hard costs, learning costs, instability, and uncertainty.

## Related Concepts
- [[ai-adoption-j-curve]]
- [[verification-tax]]
- [[evidence-quality]]
- [[organizational-intent-clarity]]
- [[product-responsibility-distribution]]
- [[sustainable-ai-work]]
- [[agentic-jevons-paradox]]

## Supporting Sources
- [[../sources/dora-roi-ai-assisted-software-development.md]]
- [[../sources/simon-willison-gitlab-act-2.md]]
- [[../sources/simon-willison-product-market-fit.md]]
- [[../sources/tsunoda-legalon-ai-driven-hiring-token-budget-x-2026-05-

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

### Organizational Intent Clarity

KB note: `wiki/concepts/organizational-intent-clarity.md`

---
aliases:
  - Organizational intent clarity
  - Goal clarity for AI adoption
---

# Organizational Intent Clarity

## Definition
The degree to which a team can state stable goals, desired outcomes, constraints, and evaluation criteria clearly enough for humans and agents to act on them.

## Why It Matters
When intent is vague or constantly shifting, AI systems look unreliable even when the underlying model is capable. The practical bottleneck moves from “can the model do it?” to “has the organization expressed what should be done, why, and how success will be judged?”

## Related Concepts
- [[context-engineering.md]]
- [[exploratory-organization-lens.md]]
- [[company-brain.md]]
- [[product-responsibility-distribution.md]]
- [[agent-management.md]]
- [[evidence-quality.md]]

## Supporting Sources
- [[../sources/iwashi86-organizational-ai-use-goal-clarity-x.md]]
- [[../sources/anzai-adventurous-organization-emconf-youtube.md]]
- [[../sources/recerqa-pdm-abolished-speakerdeck.md]]
- [[

### AI Adoption ROI and Capability Investment

KB note: `wiki/maps/ai-adoption-roi-and-capability-investment.md`

# AI Adoption ROI and Capability Investment

## Purpose
Map how AI-assisted software development becomes financial value only when capability investments let the organization absorb faster generation safely.

## Core thesis
AI ROI is not a direct function of model quality or code volume. It is a system outcome: AI adoption must be mediated by internal platforms, context/data quality, trust, user focus, verification guardrails, and delivery metrics before it can become durable business value. The strongest upside case is not only cheaper execution of existing backlog, but Jevons-style expansion in software demand when new tools, experiments, and automations become economical.

## Path from AI adoption to ROI

### 1. Capability investment first
The first question is not “which tool?” but “can the system absorb the tool?” DORA's report emphasizes quality internal developer platforms, AI-accessible internal data, clear AI stance/trust, context engineering, user-centric focus, and automated

## NotebookLM Podcast用メモ

- まず今日の全体トレンドを話してから、重要ソースを3本に絞って深掘りする。
- ソース単体の紹介で終わらせず、既存KBの概念や地図がどう更新されたかを会話に含める。
- 最後に、明日以降の調査問いを2〜3個提示する。
