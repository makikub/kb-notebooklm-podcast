<!-- generated: 2026-07-10T13:02:26.308784+00:00 -->
<!-- kb_daily_digest_date: 2026-07-10 -->
# KB Daily Digest Source — 2026-07-10

このページは、knowledge-base-llm の日次更新を NotebookLM に読み込ませるための公開向けソースページです。
Discord通知よりも文脈を厚めに残し、Podcast化しやすいように、今日追加・更新されたソース、概念、地図を文章中心で整理します。

## 今日の全体像

# KB Daily Digest 2026-07-10

今日の knowledge-base-llm は、2026-07-10 00:08 UTC の `KB: ingest July 10 xurl bookmarks` コミットで、X bookmark capture 由来の3本を新規 ingest しました。追加された raw は `bcherny-claude-code-checkup-maintenance-loop`、`fruitriin-addf-loop-engineering-speakerdeck`、`noriyukitakei-e2e-test-loop-engineering-speakerdeck` の3本で、対応する `wiki/sources/` ノートも作成されています。あわせて `loop-engineering`、`harness-engineering`、`context-engineering`、`real-world-evaluation` が更新され、今回の更新は「ループ設計をどう日常の運用・保守・テスト生成に落とすか」に寄った一日でした。

全体トレンドとしては、単発のプロンプトや単発のエージェント実行ではなく、繰り返し回る作業系そのものを設計対象にする流れが強く出ています。Loop Engineering はすでに KB 内で、目的、文脈、役割、ツール、チェックポイント、評価、リトライ、停止条件までを含む「エージェントが走る反復作業の設計」として整理されています。今日の3本はその定義に対して、保守コマンド、汎用フレームワーク、E2E テスト生成という別々の入口から具体例を追加しました。

重要ソースの1本目は Boris Cherny の Claude Code `/checkup` maintenance loop です。ここでのポイントは、エージェント harness の保守を「思い出した時に手で片付けるもの」ではなく、明示的なコマンドや操作面として扱っていることです。未使用 extension の整理、project instructions の重複排除、root context から nested files / skills への分割、遅い hooks の無効化といった項目は、どれも context engineering と harness engineering の境界にあります。つまり、良い出力を得るための作業は、モデルに投げる前のコンテキスト整理や周辺機構の清掃にも宿る、という見方を強める更新です。

2本目は 果物リン の ADDF loop engineering slide deck です。KB ではこのソースを、単なる prompt recipe ではなく「作りたいものを継続的に作れるようにするための named framework」として取り込みました。詳細な実装までは capture から確定しきれないため evidence quality は中程度ですが、重要なのは、loop engineering が個別の coding task だけでなく、作る活動全体を支える operator workflow design として語られている点です。これは、ハーネスやスキルや手順書を「作業の一部」ではなく「作業を増幅する土台」と見る KB の既存地図に自然につながります。

3本目は Noriyuki Takei の E2E tests 向け loop engineering deck です。ここでの具体的なパターンは `testspec-to-code` で、テスト仕様を durable handoff artifact として維持し、そこから agent が Playwright code を生成・修正していくループです。これは real-world evaluation の観点でも重要です。E2E テストは現実のユーザー操作に近い一方で、変更や失敗の原因追跡が難しい領域です。だからこそ、仕様書を一回限りの計画メモではなく、生成とレビューの往復に使える source of truth として置く意味があります。

概念ノート側では、`loop-engineering` に果物リンと Takei の2本が supporting sources として追加されました。これにより、Loop Engineering の地図は、Addy Osmani や Fable 5 由来の一般論から、より実務的な「フレームワーク化」「テスト仕様からコードへの反復生成」へ広がっています。`harness-engineering` にも今日の3本が追加され、ハーネスを作ることだけでなく、ハーネスを点検し続けること、そして作業ループをプロダクト化・手順化することが論点に入りました。

