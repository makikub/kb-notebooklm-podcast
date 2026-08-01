<!-- generated: 2026-08-01T13:02:22.213341+00:00 -->
<!-- kb_daily_digest_date: 2026-08-01 -->
# KB Daily Digest Source — 2026-08-01

このページは、knowledge-base-llm の日次更新を NotebookLM に読み込ませるための公開向けソースページです。
Discord通知よりも文脈を厚めに残し、Podcast化しやすいように、今日追加・更新されたソース、概念、地図を文章中心で整理します。

## 今日の全体像

# KB Daily Digest 2026-08-01

2026-08-01 UTC の knowledge-base-llm 更新は、X bookmarks batch と Namespace 公式ドキュメントの手動 ingest が重なった日でした。新規 raw は `raw/x/bookmarks/bookmarks-20260801T0000Z.json` と4本の X 由来 article note、さらに Namespace の Devin on Devboxes 公式ドキュメント HTML/Markdown です。wiki 側には5本の source note が追加され、`managed-agents`、`environment-bootstrapping`、`agent-harness-landscape`、`harness-engineering-vendor-comparison` が更新されました。X 由来の4本はスナップショット/カード中心なので evidence strength は medium 前後ですが、Namespace 公式ドキュメントは統合アーキテクチャとセットアップ手順の根拠として強めです。

今日の全体トレンドは、「coding agent の性能や実用性はモデル単体ではなく、知識の構造化、実行環境、ツール接続、製品化された常時稼働 runtime の組み合わせで決まる」という方向です。Claude 向け ontology、LLM Wiki、remote MCP、Gemini Spark、Devin on Namespace Devboxes は一見ばらばらですが、KB の地図では同じ問題に接続します。つまり、エージェントがうまく働くには、情報をどう整理するか、どこで実行するか、外部ツールへどう安全に繋ぐか、どの単位で管理・監査するかが重要になる、という読みです。

重要ソース1本目は Namespace の公式 Devin integration docs です。ここでは Devin Cloud が orchestration、planning、context management、inference を担い、Namespace Devboxes が shell commands、file edits、repository access、builds、tests を担うと明確に分離されています。Devin session が queue されると Namespace が fresh Devbox を provision し、その中で Devin Outposts worker が起動し、worker は outbound HTTPS で Devin Cloud へ接続します。session 終了時には worker が exit し Devbox が tear down されるため、cloud agent の「頭脳」と「手足」が別 plane になっている実例として読めます。

重要ソース2本目は Claude Code研究所の ontology / structure signal です。記事本文は今回の snapshot では取れていませんが、カードタイトルは「Claude の性能改善には、素材を増やすより ontology と構造が効く」という主張を示しています。これは KB 自身の raw/wiki 分離とかなり相性がよい更新です。raw を増やすだけではなく、source note、concept、map、open question へ編み直すことが、Claude や coding agent に渡す context の品質を上げるという仮説を補強します。

重要ソース3本目は HedgehogPython の LLM Wiki / codebase knowledge signal です。こちらも X bookmark 経由の Qiita 共有であり、本文の深掘りは次回課題ですが、「コードベース知識は LLM Wiki で十分かもしれない」という実務的な方向を示しています。RAG や検索基盤に raw source を積むだけではなく、コードベースを理解しやすい compiled wiki として整える発想は、agent に長期作業を任せる時の context engineering と workflow compilation の中心に近いです。

残りの2本も、agent harness の周辺地図を広げています。Mark Kretschmann の Gemini Spark global availability は、Google AI Pro / Ultra users 向けに 24/7 cloud agent が globally available になったという rollout signal で、long-running / managed agent が実験段階から配布面へ移る流れを示します。Yusuke Wada の Hono + TypeScript SDK v2 による remote MCP server signal は、agent の tool surface が特殊基盤ではなく ordinary web stack でも構築しやすくなっていることを示します。常時稼働の managed runtime と、軽量に立てられる remote tool server が並ぶことで、agent product の「操作面」と「接続面」の両方が現実的になっています。

KB 地図の更新としては、`managed-agents` に「cloud orchestration plane と fresh per-session execution plane の分離」が入り、`environment-bootstrapping` には predefined remote environments が setup entropy を下げる一方で、image freshness、access mode、teardown behavior、credential handling を設計問題として持ち込む、という tension が追加されました。`agent-harness-landscape` では Devin / Namespace の連携が、generic remote CLI ではなく environment-specific runtime substrate の例として補強されました。`harness-engineering-vendor-comparison` でも Cognition / Devin の distinctive emphasis に Devin Outposts worker と orchestration/execution-plane separation が加わっています。

