<!-- generated: 2026-06-04T13:01:19.910336+00:00 -->
<!-- kb_daily_digest_date: 2026-06-04 -->
# KB Daily Digest Source — 2026-06-04

このページは、knowledge-base-llm の日次更新を NotebookLM に読み込ませるための公開向けソースページです。
Discord通知よりも文脈を厚めに残し、Podcast化しやすいように、今日追加・更新されたソース、概念、地図を文章中心で整理します。

## 今日の全体像

# KB Daily Digest - 2026-06-04

今日の knowledge-base-llm は、UTC 2026-06-04 の `kb: ingest daily x bookmarks` により、Xブックマーク由来の新規ソース3本と、それに対応する `wiki/sources` 3本、さらに `wiki/maps/agent-harness-landscape.md` の更新が入りました。大きな流れとしては、エージェントやAI支援の価値が「モデル単体」ではなく、作業者が普段いる場所に文脈、出力、レビュー、配布、委任をどう接続するかに移っている、という読み筋です。

重要ソース1本目は、Loredana Crisan による Figma Make の投稿です。Figma Make が production codebase と接続し、視覚的にソフトウェアを編集したあと、Figmaを離れずに branch、commit、PR まで進められる、という内容でした。KB内では、これは `tool-accessibility` や `rich-agent-output-artifact` の話に直結します。つまり、AIが生成したものを別の開発環境へ持ち出して処理するのではなく、視覚編集、レビュー、git操作までが同じワークフロー面に寄ってくる兆候です。

重要ソース2本目は、Nick Baumann の Codex運用メモです。彼は Codex を単発チャットではなく、ひとつの永続的な「chief of staff」スレッドとして扱い、その親スレッドから新しいプロジェクトやワークストリーム用のスレッドを立ち上げる、と説明しています。ここで面白いのは、賢い回答そのものよりも、文脈を保持した親スレッドが作業の起点になっている点です。KBの `agent-harness-landscape` では、これが continuity across sessions、thread-spawning、agent management の実例として位置づけられました。

重要ソース3本目は、Goodpatch の土屋尚史さんによる社内HTML共有サービスの投稿です。社内でHTMLを共有する機会が増えたため、公開範囲を柔軟に設定でき、Slack共有や esa / Notion への埋め込みがしやすいサービスを作った、という内容です。これは一見するとAIエージェントから少し離れた社内ツールの話ですが、KB上ではかなり重要です。なぜなら、エージェント時代の成果物はMarkdownやコードだけでなく、HTMLのようなリッチで配布しやすい成果物として共有されることが増えるからです。

今日の3本をまとめると、トレンドは「作る場所」「指示する場所」「成果物を見る場所」「共有する場所」が再編されている、ということです。Figmaは視覚編集からPRまでをつなぎ、Codexの永続スレッドは複数ワークストリームの文脈ルーターになり、GoodpatchのHTML共有サービスは成果物を社内の既存ツールへ埋め込める配布面にしています。どれも、AI活用をプロンプト技術だけでなく、作業面の設計問題として捉える材料になります。

`agent-harness-landscape.md` の更新では、OpenAI / Codex の項目に「persistent chief-of-staff threads and thread-spawning as a continuity primitive」が追加され、Figma / Claude Design / workflow surfaces の項目に Figma Make の branch / commit / PR 操作が追記されました。また、GoodpatchのHTML共有は `rich-agent-output-artifact`、`structured-handoff-artifacts`、`context-first-development` と結びつき、成果物を人やチームが扱いやすい形にする層として読めるようになっています。

実務上の示唆は、エージェント導入の評価軸を「どのモデルを使うか」だけに置かないことです。むしろ、永続スレッドをどこで管理するか、生成物をどうレビュー可能にするか、HTMLやPRや埋め込みのような成果物をどう権限管理つきで流通させるか、という周辺設計が差を作ります。今日の更新は、AI支援が個人の作業効率だけでなく、チームのハンドオフ、レビュー、共有の設計へ広がっていることを示しています。

