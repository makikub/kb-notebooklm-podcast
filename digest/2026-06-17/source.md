<!-- generated: 2026-06-17T13:02:08.661086+00:00 -->
<!-- kb_daily_digest_date: 2026-06-17 -->
# KB Daily Digest Source — 2026-06-17

このページは、knowledge-base-llm の日次更新を NotebookLM に読み込ませるための公開向けソースページです。
Discord通知よりも文脈を厚めに残し、Podcast化しやすいように、今日追加・更新されたソース、概念、地図を文章中心で整理します。

## 今日の全体像

# KB Daily Digest 2026-06-17

今日の knowledge-base-llm は、UTC 2026-06-17 に新規 ingest / compile がありました。確認できた主な追加は、X ブックマークの raw snapshot、Nick Dobos による Cursor Origin の source note、DevelopersIO による Open Knowledge Format 実践記事の raw/source note、そして OKF に合わせた concept / map / navigation の更新です。特に `open-knowledge-format`、`compiled-wiki`、`context-graph`、`okf-adoption-for-knowledge-base-llm`、`research-os-query-paths` が更新され、単なるソース追加ではなく、このKB自体の構造をどう標準化するかに踏み込んだ日でした。

全体トレンドは、「LLM向け知識ベースをMarkdownの私的な整理術で終わらせず、エージェントや別ツールが読める交換形式へ寄せる」ことです。Google Cloud の Open Knowledge Format は、Markdownファイル、YAML frontmatter、通常のMarkdownリンク、ディレクトリ構造を、LLM-wiki的な知識共有の最小共通形式として位置づけています。今日のKB更新では、その外部仕様を受けて、この `knowledge-base-llm` がすでにOKF的な形を持っている一方で、frontmatter や `type` フィールドの整備はまだ足りない、という現実的な採用判断が追加されました。

重要ソースの1本目は、**Google Cloud - Introducing the Open Knowledge Format** です。これは6月12日の一次ソースですが、今日のOKF compileの基準点になっています。OKFは、組織知がカタログ、Wiki、Drive、コードコメント、ノートブック、個人の経験に分散しているため、エージェントが十分な文脈を得られない、という問題設定から始まります。そこで、独自サービスやSDKではなく、Markdown中心の軽い束として知識を渡せる形式を提案している点が重要です。KBの文脈では、`compiled-wiki` と `context-graph` の中間に置ける「可搬な知識基盤」の候補として読めます。

重要ソースの2本目は、**DevelopersIO - Googleが公開したAIエージェント向け知識共有フォーマット『OKF』を触ってみた** です。一次ソースだけでは見えにくい実装上の摩擦がここで補われました。特に、v0.1のspecはbundle absoluteなMarkdownリンクを推奨している一方で、現時点のreference visualizerは `/` で始まるリンクをgraph edgeとして拾わず、relative linkへ変えるとedgeが出た、という検証結果は実務上かなり大きいです。OKFを採用するなら、spec準拠だけでなく「どのconsumerで何がedgeとして解釈されるか」を確認する必要があります。

重要ソースの3本目は、**Nick Dobos - Cursor Origin / agent-native git platform** です。これはOKFとは別系統の信号ですが、エージェント運用の基盤がエディタやチャットだけでなく、Git workflowそのものに広がっていることを示しています。Cursor Origin は「agent-native git platform」として予告され、関連投稿では単一repoで高頻度commitを扱うようなメッセージが出ています。証拠としてはXのteaserなので信頼度は中程度以下ですが、agentic Git work のcoordination layerという方向は、KB内の `agent-management`、`worker-based-composition`、`harness-engineering` の論点に接続できます。

今日の compile で一番実務的なのは、`wiki/maps/okf-adoption-for-knowledge-base-llm.md` が追加されたことです。結論は「repo-wide conversionではなく、新規・更新ノートからOKF v0.1 conventionsを段階採用する」です。現状スナップショットでは、`wiki/` 内のMarkdown 572件のうち、非予約concept documentが571件、YAML frontmatterありは85件、必須の `type` を持つものは0件、frontmatterなしは486件でした。つまり、このKBは構造としてはOKF的でも、形式としてはOKF conformantではありません。だからこそ、いきなり全変換せず、type vocabulary、checker、新規/変更分へのpilotから進める判断になっています。