実務上の読みどころは、エージェント運用の投資先が三層に分かれてきたことです。第一層は ontology / LLM Wiki のような知識編成で、モデルに渡す context の形を整える。第二層は Namespace Devbox や Gemini Spark のような managed runtime で、エージェントがどこで、どの権限で、どの lifecycle で動くかを決める。第三層は remote MCP のような tool connectivity で、agent が外部システムとやり取りする interface を整える。この三層が揃わないと、モデル性能だけを上げても現場の workflow には届きにくい、というのが今日の更新の中心です。

Podcastで掘るなら、まず「知識を増やすこと」と「知識を構造化すること」の違いを扱うとよさそうです。次に、Devin on Namespace Devboxes を例に、cloud agent の頭脳と実行環境が分離することで、セキュリティ、監査、再現性、credential handling がどう変わるかを話せます。最後に、Gemini Spark と remote MCP を並べて、agent が常時動くことと、必要な tool surface を普通の web framework で足せることが組み合わさると、企業の agent harness はどのような管理単位になるのか、という問いに展開できます。

次に追うべき問いは3つあります。まず、Namespace Devbox の isolation、secret handling、audit log、failure recovery は公式 docs の外でどこまで確認できるのか。次に、ontology / LLM Wiki の効果を「体感」ではなく coding agent の task success、review latency、context churn でどう測るのか。最後に、remote MCP が普通の web stack に乗るほど、auth、tenant boundary、tool permission、observability を誰がどのレイヤーで標準化するのか、です。

## Important Sources

- `https://namespace.so/docs/devbox/devin`
- `https://x.com/i/status/2082446956710998379`
- `https://x.com/i/status/2082714025969037383`
- `https://x.com/i/status/2082859528765178176`
- `https://x.com/i/status/2083146706326344182`

## New / Changed Files

- `raw/x/bookmarks/bookmarks-20260801T0000Z.json`
- `raw/articles/claudecode-lab-ontology-for-improving-claude-performance-x-2026-07-29.md`
- `raw/articles/hedgehogpython-codebase-knowledge-llm-wiki-enough-x-2026-07-30.md`
- `raw/articles/mark-k-gemini-spark-global-availability-x-2026-07-30.md`
- `raw/articles/yusuke-wada-remote-mcp-server-hono-typescript-sdk-v2-x-2026-07-31.md`
- `raw/articles/namespace-devin-ai-devbox-doc-2026-07-21.md`
- `raw/articles/namespace-devin-ai-devbox-doc-2026-07-21.html`
- `wiki/sources/claudecode-lab-ontology-for-improving-claude-performance-x-2026-07-29.md`
- `wiki/sources/hedgehogpython-codebase-knowledge-llm-wiki-enough-x-2026-07-30.md`
- `wiki/sources/mark-k-gemini-spark-global-availability-x-2026-07-30.md`
- `wiki/sources/yusuke-wada-remote-mcp-server-hono-typescript-sdk-v2-x-2026-07-31.md`
- `wiki/sources/namespace-devin-ai-devbox-doc.md`
- `wiki/INDEX.md`
- `wiki/concepts/environment-bootstrapping.md`
- `wiki/concepts/managed-agents.md`
- `wiki/maps/agent-harness-landscape.md`
- `wiki/maps/harness-engineering-vendor-comparison.md`


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

### Namespace - Devin on Devboxes documentation

Source note: `wiki/sources/namespace-devin-ai-devbox-doc.md`

# Namespace - Devin on Devboxes documentation

## Source Metadata
- Raw path: `../../raw/articles/namespace-devin-ai-devbox-doc-2026-07-21.md`
- Raw HTML: `../../raw/articles/namespace-devin-ai-devbox-doc-2026-07-21.html`
- Original URL: https://namespace.so/docs/devbox/devin
- Publisher: Namespace
- Page title: Devin AI | Namespace
- Last updated: 2026-07-21
- Captured: 2026-08-01
- Type: official product documentation
- Evidence strength: high for documented architecture and setup flow; low for performance or reliability claims because no benchmarks are provided

## Summary
Namespace documents a native Devin integration where Devin Cloud handles orchestration, planning, context management, and inference, while Namespace Devboxes handle shell commands, file edits, repository access, builds, and tests. The integration uses Devin Outposts: a Devin session is queued for a worker, Namespace provisions a fresh Devbox, starts the Devin worker inside it, and the worker connects outward to Devin Cloud over HTTPS. When the session ends, the worker exits and the Devbox is torn down.

