<!-- generated: 2026-06-16T13:02:31.597150+00:00 -->
<!-- kb_daily_digest_date: 2026-06-16 -->
# KB Daily Digest Source — 2026-06-16

このページは、knowledge-base-llm の日次更新を NotebookLM に読み込ませるための公開向けソースページです。
Discord通知よりも文脈を厚めに残し、Podcast化しやすいように、今日追加・更新されたソース、概念、地図を文章中心で整理します。

## 今日の全体像

# KB Daily Digest 2026-06-16

今日の knowledge-base-llm は、UTC 2026-06-16 に X ブックマーク由来の ingest が 1 コミット入り、raw 記録 4 件、wiki/source ノート 4 件が追加されました。大きな compile 更新や concept/map 本体の直接更新はなく、今回も source 層の追加が中心です。ただし、昨日に続いて「エージェントを一回きりの応答装置ではなく、目標、監督、検証、探索面を持つ運用システムとして扱う」という流れがはっきりしています。

全体トレンドは、AI エージェントの実務利用が「人間が逐次確認する HITL」から、「人間がループ全体を監督し、必要な箇所だけ介入する HOTL」へ少しずつ重心を移していることです。スナガクさんの HOTL / Human on the Loop は、その方向をもっとも短く表したソースです。確認を毎段階に挟むと、品質保証のつもりがワークフロー全体の停止点になりやすい。今日追加された他のソースも、Claude Code の反復ループ、Codex の `/goal`、Twitter Atlas の関係グラフという形で、「人間がどこを見るべきか」「エージェントにどこまで走らせるか」を考える材料になっています。

重要ソースの1本目は、**スナガク — HOTL / Human on the Loop** です。ここでの読みどころは、HITL を否定するというより、確認の置き場所を再設計している点です。人間が全工程のゲートになると、AI は自律的に完了へ進めません。一方で、人間を完全に外すと、 silent failure や意図のズレが見逃されます。KB の文脈では、`approval-policy`、`agent-autonomy`、`long-running-agents` をつなぐ実務的な論点であり、「どのステップを自動化し、どの判断を人間に残すか」を決めるための短いラベルとして使えます。

重要ソースの2本目は、**0xMorty — The 9-Step Loop That Turns Claude Code Into a Senior Engineer** です。取得できているのは X article card のタイトル中心で、9ステップの本文はまだ KB 内では検証できません。それでも、タイトルが示す方向は重要です。Claude Code を単なるプロンプト入力先ではなく、シニアエンジニア的な振る舞いに近づけるための反復プロセスとして扱っているからです。これは `loop-engineering`、`self-verification`、`coding-agent-harness-patterns` の周辺に置ける信号で、今後本文が取得できれば、どのステップが harness 側の設計で、どのステップが repo や skill 側の設計なのかを分けて整理したいところです。

重要ソースの3本目は、**Tibo — Codex can see and set its own /goal** です。Codex が `/goal` を見て、自分で設定できるという話は、エージェントの制御面が「外から与えられるタスク」だけではなく、「意図を読んで自分の作業境界を作る面」へ広がっていることを示しています。これは便利な一方で、境界設定がズレると、 agent が自信を持って間違った目的へ進むリスクもあります。KB では `agent-autonomy` や `goal-driven execution` の議論に戻し、「自己目標設定を許すなら、どんな制約、ログ、レビュー面が必要か」を考える材料になります。

4本目の **tiago — Twitter Atlas** は、今日の流れの中では少し異なる入口です。Twitter Atlas は、アカウント同士の会話や近さを空間的なマップとして見せるプロダクト launch card で、ソーシャルネットワークを平たいリストではなく、隣接関係とクラスターで理解する発想を示しています。KB の `context-graph`、`compiled-wiki`、`research-os-query-paths` と相性がよく、エージェント運用でも「次に読むべき近傍」「判断に関係する隣接概念」「人間が監督すべきクラスタ」をどう見せるかという UI / 知識地図の話につながります。

今回の source 追加によって、KB の地図上では `loop-engineering`、`agent-autonomy`、`approval-policy`、`context-graph` の周辺が少し濃くなりました。concept/map 本体は今日は更新されていませんが、次に compile するなら、HOTL と goal 自己設定を同じ地図に置き、エージェントを走らせる自由度と、人間が観測・介入する面の関係を整理するとよさそうです。Claude Code の 9-step loop はプロセス側、Codex の `/goal` は制御面、Twitter Atlas は観測面の比喩として、それぞれ別の角度から同じ問題を照らしています。

実務上の読みどころは、「自動化を強めるほど、人間の役割が消える」のではなく、「人間の役割を細かい確認者から、ループ設計者、例外処理者、観測面の編集者へ移す必要がある」という点です。毎回の approve / reject ではなく、どこでエージェントが自分の目標を確認し、どこで検証し、どこで人間に戻すかを設計できるチームほど、長いタスクを止めずに走らせやすくなります。

