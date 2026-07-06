<!-- generated: 2026-07-06T13:02:06.175303+00:00 -->
<!-- kb_daily_digest_date: 2026-07-06 -->
# KB Daily Digest Source — 2026-07-06

このページは、knowledge-base-llm の日次更新を NotebookLM に読み込ませるための公開向けソースページです。
Discord通知よりも文脈を厚めに残し、Podcast化しやすいように、今日追加・更新されたソース、概念、地図を文章中心で整理します。

## 今日の全体像

# KB Daily Digest 2026-07-06

2026-07-06 UTC の knowledge-base-llm には、X bookmarks 由来の新規 ingest が 3本入りました。今回の中心は、自己改善型 agentic systems の段階的な作り方、Google Drive 等における機密情報の扱い、Claude Code の compact 問題と対策です。wiki 側では `loop-engineering`、`agent-safety`、`context-resets`、`agent-harness-landscape` が更新され、ハーネス設計の地図に「ループをどう育てるか」「秘密をどこに置くか」「長時間セッションをどう回復するか」という実務寄りの論点が加わりました。

重要ソースの 1本目は、Movez / @0xMovez による Anthropic workshops on self-improving agentic systems の共有です。捕捉された内容はワークショップ本編ではなくタイムテーブル中心ですが、基本 agent、memory、autonomy、proactive agent、self-improving agents へ進む順序が明示されています。KB ではこのソースを `loop-engineering` と `agent-harness-landscape` に接続し、自己改善を単発の魔法ではなく、記憶、実行、能動性、改善ループを段階的に積む maturity ladder として扱っています。

この追加によって `loop-engineering` の論点は少し締まりました。特に「self-improving agent system」という言葉を、モデル内部が勝手に継続学習する話と混同せず、trace-driven improvement、routine / skill の更新、評価ループ、再実行可能な harness artifact の改善として分解する必要があります。今回のソースは、本編詳細までは未取得ながら、memory を autonomy の前段に置き、その後に proactive behavior と self-improvement を置く順番自体が強い設計シグナルです。

重要ソースの 2本目は、ryoppippi / @ryoppippi による「機密情報を Google Drive 等にアップロードするのはよいのか？」という記事共有です。捕捉できているのは X 投稿と記事タイトルカードで、本文の細部までは KB に入っていません。ただし投稿者の要約は「要はバランス」であり、KB ではこれを `agent-safety`、`approval-policy`、`environment-bootstrapping`、`evidence-quality` に接続しました。

このソースの意味は、エージェント運用における安全性が prompt guardrail だけでは終わらない点にあります。LLM に渡す前のファイル置き場、共有ドライブ、アクセス制御、redaction、チーム内の運用規律が、そのまま agent safety の一部になります。今回の digest では詳細な法務・セキュリティ判断までは踏み込みませんが、「便利だから共有ドライブに置く」でも「機密だから全部禁止」でもなく、データ分類、権限、監査性、モデル入力までの経路で判断する必要がある、という方向づけが加わりました。

重要ソースの 3本目は、Yuichi Uemura / @u1 による Claude Code compact の問題点と対策に関する記事カードです。こちらはタイトルのみの capture なので、KB の source note も保守的です。それでも、Claude Code の compact が単なる便利機能ではなく、失敗モードと対策を持つ運用論点として扱われ始めていることは重要です。

`context-resets` には、このソースをきっかけに「compact が信用できなくなった時に reset を強制する信号は何か」という open question が追加されています。長時間セッションでは、compaction は低コストな継続手段ですが、誤った理解やノイズを圧縮して残す危険があります。対して reset は明示的な handoff artifact を必要とするため面倒ですが、状態を再構築することで drift を減らせます。今回の更新は、compaction vs reset を単なる好みではなく、harness の recovery policy として考える流れを強めています。

全体トレンドとしては、今回の 3本はいずれも「agent を賢くする」話を、モデル性能ではなく周辺の運用面へ引き戻しています。自己改善には loop と memory が必要で、機密情報の扱いには共有基盤と承認ポリシーが必要で、compact の失敗には reset / handoff / verification が必要です。つまり KB の agent harness landscape は、ツール連携や multi-agent 構成だけでなく、情報管理、復旧戦略、改善サイクルまで含む運用 OS のような方向へ広がっています。

Podcast で掘るなら、論点は 3つあります。第一に、self-improving agent を語る時に「何が改善されるのか」を model、memory、prompt、routine、skill、eval、runner に分解すること。第二に、LLM エージェント時代の機密データ管理では、Google Drive のような汎用共有基盤をどう分類・監査・制限するか。第三に、Claude Code や類似 coding agent の長時間作業で、compact、rewind、reset、handoff の使い分けをどうルール化するかです。

