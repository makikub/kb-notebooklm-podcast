<!-- generated: 2026-07-03T13:01:58.447128+00:00 -->
<!-- kb_daily_digest_date: 2026-07-03 -->
# KB Daily Digest Source — 2026-07-03

このページは、knowledge-base-llm の日次更新を NotebookLM に読み込ませるための公開向けソースページです。
Discord通知よりも文脈を厚めに残し、Podcast化しやすいように、今日追加・更新されたソース、概念、地図を文章中心で整理します。

## 今日の全体像

# KB Daily Digest — 2026-07-03

今日の knowledge-base-llm は、UTC 2026-07-03 00:07 の `kb: ingest 2026-07-03 x bookmarks` により、Xブックマーク由来の新規 source notes が4本追加されました。新規 raw は `raw/articles/browser-use-cli-3-0-x-2026-07-02.md`、`raw/articles/claude-code-dataviz-skill-x-2026-07-01.md`、`raw/articles/herdr-runtime-for-coding-agents-x-2026-06-30.md`、`raw/articles/taylor-caldwell-x-mcp-x-2026-06-30.md`、および `raw/x/bookmarks/bookmarks-20260703T0000Z.json` です。wiki 側では対応する `wiki/sources/` が4本増え、`wiki/INDEX.md` も更新されています。

全体トレンドは、「AIに何をさせるか」から「AIが作業できる面をどう薄く、権限つきで、検証可能に開くか」へ寄っています。Browser Use CLI 3.0 はブラウザを直接CDPで操作する薄い harness を示し、X MCP は first-party API をMCP互換ツールとしてAIクライアントに接続する流れを示します。herdr は coding agent をチャットアプリではなく、terminal、agent instance、state を所有する runtime として位置づけています。Claude Code の `/dataviz` skill は、出力品質のガイドラインと validator を context artifact として持ち込む方向です。

重要ソース1本目は、`Browser Use - Browser Use CLI 3.0` です。ソースノートでは、Browser Use CLI 3.0 が任意のモデルを browser agent 化し、`browser-harness` 経由の direct CDP control を使い、cloud browser と real Chrome の両方に対応する、と整理されています。KB上では `tool-accessibility`、`harness-engineering`、`coding-agents`、`agent-recognizable-repository` に接続されています。特に重要なのは、browser automation の価値が「高機能SDK」よりも、モデルから見て扱いやすい最小の操作面に移る可能性です。

重要ソース2本目は、`Taylor Caldwell - 𝕏 MCP` です。X API を MCP-compatible AI tool から使えるようにし、ユーザー自身の account permissions で動かす、という発表として取り込まれました。KBでは `tool-accessibility`、`managed-agents`、`agent-management`、`gateway-control-plane`、`harness-engineering` に接続されています。これはAPI公開の話であると同時に、AIクライアントが外部プラットフォーム上で何をできるかを、permission scope と audit の問題として扱う必要があることを示す更新です。

重要ソース3本目は、`herdr - runtime for coding agents` です。herdr は「app」ではなく「runtime for your coding agents」として、terminal、agent、state を所有し、どこからでも drive できる control surface として提示されています。KBでは `background-agents`、`long-running-agents`、`managed-agents`、`agent-management`、`harness-engineering`、`gateway-control-plane` に接続されました。coding agent の競争軸が、単発のチャットUIやIDE拡張ではなく、長時間動く agent 群を安全に見て、止めて、再開し、状態を扱う runtime に広がっていることを示すシグナルです。

4本目の `Daniel San - Claude Code /dataviz skill` は、今日のトレンドを品質保証の方向から補強しています。Claude Code v2.1.198 の built-in `/dataviz` skill は、chart selection、layout、visual hierarchy の guidance を context にロードし、color-palette validator も含むとされています。KB上では `rich-agent-output-artifact`、`context-engineering`、`self-verification`、`tool-accessibility`、`harness-engineering` に接続されました。これは、見た目の良い成果物を「センス」だけで作るのではなく、再利用可能なskillと機械的な検査に分解する動きとして読めます。

今日の更新で見えてくる地図は、agent harness の上下両面です。下側では Browser Use CLI 3.0 や X MCP のように、ブラウザやプラットフォームAPIをAIから呼びやすい tool surface に落とし込む動きがあります。中央では herdr のように、複数のcoding agentとterminal stateを持続的に管理する runtime が出てきています。上側では `/dataviz` skill のように、成果物の品質を context、rule、validator によって支える仕組みが増えています。