`context-engineering` の更新では、Boris Cherny の `/checkup` が特に効いています。context は単に増やす・削る対象ではなく、階層化し、重複をなくし、hooks や skills といった周辺要素を含めて整備する運用面になっています。これは、コンテキスト窓の中身だけを考える段階から、context file system、skills、hooks、MCP、起動位置などを含む harness surface 全体へ視野を広げる更新です。

`real-world-evaluation` には Takei の E2E loop が追加されました。今日の digest で見ると、評価は静的ベンチマークではなく、仕様、生成コード、Playwright 実行、失敗の見直しが往復する環境として捉え直されています。実務上は、E2E テストを agent に「書かせる」だけでは不十分で、どの仕様が source of truth で、どの失敗を人間が確認し、どこから再生成するかまでを含めてループ化する必要があります。

今日の実務的な読みどころは、エージェント活用の改善ポイントが「より良いプロンプト」から「保守できるループ」へ移っていることです。未使用 extension や重複 instruction を放置すると、実行コスト、レイテンシ、誤作動の余地が増えます。一方で、テスト仕様のような durable artifact を中心に置くと、agent の生成結果をレビューしやすくなり、失敗から次の改善へ戻しやすくなります。Podcast では、`/checkup` 的な harness hygiene、ADDF のような作業システム化、E2E testspec-to-code の3つを並べて、「ループを作る」と「ループを保守する」は別だが不可分、という論点を掘るとよさそうです。

## Important Sources

- Boris Cherny - Claude Code `/checkup` maintenance loop: `wiki/sources/bcherny-claude-code-checkup-maintenance-loop-x-2026-07-08.md`
- 果物リン - ADDF loop engineering slide deck: `wiki/sources/fruitriin-addf-loop-engineering-speakerdeck-x-2026-07-08.md`
- Noriyuki Takei - loop engineering for E2E tests: `wiki/sources/noriyukitakei-e2e-test-loop-engineering-speakerdeck-x-2026-07-08.md`

## Updated Concepts

- `wiki/concepts/loop-engineering.md`
- `wiki/concepts/harness-engineering.md`
- `wiki/concepts/context-engineering.md`
- `wiki/concepts/real-world-evaluation.md`


## 重要ソース

### Boris Cherny - Claude Code /checkup maintenance loop

Source note: `wiki/sources/bcherny-claude-code-checkup-maintenance-loop-x-2026-07-08.md`

# Boris Cherny - Claude Code /checkup maintenance loop

## Source Metadata
- Raw path: `raw/articles/bcherny-claude-code-checkup-maintenance-loop-x-2026-07-08.md`
- Raw bookmark capture: `raw/x/bookmarks/bookmarks-20260710T0000Z.json`
- Original URL: https://x.com/i/status/2074997570317779038
- Secondary URL: https://x.com/bcherny/status/2074997570317779038
- Author: Boris Cherny / @bcherny
- Posted: 2026-07-08T23:22:27.000Z
- Captured: 2026-07-10 via xurl bookmarks capture
- Type: X post

## Summary
This bookmark treats Claude Code maintenance as a first-class workflow. The key signal is a `/checkup` surface that helps prune unused extensions, deduplicate project instructions, split root context into nested files and skills, and disable slow hooks.

## Key Claims
- Harness maintenance can be surfaced as an explicit command, not left to manual cleanup.
- Instruction deduplication across root and nested `CLAUDE.md` files is worth automating.
- Unused skills, MCPs, and plugins can accumulate enough drag that pruning becomes part of regular operations.
- Hook latency matters enough that "turn off slow hooks" is a meaningful maintenance action.

## Evidence / Examples
- The captured post explicitly lists the `/checkup` actions.
- The post aligns with the repo's broader view that durable agent work depends on context hygiene and stable operator surfaces.

## Evidence Quality
- Source type: truncated X post
- Confidence: high for the existence of the listed maintenance actions, medium for how generalizable they are
- Supports: harness engineering, context management, knowledge-loop hygiene, long-running agents