Podcast では、今日の4本を「エージェントの自律性を上げるとき、人間はどこに立つのか」という一本の話にまとめると聞きやすそうです。前半で HOTL と HITL の違いを説明し、中盤で Claude Code の loop と Codex の `/goal` を使って、エージェント自身が工程や目的を持つ意味を掘る。後半で Twitter Atlas を持ち出し、長いループを人間が監督するには、ログやグラフや近傍探索のような観測面が不可欠だ、という流れにすると自然です。

## 重要ソース3本

- `wiki/sources/suna-gaku-hotl-human-on-the-loop-ai-complete-x-2026-06-14.md`
- `wiki/sources/0xmorty-9-step-loop-claude-code-senior-engineer-x-2026-06-15.md`
- `wiki/sources/thsottiaux-codex-set-own-goal-x-2026-06-14.md`

## 追加された主なKBノート

- `wiki/sources/0xmorty-9-step-loop-claude-code-senior-engineer-x-2026-06-15.md`
- `wiki/sources/suna-gaku-hotl-human-on-the-loop-ai-complete-x-2026-06-14.md`
- `wiki/sources/thsottiaux-codex-set-own-goal-x-2026-06-14.md`
- `wiki/sources/tiagozip-twitter-atlas-all-of-twitter-map-x-2026-06-13.md`



## 重要ソース

### 0xMorty — The 9-Step Loop That Turns Claude Code Into a Senior Engineer

Source note: `wiki/sources/0xmorty-9-step-loop-claude-code-senior-engineer-x-2026-06-15.md`

# 0xMorty — The 9-Step Loop That Turns Claude Code Into a Senior Engineer

## Source Metadata
- Raw path: [[../../raw/articles/0xmorty-9-step-loop-claude-code-senior-engineer-x-2026-06-15.md]]
- Original URL: https://x.com/i/status/2066469702075920794
- Article URL: https://x.com/i/article/2066436932624629760
- Author: 0xMorty / @0xMortyx
- Posted: 2026-06-15T10:35:44.000Z
- Captured: 2026-06-16 via xurl bookmarks capture
- Type: X article card
- Evidence strength: bookmark snapshot metadata plus article title; the capture does not expose the article body

## Summary
The bookmark surfaces an X article titled "The 9-Step Loop That Turns Claude Code Into a Senior Engineer." Even without the body text, the title is a strong signal for a structured, repeatable operating loop around Claude Code rather than a single prompt pattern.

## Key claims
- Claude Code can be improved through a staged loop instead of ad hoc prompting.
- The useful unit is a recurring operating process, not a one-off instruction.
- The article frames the result as moving Claude Code toward more senior-engineer-like behavior.

## Evidence / examples
- The capture contains the article title and the canonical post ID.
- No article body was exposed in the bookmark payload, so the exact 9-step content is not yet independently inspectable here.

## Evidence Quality
- Source type: X article card capture
- Confidence: medium
- Supports: loop-engineering, long-running-agent, and workflow-design claims
- Main limitations: title-only capture; the article body is not present in the bookmark payload
- Best use: practitioner signal for recurring operational loops around coding agents