実務上の読みどころは、これらがすべて「薄く開く」だけでは足りない点です。Direct CDP control は強力ですが、操作が薄くなるほど安全な抽象化や観測可能性が必要になります。MCPでAPIを開くと、account-scoped permission と監査が重要になります。runtime が terminal state を握るなら、並列ジョブ、権限、停止、復旧の設計が不可欠です。dataviz skill のような validator も、検査できる品質と検査できない判断の境界を見極める必要があります。

次に追う問いは、direct CDP control と高水準browser APIの使い分け、MCP tool surface の権限スコープと監査、agent runtime がterminal stateとagent stateをどう分離するか、そしてdatavizのような領域知識をどこまでportable skillとして持ち運べるか、の四つです。Podcastでは、「AIエージェントの進化は、モデル能力ではなく、作業面・権限面・runtime面・検証面の再設計として進んでいる」という切り口で話すと、今日の4本を一つの流れとして説明しやすいはずです。


## 重要ソース

### Browser Use - Browser Use CLI 3.0

Source note: `wiki/sources/browser-use-cli-3-0-x-2026-07-02.md`

# Browser Use - Browser Use CLI 3.0

## Source Metadata
- Raw path: `raw/articles/browser-use-cli-3-0-x-2026-07-02.md`
- Raw bookmark capture: `raw/x/bookmarks/bookmarks-20260703T0000Z.json`
- Original URL: https://x.com/i/status/2072699513228378262
- Primary URL: https://x.com/browser_use/status/2072699513228378262/video/1
- Author: Browser Use (@browser_use)
- Posted: 2026-07-02T15:10:47.000Z
- Captured: 2026-07-03 via xurl bookmarks capture
- Type: X post / product teaser
- Evidence strength: bookmark snapshot metadata plus official video teaser
- Public metrics at capture: 13 reposts, 5 replies, 328 likes, 2 quotes, 349 bookmarks, 23114 impressions

## Summary
Browser Use CLI 3.0 is presented as a thin browser-agent runtime that can turn any model into a browser agent via direct CDP control. The announcement matters because it keeps the harness minimal while extending support to cloud browsers and real Chrome.

## Key Claims
- Browser Use CLI 3.0 can turn any model into a browser agent.
- The CLI uses direct CDP control through browser-harness.
- It can run on cloud browsers or real Chrome.
- The release claims a smaller and cheaper token footprint.

## Evidence / Examples
- The post explicitly names "Browser Use CLI 3.0."
- It says "Direct CDP control via browser-harness."
- It also claims the interface works with cloud browsers or a real Chrome instance.

## Evidence Quality
- Source type: X post / product teaser
- Confidence: high for the browser-agent framing, medium for the exact footprint and token-efficiency claims
- Supports: tool accessibility, harness engineering, coding agents, browser automation, agent-recognizable repositories
- Main limitations: the post is promotional and does not include methodology or stability data
- Best use: compare thin browser 

### Daniel San - Claude Code /dataviz skill

Source note: `wiki/sources/claude-code-dataviz-skill-x-2026-07-01.md`

# Daniel San - Claude Code /dataviz skill

## Source Metadata
- Raw path: `raw/articles/claude-code-dataviz-skill-x-2026-07-01.md`
- Raw bookmark capture: `raw/x/bookmarks/bookmarks-20260703T0000Z.json`
- Original URL: https://x.com/i/status/2072460033896419478
- Primary URL: https://x.com/dani_avila7/status/2072460033896419478/video/1
- Author: Daniel San (@dani_avila7)
- Posted: 2026-07-01T23:19:11.000Z
- Captured: 2026-07-03 via xurl bookmarks capture
- Type: X post / product teaser
- Evidence strength: bookmark snapshot metadata plus official video teaser
- Public metrics at capture: 58 reposts, 11 replies, 632 likes, 5 quotes, 689 bookmarks, 83605 impressions

## Summary
The `/dataviz` skill turns chart and dashboard guidance into a built-in context artifact. The important shift is that visualization rules are no longer just tribal knowledge: Claude Code can load them directly and run a validator against the resulting palette choices.

## Key Claims
- Claude Code v2.1.198 includes a built-in `/dataviz` skill.
- The skill loads chart and dashboard guidance into context.
- The guidance covers chart selection, layout, and visual hierarchy.
- A runnable color-palette validator is included.

## Evidence / Examples
- The tweet text explicitly names the built-in skill and version.
- It says the skill loads design guidance directly into context.
- It also says there is a runnable validator, implying a machine-checkable guardrail.

