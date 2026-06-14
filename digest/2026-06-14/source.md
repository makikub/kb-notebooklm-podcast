<!-- generated: 2026-06-14T13:01:49.356289+00:00 -->
<!-- kb_daily_digest_date: 2026-06-14 -->
# KB Daily Digest Source — 2026-06-14

このページは、knowledge-base-llm の日次更新を NotebookLM に読み込ませるための公開向けソースページです。
Discord通知よりも文脈を厚めに残し、Podcast化しやすいように、今日追加・更新されたソース、概念、地図を文章中心で整理します。

## 今日の全体像

# KB Daily Digest 2026-06-14

今日の knowledge-base-llm は、「エージェントに何をさせるか」から一段進んで、「エージェントが参照・反復・交換できる知識とループをどう設計するか」に焦点が寄った更新でした。UTC 2026-06-14 の新規 ingest / compile は 3 コミットで、raw 記録が 8 件、wiki/source ノートが 7 件追加され、`open-knowledge-format`、`compiled-wiki`、`context-graph`、`loop-engineering`、`context-graph-and-company-brain` などが更新されています。

全体トレンドは、Markdown ベースの知識、状態を持つエージェント実行基盤、ループ設計、モデル/クォータ運用が同じ運用面に集まりつつある、というものです。Google Cloud の Open Knowledge Format は、LLM wiki 的な知識を「サービス」ではなく「交換可能なファイル形式」として扱う提案です。一方で Addy Osmani の loop engineering は、人間が毎回プロンプトを書くのではなく、目的、状態、検証、再試行、停止条件を持つループそのものを設計対象にする見方を強めています。

重要ソースの1本目は、Google Cloud Blog の「Introducing the Open Knowledge Format」です。OKF v0.1 は、Markdown ファイル、YAML frontmatter、ファイルパスによる概念識別、Markdown リンク、任意の `index.md` / `log.md` を組み合わせ、エージェントやカタログ、ビジュアライザが同じ知識束を読み書きできるようにする提案です。KB にとっては、これまでの `compiled-wiki` や `context-graph` の方向性を外部の一次ソースで補強する更新であり、ローカルな知識整理を超えて「別の producer / consumer と交換できる最小契約」へ話が広がりました。

重要ソースの2本目は、Addy Osmani の「Loop Engineering」です。この記事は、プロンプト、コンテキスト、ハーネスの上位に、定期実行、worktree、skills、plugins/connectors、sub-agents、外部メモリを含むループ設計の層を置きます。特に KB では、loop engineering を「1回の agent run を支える harness」より上にある、反復・発見・検証・状態保存の運用設計として整理しました。無人ループにはコスト上限と停止条件が必要で、強いモデルほどループを雑に大きくするのではなく、何を証拠に完了とするかを先に決める必要があります。

重要ソースの3本目は、Cloudflare Agents SDK / Build Agents on Cloudflare の docs カードです。X ブックマーク由来なので本文全体の一次取得ではありませんが、公式 docs preview と日本語コメントからは、persistent memory、realtime WebSockets、scheduled tasks、Durable Objects による状態保持、React の `useAgent`、CLI からの更新といった実行基盤の特徴が読み取れます。これは loop engineering の実装先として重要で、ループや長時間エージェントを「チャット履歴」ではなく、状態同期できる runtime に載せる流れを示しています。

周辺ソースでは、Z.ai の GLM-5.2 / devpack 最新モデル、Kimi-K2.7-Code、OpenAI Codex の rate limit reset を後で使える機能、Akshay Pachaar の self-repairing agent harness 記事カードが追加されました。これらは単体ではモデルリリースや小さなプロダクト更新に見えますが、まとめると「モデルを切り替えられること」「トークン効率や agent performance を見ること」「利用枠を作業タイミングに合わせて保存すること」「ハーネスが自分の詰まりを検出・修復すること」が、エージェント運用の当たり前の面になってきていると読めます。

概念更新としては、`open-knowledge-format` が新設され、OKF を Markdown-first な知識束の交換形式として定義しました。`compiled-wiki` と `context-graph` には、Markdown の inspectability と typed graph の権限・時間・関係処理をどう組み合わせるかという論点が補強されています。`context-graph-and-company-brain` では、OKF-style bundle を Markdown wiki と typed graph の中間的な相互運用層として位置づけ、`loop-engineering` では term の起源、実務部品、コスト/停止条件の注意が整理されました。