Podcastで掘るなら、論点は3つあります。第一に、Figmaのような視覚UIがどこまでgitやCIの責務を吸収すべきか。第二に、永続的な親スレッドはいつ便利で、いつリセットや分割が必要になるのか。第三に、HTMLのようなリッチ成果物を社内で配るとき、利便性と権限管理の境界をどう設計するかです。今日の更新は小粒な3本ですが、エージェント・ハーネスの地図を「モデルの外側にある作業環境の設計」へさらに押し広げる内容でした。

## Important Sources

- Loredana Crisan / Figma Make on a production codebase: https://x.com/loredanacrisan/status/2060019763548705183
- Nick Baumann / Codex as a persistent chief-of-staff thread: https://x.com/nickbaumann_/status/2060480729830789376
- 土屋尚史 / Goodpatch internal HTML sharing service: https://x.com/tsuchinao83/status/2062074868406084007

## Changed KB Notes

- `wiki/sources/loredanacrisan-figma-make-production-codebase-x-2026-05-28.md`
- `wiki/sources/nickbaumann-codex-chief-of-staff-thread-x-2026-05-29.md`
- `wiki/sources/tsuchinao83-goodpatch-internal-html-sharing-service-x-2026-06-03.md`
- `wiki/maps/agent-harness-landscape.md`


## 重要ソース

### Loredana Crisan - Figma Make on a production codebase

Source note: `wiki/sources/loredanacrisan-figma-make-production-codebase-x-2026-05-28.md`

# Loredana Crisan - Figma Make on a production codebase

## Source Metadata
- Source type: X bookmark snapshot
- X post: https://x.com/loredanacrisan/status/2060019763548705183
- Linked video card: https://x.com/loredanacrisan/status/2060019763548705183/video/1
- Author: Loredana Crisan (@loredanacrisan)
- Tweet created: 2026-05-28T15:25:59.000Z
- Captured: 2026-06-04 via xurl bookmarks capture
- Evidence strength: bookmark snapshot metadata plus linked video card
- Public metrics at capture: 10 reposts, 9 replies, 263 likes, 2 quotes, 73 bookmarks, 17530 impressions
- Raw path: [[../../raw/articles/loredanacrisan-figma-make-production-codebase-x-2026-05-28.md]]

## Linked URLs
- https://x.com/loredanacrisan/status/2060019763548705183
- https://x.com/loredanacrisan/status/2060019763548705183/video/1

## Bookmark text
> Figma Make now works with your production codebase: edit software visually, then branch, commit, and open PRs, without leaving Figma or touching a terminal.
>
> We believe the future of building is visual-first and collaborative by default. We're just getting started.

## What it says
Figma is presenting Make as a production-capable visual surface, not just a design sandbox. The key detail is that the visual editor now spans into branching, commits, and PRs.

## Why it matters
This moves the harness boundary upward into the product UI itself. It is an example of tool accessibility and rich output surfaces becoming part of the main workflow instead of an afterthought.

## Related concepts
- [[../concepts/tool-accessibility.md]]
- [[../concepts/rich-agent-output-artifact.md]]
- [[../concepts/managed-agents.md]]
- [[../concepts/product-responsibility-distribution.md]]

