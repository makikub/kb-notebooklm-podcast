<!-- generated: 2026-06-18T13:02:14.666222+00:00 -->
<!-- kb_daily_digest_date: 2026-06-18 -->
# KB Daily Digest Source — 2026-06-18

このページは、knowledge-base-llm の日次更新を NotebookLM に読み込ませるための公開向けソースページです。
Discord通知よりも文脈を厚めに残し、Podcast化しやすいように、今日追加・更新されたソース、概念、地図を文章中心で整理します。

## 今日の全体像

# KB Daily Digest 2026-06-18

今日の knowledge-base-llm は、UTC 2026-06-18 に X ブックマーク由来の新規 ingest / compile がありました。確認できた追加は、Cursor の cloud agent handoff、Figma MCP の Slides / FigJam / Make 拡張、Claude loop 作成記事へのポインタ、そして Codex の open source model 対応ドキュメントポインタの4本です。いずれも単発のTipsというより、エージェントをどこで動かし、どの成果物へ接続し、どのモデルやループで運用するかという「agent harness」の実装面に寄っています。

全体トレンドは、「AIエージェントがチャット欄やローカルIDEの中だけで完結しなくなっている」ことです。Cursor はローカルで始めた agent をクラウドへ移し、ノートPCを閉じても走らせ、スマートフォンから指示し、複数agentを並列に動かしてPRとdemoを返す流れを示しています。一方で Figma は MCP server の操作対象をデザインキャンバスだけでなく、Slides、FigJam、Figma Make の code-to-canvas round trip、custom fonts、image export へ広げています。コード生成の先にあるレビュー資料、ホワイトボード、デザイン成果物まで agent-accessible surface に入ってきた、という読みができます。

重要ソースの1本目は、**Cursor - local agents can move to the cloud and keep working** です。これは公式X投稿のproduct teaserで、証拠としては高いものの、正確なrollout範囲や制約はまだ分かりません。それでも、phone prompting、parallel agents、PR delivery、demo返却が同じ文脈で語られている点は大きいです。KB上では `background-agents`、`long-running-agents`、`managed-agents`、`multi-agent-orchestration` に接続され、agentを「一回の補完」ではなく「遠隔で継続する作業単位」として扱う方向を補強しました。

重要ソースの2本目は、**Figma - MCP server expands to Slides, FigJam, and Make round-tripping** です。Figma MCP の拡張は、agentic design workflow の対象が「画面を少し編集する」だけではなく、deck生成、board作成、code/canvas往復、fontやimage exportを含む成果物生成へ広がることを示しています。実務的には、AIが作るものをコード差分だけでレビューするのではなく、design review、planning board、presentation deck といった別形式のartifactでも検証できるようになる可能性があります。

重要ソースの3本目は、**Tibo - Codex works with open source models too** です。これはX投稿自体は短い reminder ですが、リンク先が OpenAI の Codex advanced config docs であるため、Codex App / CLI / SDK が local provider 経由で open source model と組み合わせられるという deployment signal として扱えます。KBでは、モデル選択がプロダクト境界ではなく構成項目になっていく、という観点で `coding-agents`、`tool-accessibility`、`agent-management`、`harness-engineering` に接続されました。

4本目の **MIKE - How to Create Loops with Claude** は、現時点では記事本文がcaptureされておらず、article card title だけの薄いソースです。そのため深い主張は避けつつ、`loop-engineering`、`generator-evaluator-loop`、`feedback-controls`、`self-verification` の後続enrichment候補として登録されています。今日の他3本が実行環境、成果物面、モデル構成の話だとすると、このソースは「その上でagentをどう反復させるか」という運用設計側の入口です。

KB内の地図更新としては、今回の4ソースが `agent-harness-landscape`、`harness-engineering-vendor-comparison`、`coding-agent-harness-patterns`、`coding-agent-cognitive-debt-and-review-capacity` に分散して接続されました。特に Cursor と Figma は vendor comparison に載せやすい対比です。Cursor は agent execution / PR workflow のcontrol plane、Figma は agent output artifact / design surface の拡張として読めます。Codex OSS mode は、同じharnessを別モデルへ差し替える portability の論点を足します。

実務上の示唆は、agent導入を「どのモデルが賢いか」だけで見ない方がよい、ということです。長時間実行できるか、モバイルや非同期レビューで扱えるか、成果物がPRだけでなくデモやスライドやボードとして残るか、そしてモデルbackendを将来差し替えられるか。今日の更新は、こうした運用上の接続面が製品差になり始めていることを示しています。逆に言えば、agentを並列化・クラウド化するほど、reviewability、guardrails、repo内の衝突管理、生成artifactの品質確認が重くなるはずです。