`open-knowledge-format`、`compiled-wiki`、`context-graph` の概念ノートも、OKFを受けて更新されました。`compiled-wiki` では、OKFがMarkdown knowledge substrateの交換可能性を強める一方、provenance、freshness、confidence、permission のような高信頼運用に必要な意味論はまだ外側で補う必要がある、という緊張が追加されています。`context-graph` では、Markdown link graph は可搬なinterchange layerになり得るが、permission-aware / freshness-sensitive な実行にはtyped graph indexが必要になるかもしれない、という見方が強まりました。

もう一つの地図更新として、`wiki/maps/research-os-query-paths.md` に「Should this KB adopt OKF?」というQuery Pathが追加されました。これは、KBを単なるノート一覧ではなく、 recurring question を map、concept、source、writeback へルーティングする research OS として扱うための入口です。今後OKF採用を再検討するときは、Google Cloud一次ソース、DevelopersIO実践記事、Karpathy系のLLM wiki文脈を見て、採用判断、migration checklist、conformance snapshotへ落とす、という経路が明示されました。

実務上の示唆はかなりはっきりしています。OKFは「全部を重い知識グラフにする」話ではなく、既存のMarkdown KBに最小限のfrontmatterとリンク規約を足して、他のagentやvisualizerが読めるようにする話です。ただし、`type` だけで運用に足るわけではありません。source noteにはoriginal URL、raw path、evidence strength、limitations を残し、mapには判断理由と未解決問いを残す。このKBではすでにそれを本文でやっているので、次の課題は「どの情報をfrontmatterへ上げ、どれを本文に残すか」です。

Podcast化するなら、今日の回は「Markdown知識ベースが、いつ交換形式になるのか」を主題にするとよさそうです。前半でOKFの狙いを紹介し、中盤でDevelopersIOのvisualizer検証を使って、specとtoolingのズレを現場目線で話す。後半でこのKB自身の採用メモを取り上げ、572件のノートを一括変換する誘惑を避け、新規・変更ノートからpilotし、checkerを入れてから広げる、という現実的な移行論に落とすと聞きやすいはずです。最後にCursor Originを短く添えると、知識形式だけでなく、Gitやagent coordination layerも「agent-native」へ寄っているという広いトレンドが見えます。

## 重要ソース3本

- `wiki/sources/google-cloud-open-knowledge-format.md`
- `wiki/sources/classmethod-open-knowledge-format-okf-v01-guide.md`
- `wiki/sources/nick-dobos-cursor-origin-agent-native-git-platform-x-2026-06-16.md`

## 追加・更新された主なKBノート

- `wiki/sources/classmethod-open-knowledge-format-okf-v01-guide.md`
- `wiki/sources/nick-dobos-cursor-origin-agent-native-git-platform-x-2026-06-16.md`
- `wiki/concepts/open-knowledge-format.md`
- `wiki/concepts/compiled-wiki.md`
- `wiki/concepts/context-graph.md`
- `wiki/maps/okf-adoption-for-knowledge-base-llm.md`
- `wiki/maps/research-os-query-paths.md`
- `wiki/navigation/memory.md`


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

### DevelopersIO - Googleが公開したAIエージェント向け知識共有フォーマット『OKF』を触ってみた

Source note: `wiki/sources/classmethod-open-knowledge-format-okf-v01-guide.md`

# DevelopersIO - Googleが公開したAIエージェント向け知識共有フォーマット『OKF』を触ってみた

## Source metadata
- Raw path: raw/articles/classmethod-open-knowledge-format-okf-v01-guide-2026-06-16.md
- Original URL: https://dev.classmethod.jp/articles/open-knowledge-format-okf-v01-guide/
- Published: 2026-06-16
- Author: せーの
- Publisher: DevelopersIO / Classmethod
- Type: practitioner hands-on article / secondary explanation
- Evidence strength: medium-high for observed OKF visualizer behavior and migration ergonomics; secondary for OKF design intent

## Summary
This DevelopersIO article turns Google Cloud's OKF v0.1 announcement into a practical walkthrough: it explains the minimal Markdown/YAML-frontmatter bundle model, hand-builds a small OKF bundle, runs the bundled static visualizer, and checks how close an existing Obsidian vault is to OKF compliance. Its most useful contribution is the implementation note that the v0.1 visualizer skips absolute Markdown links even though the spec recommends them, so relative links are currently needed to get graph edges.