実務上の読みどころは、知識基盤とエージェント基盤を別々に考えないことです。OKF のような形式が普及すると、エージェントは「検索で似たテキストを拾う」だけでなく、概念、リンク、ログ、frontmatter、鮮度、出典をもつ知識 bundle を前提に行動できるようになります。そのうえで loop engineering を組むなら、ループの入力はただの長いプロンプトではなく、検証可能で差分管理できる知識リポジトリになります。

次に追う問いは、OKF が provenance、permissions、freshness、confidence、derived claims をどこまで最小スキーマで扱えるか、Cloudflare の stateful agent runtime がどの程度まで業務ループの system of record になれるか、そして self-repairing harness の修復範囲をどう監査可能に保つかです。Podcast では、OKF を「LLM wiki の HTML 化」ではなく「agent knowledge の可搬形式」として捉えること、loop engineering を「自動化の美名」ではなく停止条件と証拠設計の技術として扱うこと、モデル/クォータ/ランタイムの更新が運用設計にどう跳ね返るかを掘るとよさそうです。

## 重要ソース3本

- `wiki/sources/google-cloud-open-knowledge-format.md`
- `wiki/sources/addyosmani-loop-engineering.md`
- `wiki/sources/yusuke-wada-cloudflare-agents-sdk-build-agents-on-cloudflare-x-2026-06-13.md`

## 更新された主なKBノート

- `wiki/concepts/open-knowledge-format.md`
- `wiki/concepts/compiled-wiki.md`
- `wiki/concepts/context-graph.md`
- `wiki/concepts/loop-engineering.md`
- `wiki/maps/context-graph-and-company-brain.md`
- `wiki/navigation/memory.md`
- `wiki/sources/README.md`


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

### Addy Osmani - Loop Engineering

Source note: `wiki/sources/addyosmani-loop-engineering.md`

# Addy Osmani - Loop Engineering

## Metadata
- Source: blog post
- URL: https://addyosmani.com/blog/loop-engineering/
- Author: Addy Osmani
- Date: 2026-06-07
- Raw capture: [[../../raw/articles/addyosmani-loop-engineering-2026-06-07.md]]
- Evidence quality: primary synthesis article by a named practitioner; cites public statements from Peter Steinberger and Boris Cherny as the trigger signals.

## Summary
Addy Osmani's article popularizes "loop engineering" as the next operator surface after prompt, context, and harness engineering. The core shift is from manually prompting a coding agent turn by turn to designing a small system that finds work, prompts agents, verifies outputs, stores state, and decides the next action.

## Key Claims
- Loop engineering replaces the human as the direct prompter with a system that prompts agents against a recurring goal.
- A loop sits one level above an agent harness: the harness supports one agent run; the loop runs harnessed agents over time.
- Practical loops need automations, worktrees, skills, plugins/connectors, sub-agents, and durable state.
- The useful loop shape is becoming tool-agnostic across Codex-style and Claude Code-style systems.
- Cost controls and verifiable stopping conditions are necessary because unattended loops can amplify mistakes.

## Evidence / Examples
- Osmani cites Peter Steinberger's framing that developers should design loops that prompt agents.
- Osmani cites Boris Cherny's statement that he writes loops instead of prompting Claude directly.
- The article maps loop primitives to Codex and Claude Code capabilities: scheduled automations, worktree isolation, skills, MCP-style connectors, sub-agents, and external state.