Podcast化するなら、今日の回は「agent harness はIDEから運用基盤へ広がる」を主題にすると聞きやすそうです。前半で Cursor の cloud handoff を取り上げ、agent がローカル端末から離れて継続作業化する流れを説明する。中盤で Figma MCP を使って、エージェントの出力先がコードからデザイン、スライド、ホワイトボードへ広がる話をする。後半で Codex OSS mode と Claude loops をつなぎ、モデル選択とloop設計はharness側の構成問題になっていく、というまとめにすると、今日の4本が一つの線になります。

## 重要ソース3本

- `wiki/sources/cursor-ai-cloud-agents-phone-x-2026-06-17.md`
- `wiki/sources/figma-figma-mcp-server-slides-figjam-make-x-2026-06-16.md`
- `wiki/sources/thsottiaux-codex-open-source-models-x-2026-06-17.md`

## 追加・更新された主なKBノート

- `raw/x/bookmarks/bookmarks-20260618T0000Z.json`
- `raw/articles/cursor-ai-cloud-agents-phone-x-2026-06-17.md`
- `raw/articles/figma-figma-mcp-server-slides-figjam-make-x-2026-06-16.md`
- `raw/articles/mikenevermiss-how-to-create-loops-with-claude-x-2026-06-15.md`
- `raw/articles/thsottiaux-codex-open-source-models-x-2026-06-17.md`
- `wiki/sources/cursor-ai-cloud-agents-phone-x-2026-06-17.md`
- `wiki/sources/figma-figma-mcp-server-slides-figjam-make-x-2026-06-16.md`
- `wiki/sources/mikenevermiss-how-to-create-loops-with-claude-x-2026-06-15.md`
- `wiki/sources/thsottiaux-codex-open-source-models-x-2026-06-17.md`


## 重要ソース

### Cursor - local agents can move to the cloud and keep working

Source note: `wiki/sources/cursor-ai-cloud-agents-phone-x-2026-06-17.md`

# Cursor - local agents can move to the cloud and keep working

## Source Metadata
- Raw path: [[../../raw/articles/cursor-ai-cloud-agents-phone-x-2026-06-17.md]]
- Original URL: https://x.com/i/status/2067366343817805899
- Primary URL: https://x.com/cursor_ai/status/2067366343817805899/video/1
- Author: Cursor (@cursor_ai)
- Posted: 2026-06-17T21:58:40.000Z
- Captured: 2026-06-18 via xurl bookmarks capture
- Type: X post / product teaser
- Evidence strength: bookmark snapshot metadata plus official product teaser video

## Summary
Cursor frames a cloud handoff for local agents as a practical workflow improvement: agents can keep running after the laptop is closed, be prompted from a phone, run in parallel, and return PRs with demos.

## Key Claims
- Cursor is moving agent execution from local machines into the cloud.
- Mobile prompting is part of the intended control surface.
- Parallel agent execution is a first-class use case.
- Returned PRs and demos imply an end-to-end remote work loop rather than only code editing.

## Evidence / Examples
- The tweet text directly names cloud handoff, phone prompting, parallel agents, and PR delivery.
- The attached video preview indicates this is a product announcement, not just a community workaround.

## Evidence Quality
- Source type: X official product teaser
- Confidence: high for the announcement; medium for exact rollout scope
- Supports: long-running agents, managed agents, background execution, and remote operator control
- Main limitations: the bookmark does not expose technical constraints or pricing
- Best use: compare cloud agent control planes and remote workflow surfaces