## Related Concepts
- [[../concepts/harness-engineering.md]]
- [[../concepts/context-engineering.md]]
- [[../concepts/agent-knowledge-loop.md]]
- [[../concepts/long-ru

### 果物リン - ADDF loop engineering slide deck

Source note: `wiki/sources/fruitriin-addf-loop-engineering-speakerdeck-x-2026-07-08.md`

# 果物リン - ADDF loop engineering slide deck

## Source Metadata
- Raw path: `raw/articles/fruitriin-addf-loop-engineering-speakerdeck-x-2026-07-08.md`
- Raw bookmark capture: `raw/x/bookmarks/bookmarks-20260710T0000Z.json`
- Original URL: https://x.com/i/status/2074797903949025773
- Primary URL: https://speakerdeck.com/fruitriin/i-didnt-set-out-to-build-loop-engineering-but-addf-did
- Author: 果物リン / @FruitRiin
- Posted: 2026-07-08T10:09:02.000Z
- Captured: 2026-07-10 via xurl bookmarks capture
- Type: X post / slide deck share

## Summary
This slide deck presents ADDF as a loop-engineering framework. The useful signal is that the author is not just describing a one-off prompt recipe; they are describing a way to build a repeatable system that makes many kinds of work easier to carry through.

## Key Claims
- Loop engineering can be implemented as a named framework rather than an ad hoc set of habits.
- The framework is motivated by wanting to make many things, not by a single coding task.
- The deck sits in the same broad family as other loop and harness notes in this KB, but it leans more toward operator workflow design than model capability.

## Evidence / Examples
- The deck title explicitly says it is a framework for loop engineering.
- The card description emphasizes the goal of building a system that can produce more of the things the author wants to make.

## Evidence Quality
- Source type: slide deck share with limited transcript
- Confidence: medium for the framing, lower for any unquoted implementation details
- Supports: loop engineering, harness engineering, repeated-deliverable workflows

## Related Concepts
- [[../concepts/loop-engineering.md]]
- [[../concepts/harness-engineering.md]]
- [[../concepts/agent-knowledge-loop.md]]

## Related Maps
- [[../maps/cod

### Noriyuki Takei - loop engineering for E2E tests

Source note: `wiki/sources/noriyukitakei-e2e-test-loop-engineering-speakerdeck-x-2026-07-08.md`

# Noriyuki Takei - loop engineering for E2E tests

## Source Metadata
- Raw path: `raw/articles/noriyukitakei-e2e-test-loop-engineering-speakerdeck-x-2026-07-08.md`
- Raw bookmark capture: `raw/x/bookmarks/bookmarks-20260710T0000Z.json`
- Original URL: https://x.com/i/status/2075001763682509238
- Primary URL: https://speakerdeck.com/noriyukitakei/e2ebyloop
- Author: Noriyuki Takei / @noriyukitakei
- Posted: 2026-07-08T23:39:06.000Z
- Captured: 2026-07-10 via xurl bookmarks capture
- Type: X post / slide deck share

## Summary
This deck is a concrete example of loop engineering applied to test automation. The main signal is the explicit `testspec-to-code` pattern: keep a test-spec artifact as the source of truth, then let an agent generate and revise Playwright code from it.

## Key Claims
- E2E test work can be structured as a loop between a specification artifact and generated code.
- The loop should be repeatable enough to act like a self-running environment.
- Test spec documents can be treated as durable handoff artifacts instead of one-time planning notes.

## Evidence / Examples
- The bookmark text names the talk as an implementation of loop engineering for E2E testing.
- The deck metadata explicitly references `testspec-to-code` and Playwright code generation / revision.

## Evidence Quality
- Source type: slide deck share with partial transcript
- Confidence: medium for the overall pattern, lower for any implementation details not visible in the capture
- Supports: loop engineering, coding agents, structured handoff artifacts, eval-review reliability

## Related Concepts
- [[../concepts/loop-engineering.md]]
- [[../concepts/coding-agents.md]]
- [[../concepts/structured-handoff-artifacts.md]]
- [[../concepts/real-world-evaluation.md]]

## Related Maps
- [[../maps

## 更新された概念・地図

### Context Engineering

KB note: `wiki/concepts/context-engineering.md`

---
aliases:
  - Context Engineering
---

# Context Engineering

## Definition
The practice of deliberately deciding what information enters an agent's context window, what is compressed, what is retrieved on demand, and what is dropped.

## Why It Matters
Context is both a cost surface and a reliability surface. Poorly selected context can increase token spend, hide relevant signal, preserve stale mistakes, and make agents appear less capable than they are.

## Related Concepts
- [[context-file-system.md]]
- [[context-resets.md]]
- [[compiled-wiki.md]]
- [[structured-handoff-artifacts.md]]
- [[evidence-quality.md]]
- [[self-verification.md]]
- [[llm-inference-performance.md]]
- [[kv-cache.md]]
- [[organizational-intent-clarity.md]]
- [[conversational-feedback-learning.md]]
- [[workflow-compilation.md]]

## Supporting Sources
- [[../sources/gargetisha-openclaw-under-the-hood-x-article.md]]
- [[../sources/machinelearningmastery-effective-context-engineering-ai-agents.md]]
- [[../sources

### Harness Engineering

KB note: `wiki/concepts/harness-engineering.md`

---
aliases:
  - Harness Engineering
---

# Harness Engineering

## Definition
The design of the environment, artifacts, controls, tooling, and feedback loops around an agent so that it can produce more reliable results over time.

## Why It Matters
As agents become more capable, performance depends less on the model alone and more on the structure that surrounds it.

## Related Concepts
- [[guides and sensors]]
- [[agent recognizable repository]]
- [[structured handoff artifacts]]
- [[machine-checkable invariants]]
- [[heavy-thinking.md]]

## Supporting Sources
- [[../sources/openai-harness-engineering.md]]
- [[../sources/martin-fowler-harness-engineering.md]]
- [[../sources/gota-purpose-first-harness-design-speakerdeck.md]]
- [[../sources/rkaga-how-to-approach-harness-engineering-speakerdeck.md]]
- [[../sources/rkaga-what-harness-engineering-is-and-is-not-zenn.md]]
- [[../sources/sergicalsix-harness-engineering-overview-design-philosophy-speakerdeck.md]]
- [[../sources/yuukiyo-ai-dlc

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

### Real-World Evaluation

KB note: `wiki/concepts/real-world-evaluation.md`

---
aliases:
  - Real-World Evaluation
---

# Real-World Evaluation

## Definition
Evaluation of agent systems in settings closer to actual user tasks, constraints, and long-running workflows rather than only static single-turn benchmarks.

## Why It Matters
A system can look strong on benchmarks while still failing under realistic multi-step conditions.

## Related Concepts
- [[durability]]
- [[trace-driven-improvement]]
- [[harness-engineering]]

## Supporting Sources
- [[../sources/philipp-schmid-agent-harness-2026.md]]
- [[../sources/cursor-bootstrapping-composer-with-autoinstall.md]]
- [[../sources/langchain-deep-agents-harness-engineering.md]]
- [[../sources/kevin-gu-autoagent-x-thread.md]]
- [[../sources/anthropic-claude-mythos-preview.md]]
- [[../sources/anthropic-economic-index-march-2026-report.md]]

- [[../sources/swarm-ai-cloud-argos-ci-x.md]]
- [[../sources/gota-bara-uxaudit-claude-code-plugin-x.md]]
- [[../sources/noriyukitakei-e2e-test-loop-engineering-speakerdeck-x-2026

## NotebookLM Podcast用メモ

- まず今日の全体トレンドを話してから、重要ソースを3本に絞って深掘りする。
- ソース単体の紹介で終わらせず、既存KBの概念や地図がどう更新されたかを会話に含める。
- 最後に、明日以降の調査問いを2〜3個提示する。