## Key claims
- OKF is best understood as a formalization of LLM-wiki style practice already seen in Obsidian vaults, `CLAUDE.md`, `AGENTS.md`, repo-local `index.md`, and Markdown link graphs.
- OKF's minimal required schema makes incremental migration realistic: adding `type` to existing frontmatter can make many Markdown notes compliant.
- OKF and MCP are complementary rather than competitive: OKF packages static curated knowledge, while MCP provides live tool/API access.
- The reference tooling is still immature: the spec recommends absolute-path links, but the visualizer currently ignores `/`-prefixed links when generating edges.
- The format itself is not GCP-bound, even though the reference enrichment agent is BigQuery/Gemini-oriented.

#

### Nick Dobos - Cursor Origin / agent-native git platform

Source note: `wiki/sources/nick-dobos-cursor-origin-agent-native-git-platform-x-2026-06-16.md`

# Nick Dobos - Cursor Origin / agent-native git platform

## Source Metadata
- Raw path: [[../../raw/articles/nick-dobos-cursor-origin-agent-native-git-platform-x-2026-06-16.md]]
- Canonical URL: https://x.com/i/status/2066927803610857592
- Related bookmarked post: https://x.com/i/status/2066928460069765381
- Author: Nick Dobos (@NickADobos)
- Posted: 2026-06-16T16:56:04.000Z
- Captured: 2026-06-17 via xurl bookmarks capture
- Type: X image post / product teaser
- Evidence strength: bookmark snapshot metadata plus image-card text; the image itself is not decoded here
- Public metrics at capture: 8 reposts, 9 replies, 341 likes, 23 quotes, 47 bookmarks, 244828 impressions

## Summary
The post frames Cursor Origin as an agent-native git platform. A related bookmark from the same author claims it supports 22.6 commits per second in a single repo, which suggests the product is being positioned as a high-throughput coordination layer for agentic Git work rather than a conventional source-control UI.

## Key Claims
- Cursor Origin is being pitched as an agent-native git platform.
- The product is being framed as a competitor to GitHub.
- The demo/follow-up claim emphasizes very high commit throughput in a single repo.
- The signal is about Git workflow orchestration for agents, not just code editing.

## Evidence / Examples
- The captured text says `Cursor origin` and `Agent native git platform`.
- A second captured post from the same author adds the throughput claim.

## Evidence Quality
- Source type: X image post plus follow-up post
- Confidence: medium for the existence of the product teaser, low to medium for the performance claim
- Limitations: the bookmark payload does not expose the image contents or any benchmark methodology

## Related Concepts
- [[../concepts/codin

## 更新された概念・地図

### Map Notes

KB note: `wiki/maps/README.md`

# Map Notes

Map notes connect multiple concepts and sources.

Examples:
- landscape overviews
- comparison notes
- timelines
- architecture maps
- taxonomy notes
- control vocabularies and cross-source synthesis notes
- deployment-gate and operational-risk notes that connect repo controls to production safety
- evidence-quality and source-trust notes that rank claim support
- query-path notes that route recurring user questions through stable map/concept/source paths
- navigation-support notes that help `wiki/navigation/` expose corpus shape before source-level lookup
- approval-pattern and escalation maps that connect autonomy settings to review burden

## Current maps

- [Context Graph and Company Brain](context-graph-and-company-brain.md)
- [Agent Onboarding with Domain KB + Codebase](agent-onboarding-kb-codebase.md)
- [Context Management Decision Map](context-management-decisions.md)
- [Agent Harness Landscape](agent-harness-landscape.md)
- [Agent Deployment Gates and Operational 

### OKF Adoption for knowledge-base-llm

KB note: `wiki/maps/okf-adoption-for-knowledge-base-llm.md`

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
- O

### Research OS Query Paths

KB note: `wiki/maps/research-os-query-paths.md`

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
- Concepts: [[../concepts/harness-engineering.md]]

### Navigation: Memory / Knowledge Substrate

KB note: `wiki/navigation/memory.md`

# Navigation: Memory / Knowledge Substrate

## Use When
The question is about agent memory, knowledge bases, compiled notes, context graphs, team/company brains, or retrieval architecture.

## Start Maps
- [[../maps/context-graph-and-company-brain.md]]
- [[../maps/research-os-query-paths.md]]
- [[../maps/agent-onboarding-kb-codebase.md]]
- [[../maps/okf-adoption-for-knowledge-base-llm.md]]

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
- [[../concepts/navigable

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
- [[../sour

## NotebookLM Podcast用メモ

- まず今日の全体トレンドを話してから、重要ソースを3本に絞って深掘りする。
- ソース単体の紹介で終わらせず、既存KBの概念や地図がどう更新されたかを会話に含める。
- 最後に、明日以降の調査問いを2〜3個提示する。