## Key Claims
- Devin agents are natively supported on Namespace Devboxes.
- Devin's agent loop, planning, context management, and inference remain in Devin's cloud.
- Namespace Devboxes execute commands, edits, repository access, builds, and tests.
- Devboxes can run Linux or macOS, and macOS environments include mobile-development tools such as iOS simulators.
- The Devin Outposts connection uses outbound HTTPS only, with no inbound ports, public IPs, or VPN tunnels to configure.
- Each Devin session gets a freshly provisioned Devbox, and the Devbox is torn down when the session ends.
- Setup requires a Namespace account, Devin Cloud account, a Devbox blueprint, and connecting that blueprint to th

### Claude Code Research Lab - Ontology for improving Claude performance

Source note: `wiki/sources/claudecode-lab-ontology-for-improving-claude-performance-x-2026-07-29.md`

# Claude Code Research Lab - Ontology for improving Claude performance

## Source Metadata
- Raw path: `../../raw/articles/claudecode-lab-ontology-for-improving-claude-performance-x-2026-07-29.md`
- Raw bookmark capture: `../../raw/x/bookmarks/bookmarks-20260801T0000Z.json`
- Original URL: https://x.com/i/status/2082446956710998379
- Primary URL: https://x.com/i/article/2081012579737157632
- Author: Claude Code研究所|スパルタClaude Code塾 (@claudecode_lab)
- Posted: 2026-07-29T12:43:39.000Z
- Captured: 2026-08-01T00:00:22.073Z via xurl bookmarks capture
- Type: X post / article card
- Evidence strength: bookmark snapshot metadata plus X article card title
- Public metrics at capture: 225 likes, 30 reposts, 3 replies, 8 quotes, 450 bookmarks, 39323 impressions

## Summary
This is an article-card-only bookmark, but the title is useful: it argues that ontology and structure improve Claude performance more than simply adding more source material. That fits this KB's bias toward compiled, connected knowledge rather than raw accumulation.

## Key Claims
- Knowledge structure matters for Claude performance.
- Ontology is presented as a more important lever than adding more documents.
- The article is part 1 of a series, so the framing is likely meant to be systematic rather than anecdotal.

## Evidence / Examples
- The bookmark contains only the article card title, so the strongest evidence is the title itself.
- The title explicitly contrasts better structure with simply adding more material.
- The post is useful mainly as a signal that ontology work can pay off in agent performance contexts.