## Related Concepts
- [[../concepts/loop-engineering.md]]
- [[../concepts/harness-eng

### Google Cloud - Introducing the Open Knowledge Format

Source note: `wiki/sources/google-cloud-open-knowledge-format.md`

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
- The core bundle is "just" Markdown files, a filesystem/git-friendly directory structure, and a small frontmatter surface.
- OKF v0.1 requires a `type` field and leaves domain models, sections, and producer-specific details open.
- Producer and consumer independence is the main design contract: humans, metadata pipelines, or LLMs can produce bundles; agents, visualizers, search systems, or other LLMs can consume them.

## Evidence / examples
-

### Akshay Pachaar - Your Agent Harness Should Repair Itself

Source note: `wiki/sources/akshay-pachaar-your-agent-harness-should-repair-itself-x-2026-06-08.md`

# Akshay Pachaar - Your Agent Harness Should Repair Itself

## Source Metadata
- Raw path: `raw/articles/akshay-pachaar-your-agent-harness-should-repair-itself-x-2026-06-08.md`
- Original URL: https://x.com/i/status/2064051835636498924
- Primary URL: https://x.com/i/article/2063964921495523328
- Author: Akshay Pachaar / @akshay_pachaar
- Posted: 2026-06-08T18:28:00.000Z
- Captured: 2026-06-14 via xurl bookmarks capture
- Type: X post / X article card
- Evidence strength: bookmark snapshot metadata plus article title card
- Public metrics at capture: 138 reposts, 28 replies, 1043 likes, 6 quotes, 2353 bookmarks, 479637 impressions

## Summary
The article argues that an effective agent harness should be able to repair its own bottlenecks instead of depending on the operator to keep every loop healthy. That framing pushes the design problem away from one-off prompting and toward feedback loops, routines, and operational self-maintenance.

## Key Claims
- The operator should not remain the bottleneck for a running agent system.
- Harness quality is partly about whether the system can detect and repair its own failure points.
- Loop design matters because repeated routines can absorb work that would otherwise require human attention.

## Evidence / Examples
- The bookmark is only an article card in the captured X data, so the title is the strongest directly visible evidence here.
- The share from Avi Chawla reinforces the same theme by quoting the article's leverage/bottleneck language.

## Related Concepts
- [[../concepts/harness-engineering.md]]
- [[../concepts/failure-modes.md]]
- [[../concepts/self-verification.md]]
- [[../concepts/loop-engineering.md]]
- [[../concepts/agent-autonomy.md]]

## Related Maps
- [[../maps/coding-agent-harness-patterns.md]]
- [[../maps/agent-h

### Kimi.ai - Kimi-K2.7-Code release

Source note: `wiki/sources/kimi-k2-7-code-release-x-2026-06-12.md`

# Kimi.ai - Kimi-K2.7-Code release

## Source Metadata
- Raw path: `raw/articles/kimi-k2-7-code-release-x-2026-06-12.md`
- Original URL: https://x.com/i/status/2065377579130142937
- Related bookmarked post: https://x.com/i/status/2065473287761891621
- Author: Kimi.ai / @Kimi_Moonshot
- Posted: 2026-06-12T10:16:02.000Z
- Captured: 2026-06-14 via xurl bookmarks capture
- Type: X post / model release card
- Evidence strength: bookmark snapshot metadata with benchmark-heavy release messaging
- Public metrics at capture: 1545 reposts, 575 replies, 12940 likes, 660 quotes, 2530 bookmarks, 1769148 impressions

## Summary
Kimi's K2.7 Code release is framed as a coding-specialized, open-sourced model with better benchmark performance and lower token use than K2.6. The announcement is mostly product messaging, but it is still a useful signal that coding-model competition is continuing to move toward lower-token and higher-agent-performance claims.

## Key Claims
- K2.7 Code is positioned as the latest coding model in the Kimi line.
- The release claims better coding and agent performance than K2.6.
- The model is being marketed as more token-efficient, not just more accurate.

## Evidence / Examples
- The bookmark text explicitly cites benchmark deltas and a lower-token-efficiency claim.
- The related Cline bookmark repeats the same positioning in a more adoption-oriented way.

## Related Concepts
- [[../concepts/llm-inference-performance.md]]
- [[../concepts/coding-agents.md]]
- [[../concepts/agent-autonomy.md]]
- [[../concepts/harness-engineering.md]]

## Related Maps
- [[../maps/agent-harness-landscape.md]]
- [[../maps/harness-engineering-vendor-comparison.md]]
- [[../maps/coding-agent-harness-patterns.md]]

## Open Questions
- How much of the token reduction survives in real 

### OpenAI - Codex rate limit resets can be saved for later

Source note: `wiki/sources/openai-codex-rate-limit-resets-x-2026-06-12.md`

# OpenAI - Codex rate limit resets can be saved for later

## Source Metadata
- Raw path: `raw/articles/openai-codex-rate-limit-resets-x-2026-06-12.md`
- Original URL: https://x.com/i/status/2065225362544726371
- Author: OpenAI / @OpenAI
- Posted: 2026-06-12T00:11:11.000Z
- Captured: 2026-06-14 via xurl bookmarks capture
- Type: X post / product update
- Evidence strength: bookmark snapshot metadata plus rollout announcement
- Public metrics at capture: 1714 reposts, 1245 replies, 21384 likes, 1475 quotes, 3609 bookmarks, 4148349 impressions

## Summary
OpenAI is making Codex rate-limit resets bankable, so users can save a reset and spend it later instead of losing it when they do not need it. That is a small feature on paper, but it changes how users schedule bursts of agent work around their own time and attention.

## Key Claims
- Rate-limit resets can now be deferred and used later.
- The feature is rolling out with one free saved reset for several paid tiers.
- Usage budgeting is becoming a more explicit product surface.

## Evidence / Examples
- The announcement is directly visible in the captured tweet text.
- The feature is tied to a tiered rollout, so it is not just a design idea.

## Related Concepts
- [[../concepts/sustainable-ai-work.md]]
- [[../concepts/agent-autonomy.md]]
- [[../concepts/approval-policy.md]]
- [[../concepts/verification-tax.md]]

## Related Maps
- [[../maps/approval-policy-patterns-and-escalation.md]]
- [[../maps/agent-deployment-gates-and-operational-risk.md]]
- [[../maps/coding-agent-cognitive-debt-and-review-capacity.md]]

## Open Questions
- Does banked quota meaningfully reduce interruption, or does it just shift when the interruption happens?
- Which kinds of agent work benefit most from time-shifted rate limits?

## Backlinks
- [[..

### Yusuke Wada - Cloudflare Agents SDK / Build Agents on Cloudflare

Source note: `wiki/sources/yusuke-wada-cloudflare-agents-sdk-build-agents-on-cloudflare-x-2026-06-13.md`

# Yusuke Wada - Cloudflare Agents SDK / Build Agents on Cloudflare

## Source Metadata
- Raw path: `raw/articles/yusuke-wada-cloudflare-agents-sdk-build-agents-on-cloudflare-x-2026-06-13.md`
- Original URL: https://x.com/i/status/2065743993531777173
- Related bookmarked post: https://x.com/i/status/2065737438853747124
- Primary URL: https://developers.cloudflare.com/agents/
- Author: Yusuke Wada / @yusukebe
- Posted: 2026-06-13T10:32:02.000Z
- Captured: 2026-06-14 via xurl bookmarks capture
- Type: X post / docs card
- Evidence strength: bookmark snapshot metadata plus official docs preview
- Public metrics at capture: 30 reposts, 0 replies, 365 likes, 4 quotes, 418 bookmarks, 90384 impressions

## Summary
Cloudflare's Agents SDK is being framed as a practical stateful-agent runtime: persistent memory, realtime WebSocket connections, and scheduled tasks, with the Japanese commentary emphasizing that state can be retained, synchronized, paused, and even updated from the CLI.

## Key Claims
- Agents on Cloudflare are now presented as stateful rather than purely request/response tools.
- Durable Objects are doing the persistence and synchronization work underneath the SDK.
- `useAgent` makes the runtime feel native to React.
- CLI updates are part of the operational surface, not an afterthought.

## Evidence / Examples
- The docs card itself names persistent memory, realtime WebSockets, and scheduled tasks.
- The commentary post adds implementation intuition: keep state, sync it, pause it, and mutate it from a command line.

## Related Concepts
- [[../concepts/managed-agents.md]]
- [[../concepts/background-agents.md]]
- [[../concepts/long-running-agents.md]]
- [[../concepts/tool-accessibility.md]]
- [[../concepts/harness-engineering.md]]

## Related Maps
- [[../maps/agent-

### Z.ai - GLM-5.2 / How to Switch Models

Source note: `wiki/sources/zai-glm-5-2-devpack-latest-model-x-2026-06-13.md`

# Z.ai - GLM-5.2 / How to Switch Models

## Source Metadata
- Raw path: `raw/articles/zai-glm-5-2-devpack-latest-model-x-2026-06-13.md`
- Original URL: https://x.com/i/status/2065704919299235870
- Primary URL: https://docs.z.ai/devpack/latest-model
- Author: Z.ai / @Zai_org
- Posted: 2026-06-13T07:56:46.000Z
- Captured: 2026-06-14 via xurl bookmarks capture
- Type: X post / docs card
- Evidence strength: bookmark snapshot metadata plus official docs preview
- Public metrics at capture: 751 reposts, 263 replies, 6204 likes, 341 quotes, 1046 bookmarks, 975234 impressions

## Summary
Z.ai is surfacing GLM-5.2 as the latest model in its developer plan, and the linked docs page shows how model switching works inside the coding-plan product. The most KB-relevant detail is that the docs explicitly map model names and environment variables, which makes the release feel operational rather than just promotional.

## Key Claims
- GLM-5.2 is available to GLM Coding Plan users across multiple plan tiers.
- The docs treat model switching as a first-class developer workflow.
- The page exposes environment-variable mapping for agentic tooling, which matters for portability across coding agents.

## Evidence / Examples
- The docs preview explicitly says the plan supports GLM-5.2 and tells readers to use `/llms.txt` for the documentation index.
- The captured preview also lists environment variable mappings for Claude Code.

## Related Concepts
- [[../concepts/llm-inference-performance.md]]
- [[../concepts/coding-agents.md]]
- [[../concepts/agent-management.md]]
- [[../concepts/harness-engineering.md]]

## Related Maps
- [[../maps/agent-harness-landscape.md]]
- [[../maps/harness-engineering-vendor-comparison.md]]
- [[../maps/coding-agent-harness-patterns.md]]

## Open Questions
- How muc

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

### Compiled Wiki

KB note: `wiki/concepts/compiled-wiki.md`

---
aliases:
  - Compiled Wiki
---

# Compiled Wiki

## Definition
A compiled wiki is a curated layer of linked Markdown notes derived from raw sources, rather than a direct dump of source material.

## Why It Matters
It lets an LLM work over a cleaner, more connected representation of knowledge while preserving traceability back to raw evidence.

## Related Concepts
- [[agent knowledge loop]]
- [[obsidian as interface]]
- [[knowledge base linting]]
- [[open-knowledge-format]]

## Supporting Sources
- [[../sources/karpathy-personal-llm-kb.md]]
- [[../sources/coreyganim-karpathy-second-brain-clearly-explained-x.md]]
- [[../sources/coreyganim-second-brain-monthly-audit-x.md]]
- [[../sources/shannholmberg-llm-wikid-x.md]]
- [[../sources/farza-farzapedia-x.md]]
- [[../sources/fieldtheory-cli-github.md]]
- [[../sources/obsidian-mind-github.md]]
- [[../sources/contextconor-enterprise-understanding-context-graph-x.md]]
- [[../sources/artemxtech-llm-wiki-vs-notebooklm-x.md]]
- [[../sources/aks

### Context Graph

KB note: `wiki/concepts/context-graph.md`

---
aliases:
  - Context Graph
  - Context Graphs
---

# Context Graph

## Definition
A persistent graph-structured memory layer that represents facts, relationships, rules, exceptions, provenance, validity windows, and decision traces for agent use.

## Why It Matters
Context graphs aim to make agent memory auditable and updateable. They move beyond retrieving similar documents toward querying valid, permitted, relationship-aware context for a specific action.

## Related Concepts
- [[company brain]]
- [[compiled wiki]]
- [[open-knowledge-format]]
- [[agent knowledge loop]]
- [[human in the loop]]

## Supporting Sources
- [[../sources/tsumotokai-context-graphs-agent-long-term-memory-x.md]]
- [[../sources/contextconor-enterprise-understanding-context-graph-x.md]]
- [[../sources/brett-goldstein-agentic-micro-companies-company-brain-x.md]]

- [[../sources/notebooklm-gemini-app-integration-x.md]]

- [[../sources/knowledgesense-corpus2skill-zenn.md]]
- [[../sources/google-cloud-open-knowle

### Open Knowledge Format

KB note: `wiki/concepts/open-knowledge-format.md`

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
- [[context-file-system.md]]
- [[context-graph.md]]
- [[company-brain.md]]
- [[navigable-agent-skills.md]]
- [[evidence-quality.md]]

## Supporting Sources
- [[../sources/google-cloud-open-knowledge-format.md]]
- [[../sources/karpathy-personal-llm-kb.md]]
- [[../sources/nori-handa-karpathy-llm-wiki-zenn.md]]


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

### Navigation: Memory / Knowledge Substrate

KB note: `wiki/navigation/memory.md`

# Navigation: Memory / Knowledge Substrate

## Use When
The question is about agent memory, knowledge bases, compiled notes, context graphs, team/company brains, or retrieval architecture.

## Start Maps
- [[../maps/context-graph-and-company-brain.md]]
- [[../maps/research-os-query-paths.md]]
- [[../maps/agent-onboarding-kb-codebase.md]]

## Core Concepts
- [[../concepts/compiled-wiki.md]]
- [[../concepts/agent-knowledge-loop.md]]
- [[../concepts/continual-learning.md]]
- [[../concepts/agent-dreaming.md]]
- [[../concepts/context-file-system.md]]
- [[../concepts/context-engineering.md]]
- [[../concepts/llm-inference-performance.md]]
- [[../concepts/workflow-compilation.md]]
- [[../concepts/kv-cache.md]]
- [[../concepts/context-graph.md]]
- [[../concepts/company-brain.md]]
- [[../concepts/open-knowledge-format.md]]
- [[../concepts/agent-first-organization.md]]
- [[../concepts/organizational-intent-clarity.md]]
- [[../concepts/navigable-agent-skills.md]]
- [[../concepts/memory-skill-harne

## NotebookLM Podcast用メモ

- まず今日の全体トレンドを話してから、重要ソースを3本に絞って深掘りする。
- ソース単体の紹介で終わらせず、既存KBの概念や地図がどう更新されたかを会話に含める。
- 最後に、明日以降の調査問いを2〜3個提示する。