## Sources

- `wiki/sources/movez-anthropic-workshops-self-improving-agentic-systems-x-2026-07-05.md`
- `wiki/sources/ryoppippi-google-drive-secrets-balance-article-share-x-2026-07-05.md`
- `wiki/sources/u1-claude-code-compact-problems-countermeasures-x-2026-07-04.md`

## Updated KB Areas

- `wiki/concepts/loop-engineering.md`
- `wiki/concepts/agent-safety.md`
- `wiki/concepts/context-resets.md`
- `wiki/maps/agent-harness-landscape.md`


## 重要ソース

### Movez - Anthropic workshops on self-improving agentic systems

Source note: `wiki/sources/movez-anthropic-workshops-self-improving-agentic-systems-x-2026-07-05.md`

# Movez - Anthropic workshops on self-improving agentic systems

## Source Metadata
- Raw path: `raw/articles/movez-anthropic-workshops-self-improving-agentic-systems-x-2026-07-05.md`
- Raw bookmark capture: `raw/x/bookmarks/bookmarks-20260706T0000Z.json`
- Original URL: https://x.com/i/status/2073765125958348964
- Primary URL: https://x.com/0xMovez/status/2073765125958348964/video/1
- Secondary URL: https://x.com/0xCodez/status/2065089060104720776
- Author: Movez (@0xMovez)
- Posted: 2026-07-05T13:45:09.000Z
- Captured: 2026-07-06 via xurl bookmarks capture
- Type: X post / workshop share
- Evidence strength: bookmark snapshot metadata plus workshop timetable text and teaser links
- Public metrics at capture: 67 reposts, 35 replies, 449 likes, 0 quotes, 904 bookmarks, 70148 impressions

## Summary
Anthropic's workshop share turns self-improving agent design into a staged curriculum: ship the first agent, add memory, increase autonomy, set up proactive behavior, then close the loop on self-improvement. The value here is not a single product claim but the visible decomposition of agent maturity into teachable steps.

## Key Claims
- Anthropic is packaging agent-building as a workshop sequence.
- Memory is treated as a separate step from basic agent operation.
- Autonomy and proactive behavior come after the initial agent and memory layers.
- Self-improvement is presented as the final stage in the sequence.

## Evidence / Examples
- The post literally lists five workshop segments and timestamps.
- The final segment is named "self-improving agents."
- The share includes both a video teaser and a linked related post.

## Evidence Quality
- Source type: X post / workshop share
- Confidence: high for the existence of the workshop sequence and the staged framing
- Supports: lo

### ryoppippi - Google Drive secret-handling article share

Source note: `wiki/sources/ryoppippi-google-drive-secrets-balance-article-share-x-2026-07-05.md`

# ryoppippi - Google Drive secret-handling article share

## Source Metadata
- Raw path: `raw/articles/ryoppippi-google-drive-secrets-balance-article-share-x-2026-07-05.md`
- Raw bookmark capture: `raw/x/bookmarks/bookmarks-20260706T0000Z.json`
- Original URL: https://x.com/i/status/2073822628360409420
- Primary URL: https://ryozi.hatenadiary.jp/entry/2026/05/05/124807
- Author: ryoppippi (@ryoppippi)
- Posted: 2026-07-05T17:33:39.000Z
- Captured: 2026-07-06 via xurl bookmarks capture
- Type: X post / article share
- Evidence strength: bookmark snapshot metadata plus article title card
- Public metrics at capture: 1 reposts, 0 replies, 134 likes, 0 quotes, 101 bookmarks, 12627 impressions

## Summary
This bookmark points to an article about whether confidential information should be uploaded to Google Drive. The post's useful signal is that the answer is treated as a tradeoff problem: data sensitivity, convenience, and operational discipline all matter at once.

## Key Claims
- Confidential data handling is not a simple yes/no rule.
- The underlying decision depends on how sensitive the information is and how it will be governed.
- The linked article is meant to provide a detailed, practical explanation rather than a slogan.

## Evidence / Examples
- The tweet explicitly says the linked article is detailed and helpful.
- The article title asks whether it is okay to upload confidential information to Google Drive.
- The post's own summary says "it's a balance."

## Evidence Quality
- Source type: X post / article share
- Confidence: medium for the broad tradeoff framing, low for any finer-grained policy until the article is read directly
- Supports: agent-safety, approval-policy, environment-bootstrapping, evidence-quality
- Main limitations: the bookmark capture does no

