<!-- generated: 2026-08-09T13:01:37.022004+00:00 -->
<!-- kb_daily_digest_date: 2026-08-09 -->
# KB Daily Digest Source — 2026-08-09

このページは、knowledge-base-llm の日次更新を NotebookLM に読み込ませるための公開向けソースページです。
Discord通知よりも文脈を厚めに残し、Podcast化しやすいように、今日追加・更新されたソース、概念、地図を文章中心で整理します。

## 今日の全体像

# KB Daily Digest — 2026-08-09

2026-08-09 UTC の knowledge-base-llm 更新では、X bookmark ingest から2本の新規 source note が追加されました。どちらも短い practitioner tip ですが、共通しているのは「どのモデルに、どの役割を、どの実行面で 맡せるか」を環境変数や起動パスのような harness 設定として扱っている点です。KB全体の流れとしては、coding agents、agent management、loop engineering、worker-based composition にまたがる小さな更新です。

重要ソースの1本目は、コキチーズ / @k2wanko さんによる Fable 5 と Sonnet 5 の Plan Mode 設定メモです。投稿の主張はシンプルで、`ANTHROPIC_DEFAULT_OPUS_MODEL` を `claude-fable-5[1m]`、`ANTHROPIC_DEFAULT_SONNET_MODEL` を `claude-sonnet-5[1m]`、`ANTHROPIC_MODEL` を `opusplan` にすることで、Plan Mode は Fable 5、それ以外は Sonnet 5 に振り分けられる、というものです。ベンチマークではありませんが、planning と execution を別モデルにルーティングする実例として明確です。

この1本目の読みどころは、モデル選択がユーザーの都度判断ではなく、実行環境のデフォルトとして固定されている点です。Plan Mode は高い推論品質や長い検討が求められる場面、通常作業は別モデルで十分な場面、という役割分担が暗黙にあります。KB上では、loop engineering や agent management の文脈で、ループの各段階に異なるモデル/コスト/能力を割り当てる harness knob として扱えます。

重要ソースの2本目は、ミロ / @ml0_1337 さんによる「GPT-5.6 Luna を Codex App の subagent として使う」セットアップメモです。具体的には `CODEX_CLI_PATH` を ChatGPT.app の実行パスへ向けて Codex App を起動する、という path override の話で、投稿者はこれによって token 消費量がかなり改善しそうだと見ています。これも単体では anecdotal な tips ですが、サブエージェント選択をアプリ起動層で制御する例として興味深いものです。

2本を並べると、今日の全体トレンドは「モデルルーティングがプロンプト内の相談から、環境変数・CLIパス・Plan Mode・subagent selection といった外側の操作面へ移っている」です。つまり、エージェントを賢く使うための工夫が、毎回の指示文ではなく、あらかじめ作った harness の形に近づいています。これは、長時間運用やチーム内標準化に向く一方で、サポート外の設定や brittle な path override に依存するリスクも含みます。

KB内の概念更新としては、新規 source note が `coding-agents`、`agent-management`、`loop-engineering`、`long-running-agents`、`intelligent-delegation`、`worker-based-composition` に接続されました。特に `agent-management` との接続は重要です。人間が「今回はこのモデルで」と毎回判断するのではなく、作業フェーズやサブエージェントの役割に応じて既定ルートを作ることは、エージェント群を管理する実務の一部になりつつあります。

実務上の含意は、モデルを1種類の汎用知能として見るよりも、planning、editing、background work、subagent work、review などの役割に分解して、それぞれに最小十分なモデルと権限を割り当てる設計が効きやすいということです。ただし、今日のソースはいずれも短いX投稿で、再現性・移植性・安全性の検証はまだ薄いです。したがって、KBでは「有望な運用パターンのシグナル」として扱い、強い一般則にはしないのが妥当です。

次に追う問いは3つです。第一に、Plan Mode と通常実行でモデルを分けたとき、品質、速度、コスト、修正回数は実際にどう変わるのか。第二に、`CODEX_CLI_PATH` のような path override は、公式に支えられた設定面なのか、それともリリース更新で壊れやすい local hack なのか。第三に、サブエージェントの token efficiency は、モデル選択だけでなく、タスク分割、context handoff、権限範囲、成果物フォーマットとどう相互作用するのか。今日の更新は2本だけですが、agent harness を「モデルを差し替える場所」として読む流れを補強する更新として記録する価値があります。


## 重要ソース

### K2wanko - Fable 5 plan-mode config