## Evidence Quality
- Source type: X post / product teaser
- Confidence: high for the existence of the skill, medium for how broadly it will generalize in practice
- Supports: rich agent output artifact, context engineering, self-verification, tool accessibility, harness engineering
- Main limitations: the post is short and does not show the full

### herdr - runtime for coding agents

Source note: `wiki/sources/herdr-runtime-for-coding-agents-x-2026-06-30.md`

# herdr - runtime for coding agents

## Source Metadata
- Raw path: `raw/articles/herdr-runtime-for-coding-agents-x-2026-06-30.md`
- Raw bookmark capture: `raw/x/bookmarks/bookmarks-20260703T0000Z.json`
- Original URL: https://x.com/i/status/2072023156139708480
- Primary URL: https://x.com/herdrdev/status/2072023156139708480/video/1
- Author: herdr (@herdrdev)
- Posted: 2026-06-30T18:23:11.000Z
- Captured: 2026-07-03 via xurl bookmarks capture
- Type: X post / product framing
- Evidence strength: bookmark snapshot metadata plus official video teaser
- Public metrics at capture: 29 reposts, 16 replies, 553 likes, 9 quotes, 362 bookmarks, 54062 impressions

## Summary
herdr positions itself as a runtime for coding agents, not just a chatbot or app. The useful signal is the control-surface framing: it owns terminals, agent state, and remote driving from anywhere, which aligns it with the broader move toward persistent agent runtimes.

## Key Claims
- herdr is intentionally not framed as an app.
- The product owns terminals, agent instances, and their state.
- Users can drive the runtime remotely from anywhere.

## Evidence / Examples
- The post explicitly says "runtime for your coding agents."
- It says the runtime "owns your terminals, your agents, their state."
- The final clause makes the remote-control claim: "drive them from anywhere."

## Evidence Quality
- Source type: X post / product framing
- Confidence: high for the framing, medium for the operational details beyond the teaser
- Supports: managed agents, background agents, long-running agents, agent management, harness engineering
- Main limitations: the visible text is truncated at the end and does not specify guardrails, pricing, or product boundaries
- Best use: a compact signal for runtime-centered agent con

### Taylor Caldwell - 𝕏 MCP

Source note: `wiki/sources/taylor-caldwell-x-mcp-x-2026-06-30.md`

# Taylor Caldwell - 𝕏 MCP

## Source Metadata
- Raw path: `raw/articles/taylor-caldwell-x-mcp-x-2026-06-30.md`
- Raw bookmark capture: `raw/x/bookmarks/bookmarks-20260703T0000Z.json`
- Original URL: https://x.com/i/status/2071753251360502131
- Primary URL: https://twitter.com/XDevelopers/status/2071752389183647758
- Author: Taylor Caldwell (@taycaldwell)
- Posted: 2026-06-30T00:30:41.000Z
- Captured: 2026-07-03 via xurl bookmarks capture
- Type: X post / quote post
- Evidence strength: bookmark snapshot metadata plus quoted original announcement
- Public metrics at capture: 138 reposts, 128 replies, 3696 likes, 31 quotes, 2081 bookmarks, 801250 impressions

## Summary
The 𝕏 MCP announcement is a direct signal that X wants its API surfaced through MCP-compatible tools with account-scoped permissions. Even as a quote post, the product framing is clear: the interesting unit is not just the API, but the permissioned tool surface for AI clients.

## Key Claims
- X has announced an MCP surface for its API.
- The surface can be used from any MCP-compatible AI tool.
- Users operate it with their own account permissions.

## Evidence / Examples
- The post text explicitly says "Announcing the 𝕏 MCP."
- It says the API can be used with "any MCP-compatible AI tool."
- It also says the tool uses "your own account’s permissions," which implies account-scoped access control.

## Evidence Quality
- Source type: X quote post / product announcement
- Confidence: high for the announcement framing, medium for feature depth beyond the visible text
- Supports: tool accessibility, managed agents, agent management, gateway-control-plane, harness engineering
- Main limitations: the quote post itself is short and does not specify the full permission model or available actions
- Best use: track h

## 更新された概念・地図

## NotebookLM Podcast用メモ

- まず今日の全体トレンドを話してから、重要ソースを3本に絞って深掘りする。
- ソース単体の紹介で終わらせず、既存KBの概念や地図がどう更新されたかを会話に含める。
- 最後に、明日以降の調査問いを2〜3個提示する。