## Related Concepts
- [[../concepts/background-agents.md]]
- [[../concepts/long-running-agents.md]]
- [[../concepts/managed-agents.md]]
- [[../co

### Figma - MCP server expands to Slides, FigJam, and Make round-tripping

Source note: `wiki/sources/figma-figma-mcp-server-slides-figjam-make-x-2026-06-16.md`

# Figma - MCP server expands to Slides, FigJam, and Make round-tripping

## Source Metadata
- Raw path: [[../../raw/articles/figma-figma-mcp-server-slides-figjam-make-x-2026-06-16.md]]
- Original URL: https://x.com/i/status/2066923337889305038
- Primary URL: https://x.com/figma/status/2066923337889305038/video/1
- Author: Figma (@figma)
- Posted: 2026-06-16T16:38:19.000Z
- Captured: 2026-06-18 via xurl bookmarks capture
- Type: X post / official product update
- Evidence strength: bookmark snapshot metadata plus official product video preview

## Summary
Figma says the MCP server now reaches beyond a single design canvas. The captured post highlights Slides generation/editing, FigJam board creation, code-to-canvas round-tripping in Make, plus custom font support and image exports.

## Key Claims
- The Figma MCP server can now handle slide decks, not just canvas edits.
- FigJam boards are part of the same agent-accessible workflow surface.
- Figma Make now supports code-to-canvas round-tripping in the captured product update.
- Custom font support and image exports make the surface more usable for production artifact generation.

## Evidence / Examples
- The tweet text explicitly names Slides, FigJam, Make, custom fonts, and image exports.
- The attached video preview indicates this is a product update rather than an isolated user report.

## Evidence Quality
- Source type: X official product update
- Confidence: high for the feature announcement; medium for broader workflow implications
- Supports: richer design-agent artifact generation, agent-accessible design surfaces, and code/canvas round-tripping
- Main limitations: the bookmark does not expose the full demo details or implementation limits
- Best use: connect to agentic design workflows and output-artifact handli

### MIKE - How to Create Loops with Claude

Source note: `wiki/sources/mikenevermiss-how-to-create-loops-with-claude-x-2026-06-15.md`

# MIKE - How to Create Loops with Claude

## Source Metadata
- Raw path: [[../../raw/articles/mikenevermiss-how-to-create-loops-with-claude-x-2026-06-15.md]]
- Original URL: https://x.com/i/status/2066401066518802637
- Primary URL: https://x.com/i/article/2066041362298912768
- Author: MIKE (@mikenevermiss)
- Posted: 2026-06-15T06:03:00.000Z
- Captured: 2026-06-18 via xurl bookmarks capture
- Type: X article card
- Evidence strength: bookmark snapshot metadata plus article title

## Summary
This bookmark is an X article card titled "How to Create Loops with Claude." The captured payload does not expose the article body, but the title itself is a useful pointer into practical loop design around Claude.

## Key Claims
- The source is explicitly about creating loops with Claude.
- The article-card framing suggests a practical workflow write-up rather than a product teaser.
- The bookmark is best treated as a source pointer until the article body is separately enriched.

## Evidence / Examples
- The article title is captured in the bookmark payload.
- The post links to an X article URL rather than a generic thread or image card.

## Evidence Quality
- Source type: X article card
- Confidence: medium for the existence of a loop-design article; low for any deeper claims without the article body
- Supports: loop engineering, agent self-prompting, feedback loops, and workflow design
- Main limitations: the bookmark text is just a title and the article body was not captured here
- Best use: seed later enrichment or pair with other loop-engineering sources

## Related Concepts
- [[../concepts/loop-engineering.md]]
- [[../concepts/generator-evaluator-loop.md]]
- [[../concepts/feedback-controls.md]]
- [[../concepts/self-verification.md]]
- [[../concepts/harness-engineering.md]]

## 

### Tibo - Codex works with open source models too

Source note: `wiki/sources/thsottiaux-codex-open-source-models-x-2026-06-17.md`

# Tibo - Codex works with open source models too

## Source Metadata
- Raw path: [[../../raw/articles/thsottiaux-codex-open-source-models-x-2026-06-17.md]]
- Original URL: https://x.com/i/status/2067181377028538431
- Primary URL: https://developers.openai.com/codex/config-advanced#oss-mode-local-providers
- Author: Tibo (@thsottiaux)
- Posted: 2026-06-17T09:43:41.000Z
- Captured: 2026-06-18 via xurl bookmarks capture
- Type: X post / docs pointer
- Evidence strength: bookmark snapshot metadata plus linked OpenAI docs page

## Summary
The bookmark points to OpenAI docs showing that Codex App, CLI, and SDK can run with any open source model via local providers. That is a useful deployment signal because it makes Codex more portable across model backends.

## Key Claims
- Codex App, CLI, and SDK are not limited to OpenAI-hosted models.
- Open source models can be used through the documented local-provider path.
- Model backend choice is becoming a configuration concern rather than a product boundary.

## Evidence / Examples
- The tweet text explicitly calls out support for any open source model.
- The linked docs page is the strongest provenance for the claim.

## Evidence Quality
- Source type: X docs pointer
- Confidence: high for the existence of the documented OSS-mode path; medium for details without reading the docs page directly here
- Supports: model-agnostic agent setups, local-provider configuration, and portable Codex deployments
- Main limitations: the tweet is a reminder rather than a detailed explanation
- Best use: compare Codex portability across backends and deployment modes

## Related Concepts
- [[../concepts/coding-agents.md]]
- [[../concepts/tool-accessibility.md]]
- [[../concepts/agent-management.md]]
- [[../concepts/harness-engineering.md]]
- [[../co

## 更新された概念・地図

## NotebookLM Podcast用メモ

- まず今日の全体トレンドを話してから、重要ソースを3本に絞って深掘りする。
- ソース単体の紹介で終わらせず、既存KBの概念や地図がどう更新されたかを会話に含める。
- 最後に、明日以降の調査問いを2〜3個提示する。