## Related Maps
- [[../maps/agent-harness-landscape.md]]
- [[../maps/harness-engineering-v

### Nick Baumann - Codex as a persistent chief-of-staff thread

Source note: `wiki/sources/nickbaumann-codex-chief-of-staff-thread-x-2026-05-29.md`

# Nick Baumann - Codex as a persistent chief-of-staff thread

## Source Metadata
- Source type: X bookmark snapshot
- X post: https://x.com/nickbaumann_/status/2060480729830789376
- Secondary X source: https://twitter.com/guinnesschen/status/2060464235868836235
- Author: Nick Baumann (@nickbaumann_)
- Tweet created: 2026-05-29T21:57:42.000Z
- Captured: 2026-06-04 via xurl bookmarks capture
- Evidence strength: bookmark snapshot metadata plus linked X source
- Public metrics at capture: 114 reposts, 95 replies, 2501 likes, 20 quotes, 3712 bookmarks, 356960 impressions
- Raw path: [[../../raw/articles/nickbaumann-codex-chief-of-staff-thread-x-2026-05-29.md]]

## Linked URLs
- https://x.com/nickbaumann_/status/2060480729830789376
- https://twitter.com/guinnesschen/status/2060464235868836235

## Bookmark text
> This has fundamentally changed how I use Codex
>
> - everything runs out of a single persistent thread (my "chief of staff")
> - anytime I start a new project or workstream, I have that thread spin up a new thread (because it's already found the context from slack, etc)

## What it says
Codex is being used as a durable operator surface: one persistent thread accumulates context, then becomes the launcher for new work threads instead of forcing the user to re-orient from scratch.

## Why it matters
This is a concrete example of continuity as a harness feature. The value is not just the model output; it is the ability to preserve context, reuse it, and delegate from a stable parent thread.

## Related concepts
- [[../concepts/agent-captain.md]]
- [[../concepts/agent-management.md]]
- [[../concepts/background-agents.md]]
- [[../concepts/long-running-agents.md]]
- [[../concepts/context-first-development.md]]

## Related Maps
- [[../maps/agent-harness-landscape.md]]
- [[.

### 土屋尚史 / Goodpatch - internal HTML sharing service

Source note: `wiki/sources/tsuchinao83-goodpatch-internal-html-sharing-service-x-2026-06-03.md`

# 土屋尚史 / Goodpatch - internal HTML sharing service

## Source Metadata
- Source type: X bookmark snapshot
- X post: https://x.com/tsuchinao83/status/2062074868406084007
- Linked image card: https://x.com/tsuchinao83/status/2062074868406084007/photo/1
- Author: 土屋尚史 / Goodpatch (@tsuchinao83)
- Tweet created: 2026-06-03T07:32:14.000Z
- Captured: 2026-06-04 via xurl bookmarks capture
- Evidence strength: bookmark snapshot metadata plus linked image card
- Public metrics at capture: 58 reposts, 5 replies, 854 likes, 30 quotes, 687 bookmarks, 150935 impressions
- Raw path: [[../../raw/articles/tsuchinao83-goodpatch-internal-html-sharing-service-x-2026-06-03.md]]

## Linked URLs
- https://x.com/tsuchinao83/status/2062074868406084007
- https://x.com/tsuchinao83/status/2062074868406084007/photo/1

## Bookmark text
> 最近、社内でHTMLで共有する事が多くなってきたので、空き時間にサクッと社内でHTMLを共有するサービスを作った。公開範囲を柔軟に設定できたり、Slackで簡単に共有できたり、esaやNotionに埋め込みで貼り付けれたり、かゆいところに手が届く感じで非常に便利。
>
> Goodpatch社内のみです。

## What it says
Goodpatch is using HTML as a lightweight internal artifact format and built a service around sharing it with controlled visibility and convenient distribution paths.

## Why it matters
This is a useful example of artifact-first internal workflows. The output format itself becomes the collaboration surface, especially when it can be embedded into other tools employees already use.

## Related concepts
- [[../concepts/rich-agent-output-artifact.md]]
- [[../concepts/context-first-development.md]]
- [[../concepts/tool-accessibility.md]]
- [[../concepts/structured-handoff-artifacts.md]]

## Related Maps
- [[../maps/agent-harness-landscape.md]]
- [[../maps/context-management-decisions.md]]
- [[../maps/coding-agent-harness-patterns.md]]

## Open questions
- Which internal artifacts should be HTML, and wh

## 更新された概念・地図

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

## NotebookLM Podcast用メモ

- まず今日の全体トレンドを話してから、重要ソースを3本に絞って深掘りする。
- ソース単体の紹介で終わらせず、既存KBの概念や地図がどう更新されたかを会話に含める。
- 最後に、明日以降の調査問いを2〜3個提示する。