Source note: `wiki/sources/k2wanko-fable-5-plan-mode-config-x-2026-07-01.md`

# K2wanko - Fable 5 plan-mode config

## Source Metadata
- Raw path: `../../raw/articles/k2wanko-fable-5-plan-mode-config-x-2026-07-01.md`
- Raw bookmark capture: `../../raw/x/bookmarks/bookmarks-20260809T0000Z.json`
- Original URL: https://x.com/i/status/2072409890195464627
- Author: コキチーズ / @k2wanko
- Posted: 2026-07-01T19:59:55.000Z
- Captured: 2026-08-09T00:00:22.001Z via xurl bookmarks capture
- Type: X configuration tip / snippet
- Evidence strength: medium; the post is a short setup note, but the configuration itself is explicit
- Public metrics at capture: 666 likes, 65 reposts, 5 replies, 11 quotes, 952 bookmarks, 90312 impressions

## Summary
K2wanko describes a setup where Fable 5 handles planning and Sonnet 5 handles the rest of the work. The post does not present a benchmark or a general rule, but it does give a concrete environment-variable split that treats plan mode and routine execution as separate routing surfaces.

## Key Claims
- `ANTHROPIC_DEFAULT_OPUS_MODEL` can be set to `claude-fable-5[1m]`.
- `ANTHROPIC_DEFAULT_SONNET_MODEL` can be set to `claude-sonnet-5[1m]`.
- `ANTHROPIC_MODEL` can be set to `opusplan`.
- With that setup, Plan Mode uses Fable 5 while other work uses Sonnet 5.

## Evidence / Examples
- The note includes the exact shell exports.
- The author states the resulting behavior in plain language at the end of the post.
- The post is short, so there is no additional explanation of why this split works beyond the implied cost/quality tradeoff.

## Evidence Quality
- Source type: X practitioner config note
- Confidence: medium for the existence of the setup, low for any broad claim that it is the best configuration
- Supports: [[../concepts/coding-agents.md]], [[../concepts/loop-engineering.md]], [[../concepts/agent-management.md]], [[..

### Miro - Codex App subagent with GPT-5.6 Luna

Source note: `wiki/sources/ml0-1337-codex-app-subagent-gpt-56-luna-x-2026-08-08.md`

# Miro - Codex App subagent with GPT-5.6 Luna

## Source Metadata
- Raw path: `../../raw/articles/ml0-1337-codex-app-subagent-gpt-56-luna-x-2026-08-08.md`
- Raw bookmark capture: `../../raw/x/bookmarks/bookmarks-20260809T0000Z.json`
- Original URL: https://x.com/i/status/2085989856380121439
- Linked media URL: https://x.com/ml0_1337/status/2085989856380121439/photo/1
- Author: ミロ / @ml0_1337
- Posted: 2026-08-08T07:21:52.000Z
- Captured: 2026-08-09T00:00:22.001Z via xurl bookmarks capture
- Type: X practitioner tip / screenshot post
- Evidence strength: medium; the setup is explicit, but the support is a single screenshot-and-caption post
- Public metrics at capture: 129 likes, 6 reposts, 1 reply, 2 quotes, 222 bookmarks, 16614 impressions

## Summary
Miro says they found a way to use GPT-5.6 Luna as a subagent inside Codex App, which they expect to reduce token consumption. The concrete mechanism is an environment-variable override that points `CODEX_CLI_PATH` at the ChatGPT app binary, so the post is really about harness wiring rather than model theory.

## Key Claims
- GPT-5.6 Luna can be used as a Codex App subagent.
- The setup may materially improve token efficiency.
- The user can influence Codex behavior by setting `CODEX_CLI_PATH` before launching the app.

## Evidence / Examples
- The post gives a step-by-step setup.
- The visible command overrides `CODEX_CLI_PATH` to a ChatGPT app path on macOS.
- The caption explicitly claims the subagent behavior is achieved through that path selection.

## Evidence Quality
- Source type: X practitioner tip with a screenshot
- Confidence: medium for the reported setup, low for portability without more context
- Supports: [[../concepts/coding-agents.md]], [[../concepts/intelligent-delegation.md]], [[../concepts/worker-based-

## 更新された概念・地図

## NotebookLM Podcast用メモ

- まず今日の全体トレンドを話してから、重要ソースを3本に絞って深掘りする。
- ソース単体の紹介で終わらせず、既存KBの概念や地図がどう更新されたかを会話に含める。
- 最後に、明日以降の調査問いを2〜3個提示する。