### Yuichi Uemura - Claude Code compaction problems and countermeasures

Source note: `wiki/sources/u1-claude-code-compact-problems-countermeasures-x-2026-07-04.md`

# Yuichi Uemura - Claude Code compaction problems and countermeasures

## Source Metadata
- Raw path: `raw/articles/u1-claude-code-compact-problems-countermeasures-x-2026-07-04.md`
- Raw bookmark capture: `raw/x/bookmarks/bookmarks-20260706T0000Z.json`
- Original URL: https://x.com/i/status/2073289543948923153
- Primary URL: https://x.com/i/article/2073286645626060800
- Author: Yuichi Uemura (@u1)
- Posted: 2026-07-04T06:15:21.000Z
- Captured: 2026-07-06 via xurl bookmarks capture
- Type: X post / article card
- Evidence strength: bookmark snapshot metadata plus article title only
- Public metrics at capture: 176 reposts, 10 replies, 1568 likes, 75 quotes, 3241 bookmarks, 680074 impressions

## Summary
The capture only exposes the article title, but that title is still useful: it points directly at a compaction failure-mode discussion for Claude Code. The most conservative read is that the linked article covers what goes wrong during compact and what to do about it.

## Key Claims
- Claude Code compaction has recognizable failure modes.
- There are practical countermeasures worth documenting.
- The topic is important enough to merit a standalone article card.

## Evidence / Examples
- The bookmark title names both the problem and the response: "compact" problems and countermeasures.
- No body text was captured, so the note should avoid guessing the specific advice.

## Evidence Quality
- Source type: X post / article card
- Confidence: low for specifics, medium for the existence of a compaction-focused article and its general topic
- Supports: context-resets, context-engineering, feedback-controls, self-verification
- Main limitations: title-only capture
- Best use: a pointer into the KB's compaction/reset cluster when discussing long-session recovery

## Related Concep

## 更新された概念・地図

### Agent Safety

KB note: `wiki/concepts/agent-safety.md`

---
aliases:
  - Agent Safety
---

# Agent Safety

## Definition
The set of mechanisms and design choices used to keep an agent helpful, bounded, and resistant to harmful or misaligned behavior.

## Why It Matters
As agents gain tools and autonomy, safety becomes an architectural concern rather than just a prompt concern.

## Related Concepts
- [[behavioral stability]]
- [[approval policy]]
- [[human-in-the-loop]]
- [[failure modes]]
- [[middleware-controls]]

## Supporting Sources
- [[../sources/newspicks-harness-engineering-what-is-it.md]]
- [[../sources/anthropic-emotion-concepts.md]]
- [[../sources/anthropic-claude-code-auto-mode.md]]
- [[../sources/anthropic-claude-code-web-scheduled-tasks-docs.md]]
- [[../sources/anthropic-claude-code-on-the-web-docs.md]]
- [[../sources/anthropic-claude-mythos-preview.md]]
- [[../sources/spillwave-ai-coding-hangover-harness-engineering.md]]
- [[../sources/openclaw-release-v2026-4-11-github.md]]
- [[../sources/keisuke69-ai-agent-security-enterpris

### Context Resets

KB note: `wiki/concepts/context-resets.md`

---
aliases:
  - Context Resets
---

# Context Resets

## Definition
A harness strategy where a new agent session starts from a clean context window and reconstructs state from explicit handoff artifacts rather than compressed conversation memory.

## Why It Matters
Resets can reduce context drift and force higher-quality handoffs, especially on long tasks. In the current source set, they function less like a universal best practice and more like a reliability tactic that becomes valuable when session history turns noisy or self-reinforcing.

## Related Concepts
- [[structured-handoff-artifacts]]
- [[long-running-agents]]
- [[self-evaluation-bias]]

## Supporting Sources
- [[../sources/anthropic-harness-design-long-running-apps.md]]
- [[../sources/anthropic-effective-harnesses-long-running-agents.md]]
- [[../sources/trq212-claude-code-usage-context-management-x.md]]
- [[../sources/walden-yan-multi-agent-pragmatic-update-x.md]]
- [[../sources/anthropic-april-23-postmortem-claude-code-qu

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

## NotebookLM Podcast用メモ

- まず今日の全体トレンドを話してから、重要ソースを3本に絞って深掘りする。
- ソース単体の紹介で終わらせず、既存KBの概念や地図がどう更新されたかを会話に含める。
- 最後に、明日以降の調査問いを2〜3個提示する。