## Related Concepts
- [[../concepts/loop-engineering.md]]
- [[../concepts/long-running-agents.md]]
- [[../concepts/self-verification.

### スナガク — HOTL / Human on the Loop

Source note: `wiki/sources/suna-gaku-hotl-human-on-the-loop-ai-complete-x-2026-06-14.md`

# スナガク — HOTL / Human on the Loop

## Source Metadata
- Raw path: [[../../raw/articles/suna-gaku-hotl-human-on-the-loop-ai-complete-x-2026-06-14.md]]
- Original URL: https://x.com/i/status/2065952537132630320
- Author: スナガク / @suna_gaku
- Posted: 2026-06-14T00:20:43.000Z
- Captured: 2026-06-16 via xurl bookmarks capture
- Type: X post
- Evidence strength: direct bookmark text from xurl bookmarks capture

## Summary
The post proposes HOTL, "Human on the Loop," as a way to remove the manual confirmation phase from an AI workflow and let the AI finish the flow itself. The main objection to HITL here is that a blocked human can stall the entire system.

## Key claims
- Human-on-the-loop is preferable when the goal is end-to-end completion.
- Human-in-the-loop introduces a human bottleneck if confirmation is required at every phase.
- The useful shift is from supervision-by-default to supervision only where it matters.

## Evidence / examples
- The bookmark text explicitly contrasts HOTL and HITL.
- The claim is expressed as a workflow principle, not as a benchmark or implementation study.

## Evidence Quality
- Source type: practitioner X post
- Confidence: medium
- Supports: agent-autonomy, approval-policy, and workflow-decomposition discussions
- Main limitations: no concrete system design, evaluation data, or counterexample discussion
- Best use: shorthand for a less-blocking oversight model

## Related Concepts
- [[../concepts/human-in-the-loop.md]]
- [[../concepts/agent-autonomy.md]]
- [[../concepts/approval-policy.md]]
- [[../concepts/long-running-agents.md]]

## Related Maps
- [[../maps/approval-policy-patterns-and-escalation.md]]
- [[../maps/agent-deployment-gates-and-operational-risk.md]]

## Open Questions
- Which steps can safely move from HITL to HOTL without cr

### Tibo — Codex can see and set its own /goal

Source note: `wiki/sources/thsottiaux-codex-set-own-goal-x-2026-06-14.md`

# Tibo — Codex can see and set its own /goal

## Source Metadata
- Raw path: [[../../raw/articles/thsottiaux-codex-set-own-goal-x-2026-06-14.md]]
- Original URL: https://x.com/i/status/2066270561081454989
- Related post: https://twitter.com/skirano/status/2066225908202053818
- Author: Tibo / @thsottiaux
- Posted: 2026-06-14T21:24:25.000Z
- Captured: 2026-06-16 via xurl bookmarks capture
- Type: X post / quote-fragment
- Evidence strength: direct bookmark text from xurl bookmarks capture

## Summary
The post frames Codex as more than a command executor: it can see and set its own `/goal`, which is a concise way to describe meta-prompting moving into the agent's operating loop. The underlying intuition is that the agent should be able to infer task boundaries from intent and keep steering itself.

## Key claims
- Codex can participate in goal formation, not just goal execution.
- Goal-setting can be treated as part of the agent surface itself.
- Meta prompting becomes more useful when the agent can translate intent into its own task structure.

## Evidence / examples
- The bookmark text explicitly names `/goal` and the generalization to meta prompting.
- The linked Skirano status provides adjacent context, but the bookmark already contains the core claim.

## Evidence Quality
- Source type: practitioner X post
- Confidence: medium
- Supports: loop-engineering, agent-autonomy, and goal-driven execution claims
- Main limitations: brief quote-style capture, no implementation detail, and no evaluation data
- Best use: a compact signal that `/goal` is becoming a self-directed control surface

## Related Concepts
- [[../concepts/loop-engineering.md]]
- [[../concepts/agent-autonomy.md]]
- [[../concepts/incremental-progress.md]]
- [[../concepts/agent-management.md]]

## Related M

### tiago — Twitter Atlas

Source note: `wiki/sources/tiagozip-twitter-atlas-all-of-twitter-map-x-2026-06-13.md`

# tiago — Twitter Atlas

## Source Metadata
- Raw path: [[../../raw/articles/tiagozip-twitter-atlas-all-of-twitter-map-x-2026-06-13.md]]
- Original URL: https://x.com/i/status/2065735939507601802
- Product URL: https://atlas.tiago.zip?ref=launch_tweet
- Author: tiago / @tiagozip_
- Posted: 2026-06-13T10:00:02.000Z
- Captured: 2026-06-16 via xurl bookmarks capture
- Type: X post / product launch card
- Evidence strength: bookmark snapshot metadata plus the linked product title and description

## Summary
Twitter Atlas is a map of social proximity: each account is placed near the people it talks to, and the product pitches itself as a way to understand your cluster, neighbors, and position in the network. The useful KB signal is the graph-first way it makes relationships visible.

## Key claims
- Social networks can be understood as spatial maps of adjacency.
- Cluster position can reveal context that a flat list of accounts does not.
- Graph visualization can surface relational structure for exploration.

## Evidence / examples
- The bookmark text explicitly describes an account map and cluster placement.
- The linked product title says it is a map of all of Twitter, not just a single profile view.

## Evidence Quality
- Source type: product launch card
- Confidence: medium
- Supports: context-graph and graph-navigation analogies
- Main limitations: this is a launch claim, not a study of actual analytic value
- Best use: inspiration for graph-shaped context surfaces and neighborhood exploration

## Related Concepts
- [[../concepts/context-graph.md]]
- [[../concepts/compiled-wiki.md]]
- [[../concepts/open-knowledge-format.md]]
- [[../concepts/context-engineering.md]]

## Related Maps
- [[../maps/context-graph-and-company-brain.md]]
- [[../maps/research-os-query-paths.md]]

## 更新された概念・地図

## NotebookLM Podcast用メモ

- まず今日の全体トレンドを話してから、重要ソースを3本に絞って深掘りする。
- ソース単体の紹介で終わらせず、既存KBの概念や地図がどう更新されたかを会話に含める。
- 最後に、明日以降の調査問いを2〜3個提示する。