## Evidence Quality
- Source type: X post / article card
- Confidence: medium for the general structural claim, low-medium for any deeper specifics not present in the snapshot
- Supports: [[../

### HedgehogPython - LLM Wiki may be enough for codebase knowledge

Source note: `wiki/sources/hedgehogpython-codebase-knowledge-llm-wiki-enough-x-2026-07-30.md`

# HedgehogPython - LLM Wiki may be enough for codebase knowledge

## Source Metadata
- Raw path: `../../raw/articles/hedgehogpython-codebase-knowledge-llm-wiki-enough-x-2026-07-30.md`
- Raw bookmark capture: `../../raw/x/bookmarks/bookmarks-20260801T0000Z.json`
- Original URL: https://x.com/i/status/2082714025969037383
- Primary URL: https://qiita.com/Syoitu/items/ff38655fed51a2920910
- Author: HedgehogPython (@HedgehogPython)
- Posted: 2026-07-30T06:24:53.000Z
- Captured: 2026-08-01T00:00:22.073Z via xurl bookmarks capture
- Type: X post / link share to Qiita
- Evidence strength: bookmark snapshot metadata plus captured article title card
- Public metrics at capture: 28 likes, 4 reposts, 0 replies, 1 quote, 23 bookmarks, 3420 impressions

## Summary
This bookmark is a direct reminder that the Karpathy-style LLM Wiki pattern is still resonating as a practical alternative to dumping source material into a retrieval layer and hoping for the best. The signal aligns with this KB's own compiled/raw split.

## Key Claims
- A codebase knowledge layer can be built with an LLM Wiki pattern.
- The value is in curated compilation, not just in retrieval infrastructure.
- The Qiita article is framed as a practical explanation rather than a speculative architecture essay.

## Evidence / Examples
- The bookmark text explicitly says the article argues that LLM Wiki may be enough for codebase knowledge.
- The linked Qiita title is about codebase knowledge and LLM Wiki.
- The post sits in the same design space as this repo's own raw/wiki separation.

## Evidence Quality
- Source type: X post pointing to a Qiita article
- Confidence: medium for the practical claim, high that the article is a relevant practitioner signal
- Supports: [[../concepts/compiled-wiki.md]], [[../concepts/context-e

### Mark Kretschmann - Gemini Spark global availability

Source note: `wiki/sources/mark-k-gemini-spark-global-availability-x-2026-07-30.md`

# Mark Kretschmann - Gemini Spark global availability

## Source Metadata
- Raw path: `../../raw/articles/mark-k-gemini-spark-global-availability-x-2026-07-30.md`
- Raw bookmark capture: `../../raw/x/bookmarks/bookmarks-20260801T0000Z.json`
- Original URL: https://x.com/i/status/2082859528765178176
- Linked media URL: https://x.com/mark_k/status/2082859528765178176/photo/1
- Author: Mark Kretschmann (@mark_k)
- Posted: 2026-07-30T16:03:03.000Z
- Captured: 2026-08-01T00:00:22.073Z via xurl bookmarks capture
- Type: X post / product availability update
- Evidence strength: bookmark snapshot metadata plus visible media card
- Public metrics at capture: 764 likes, 44 reposts, 72 replies, 15 quotes, 220 bookmarks, 54827 impressions

## Summary
Gemini Spark shows up here as a globally available, always-on cloud agent for Google AI Pro and Ultra users. This is a useful companion signal to the earlier Gemini Spark summary note because it moves the product from concept into availability.

## Key Claims
- Gemini Spark is available globally.
- It is offered to Google AI Pro and Ultra users.
- The product is positioned as a 24/7 cloud agent.

## Evidence / Examples
- The bookmark text states the global rollout directly.
- The post's visible card supports the product-announcement framing.
- The note should be read as a rollout signal, not a deep architecture disclosure.

## Evidence Quality
- Source type: X post / product availability update
- Confidence: high for the rollout signal, medium for the agent-runtime interpretation
- Supports: [[../concepts/agent-autonomy.md]], [[../concepts/long-running-agents.md]], [[../concepts/managed-agents.md]], [[../concepts/coding-agents.md]]
- Main limitations: no engineering details are present in the snapshot
- Best use: evidence that always-o

### Yusuke Wada - Remote MCP server with Hono and TypeScript SDK v2

Source note: `wiki/sources/yusuke-wada-remote-mcp-server-hono-typescript-sdk-v2-x-2026-07-31.md`

# Yusuke Wada - Remote MCP server with Hono and TypeScript SDK v2

## Source Metadata
- Raw path: `../../raw/articles/yusuke-wada-remote-mcp-server-hono-typescript-sdk-v2-x-2026-07-31.md`
- Raw bookmark capture: `../../raw/x/bookmarks/bookmarks-20260801T0000Z.json`
- Original URL: https://x.com/i/status/2083146706326344182
- Linked X URL: https://twitter.com/ClaudeDevs/status/2082164248697069935
- Author: Yusuke Wada (@yusukebe)
- Posted: 2026-07-31T11:04:12.000Z
- Captured: 2026-08-01T00:00:22.073Z via xurl bookmarks capture
- Type: X post / technical implementation signal
- Evidence strength: bookmark snapshot metadata plus linked X reference to a ClaudeDevs example
- Public metrics at capture: 291 likes, 19 reposts, 3 replies, 2 quotes, 147 bookmarks, 31127 impressions

## Summary
This post is a compact implementation signal for remote MCP infrastructure. The useful part is not just that remote MCP exists, but that it can apparently be built with a lightweight web framework plus the TypeScript SDK v2.

## Key Claims
- Remote MCP servers can be implemented with Hono.
- The TypeScript SDK v2 includes the support needed for that path.
- A ClaudeDevs example is relevant enough to be linked from the bookmark.

## Evidence / Examples
- The bookmark text explicitly says remote MCP servers can be written this way.
- The post includes a photo/card and a direct cross-link to a ClaudeDevs tweet.
- The capture does not include a deeper walkthrough, so the note stays at the implementation-signal level.

## Evidence Quality
- Source type: X technical implementation signal
- Confidence: medium-high for the implementation claim, medium for the broader tooling implications
- Supports: [[../concepts/tool-accessibility.md]], [[../concepts/harness-engineering.md]], [[../concepts/coding-

### Claude - Lessons from building Claude Code: How we use skills

Source note: `wiki/sources/claude-lessons-from-building-claude-code-how-we-use-skills.md`

# Claude - Lessons from building Claude Code: How we use skills

## Source Metadata
- Raw path: `../../raw/articles/claude-lessons-from-building-claude-code-how-we-use-skills-2026-06-03.md`
- Original URL: https://claude.com/blog/lessons-from-building-claude-code-how-we-use-skills
- Author: Thariq Shihipar / Anthropic
- Published: 2026-06-03
- Captured: 2026-07-29
- Type: Claude blog / Claude Code practice article
- Evidence strength: high for Anthropic's internal skill taxonomy and practical skill-authoring guidance

## Summary
Anthropic's Claude Code team reports lessons from building and scaling hundreds of internal skills. The core contribution is a nine-category taxonomy of skill types, led by "Library and API reference," plus pragmatic advice for writing skills that add high-signal context rather than repeating what Claude already knows.

## Key Claims
- Skills are one of Claude Code's most-used extension points internally at Anthropic.
- Useful skills tend to fit cleanly into one skill type; overly broad skills that straddle several types can confuse the agent.
- Library/API reference skills are valuable because they explain correct library, CLI, or SDK usage and capture gotchas.
- Verification skills had the most measurable internal impact on Claude output quality.
- Good skills use gotchas sections, filesystem-based progressive disclosure, scripts, setup config, usage logging, and careful marketplace/distribution practices.

## Nine Skill Types
- Library and API reference
- Product verification
- Data fetching and analysis
- Business process and team automation
- Code scaffolding and templates
- Code quality and review
- CI/CD and deployment
- Runbooks
- Infrastructure operations

## Evidence Quality
- Source type: first-party Claude Code team practice article.

## 更新された概念・地図

### Environment Bootstrapping

KB note: `wiki/concepts/environment-bootstrapping.md`

---
aliases:
  - Environment Bootstrapping
  - Autoinstall
---

# Environment Bootstrapping

## Definition
The process of turning a fresh repository checkout into a runnable, testable, and often partially mocked environment that an agent can use for future coding or evaluation tasks.

## Why It Matters
Coding agents learn and operate through tools. If the environment is broken before the actual task starts, the agent spends context and compute debugging setup, and downstream tests or reward signals may become meaningless.

## Operational Pattern
- Inspect repository docs, Makefiles, package managers, common language tools, and available tests.
- Identify target commands whose successful execution would indicate a usable base environment.
- Install dependencies and create missing configuration.
- Mock external services or data when necessary, while recording what was mocked.
- Validate by running target commands and comparing outputs to expected behavior.
- Discard or retry environments

### Managed Agents

KB note: `wiki/concepts/managed-agents.md`

---
aliases:
  - Managed Agent
  - Managed Agents
---

# Managed Agents

## Definition
Hosted or product-managed agent runtimes that package model execution with tools, permissions, memory, tracing, sandboxing, and operational controls.

## Why It Matters
Managed agents turn agent operation into a deployable surface rather than a local prompt pattern. They make it easier to build roleful domain agents, but they also move important governance decisions into the runtime: what tools are exposed, how memory persists, what is sandboxed, and how humans inspect or intervene.

## Related Concepts
- [[multi-agent-orchestration.md]]
- [[agent-dreaming.md]]
- [[outcomes.md]]
- [[tool-accessibility.md]]
- [[agent-management.md]]
- [[agent-safety.md]]
- [[background-agents.md]]
- [[context-engineering.md]]

## Supporting Sources
- [[../sources/claudeai-claude-managed-agents-intro-x.md]]
- [[../sources/claude-new-in-managed-agents-dreaming-outcomes-orchestration.md]]
- [[../sources/oikon48-claude-ma

### Agent Harness Landscape

KB note: `wiki/maps/agent-harness-landscape.md`

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
- [[../sources/openai-chatgpt-memory-dreaming-x-2026-06

### Harness Engineering Vendor / Practitioner Comparison

KB note: `wiki/maps/harness-engineering-vendor-comparison.md`

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
- Focus: repository design, machine-enforced invariants, agent-recognizable contex

## NotebookLM Podcast用メモ

- まず今日の全体トレンドを話してから、重要ソースを3本に絞って深掘りする。
- ソース単体の紹介で終わらせず、既存KBの概念や地図がどう更新されたかを会話に含める。
- 最後に、明日以降の調査問いを2〜3個提示する。
