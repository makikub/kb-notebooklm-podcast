<!-- generated: 2026-06-05T13:01:46.581155+00:00 -->
<!-- kb_daily_digest_date: 2026-06-05 -->
# KB Daily Digest Source — 2026-06-05

このページは、knowledge-base-llm の日次更新を NotebookLM に読み込ませるための公開向けソースページです。
Discord通知よりも文脈を厚めに残し、Podcast化しやすいように、今日追加・更新されたソース、概念、地図を文章中心で整理します。

## 今日の全体像

# KB Daily Digest - 2026-06-05

今日の knowledge-base-llm は、UTC 2026-06-05 の `KB ingest: daily X bookmarks 2026-06-05` により、Xブックマーク由来の新規ソース4本と、それに対応する `wiki/sources` 4本、さらに `wiki/maps` の複数更新が入りました。全体トレンドは、AIエージェントの競争軸が「モデルがどれだけ賢いか」から、「価値・文脈・証拠・開発ループを、プロダクトの表面でどう扱うか」へ移っていることです。今日の更新は、ROI保証、ソース帰属、永続メモリ、モバイル開発ループという別々の話に見えますが、どれもエージェント利用を実務の中で信頼可能にするための包装・導線・検証面の話として読めます。

重要ソース1本目は、Cognition の AI Productivity Guarantee です。Devin が支払額以上のエンジニアリング価値を出せなければ、Cognition 側が最大1,000万ドルまで利用を支援する、という価格・価値メッセージでした。KB上では `ai-adoption-roi-and-capability-investment.md` と `agent-harness-landscape.md` に接続され、AI導入ROIが抽象的な期待値ではなく、プロダクト境界で明示的に問われ始めているシグナルとして位置づけられました。重要なのは、これは単なる値引きではなく、生成量やモデル性能よりも「顧客が吸収できる実効価値」が前面に出てきた点です。

重要ソース2本目は、NotebookLM の Source Attribution です。生成された成果物について、どのプロンプトとソースから作られたかを見せ、そこから反復できるという発表でした。KBでは `evidence-quality-and-source-trust.md` と `context-management-decisions.md` に接続され、生成物を一回限りのブラックボックス出力ではなく、来歴を持った編集可能なアーティファクトとして扱う例になっています。これは、研究OSや社内ナレッジ基盤にとってかなり大きい方向性です。要約が正しいかどうかだけでなく、「何に基づいてそう言っているのか」を作業面の中で辿れることが、再利用可能性と信頼性を左右します。

重要ソース3本目は、OpenAI の ChatGPT memory dreaming です。ChatGPT のメモリが、会話をまたいだ文脈維持や好みの更新を担う、より強い継続性システムとして説明されています。KB上では `agent-dreaming`、`company-brain`、`context-file-system`、`agent-knowledge-loop` と結びつき、記憶が隠れた内部状態ではなく、ユーザー向けのプロダクト能力として扱われる流れを補強しました。Anthropic 系の long-running harness や dreaming の話だけでなく、OpenAI 側からも「永続文脈」が明確な競争領域になっていることが見えます。

4本目の重要な補助ソースは、OpenAI Developers による Codex の Build iOS Apps plugin です。Codex の中でアプリを表示・テストし、SwiftUI previews を開き、hot reload で編集サイクルを回せるという内容です。これは `tool-accessibility`、`coding-agents`、`harness-engineering`、`workflow-compilation` に接続され、エージェントが単にコードを書く存在から、テスト・プレビュー・反復まで含む開発面を持つ方向へ進んでいることを示しています。今日の他の3本が価値、証拠、記憶の話だとすれば、このソースは実際の作業ループをどれだけエージェント内へ閉じ込められるかの話です。

更新された地図を見ると、`ai-adoption-roi-and-capability-investment.md` では Cognition の保証が「agentic PMF と価格露出」の延長として追加されました。ここでは、AI ROI はモデル品質やコード量の直接関数ではなく、内部プラットフォーム、文脈品質、信頼、検証能力、配送指標を通して初めて財務価値になる、という既存の読み筋がさらに強くなっています。Cognition の保証は、その議論をベンダー側が製品メッセージとして引き受け始めた例です。

`context-management-decisions.md` では、OpenAI の memory dreaming が、会話をまたいだ preference retention、context freshness、productized memory の例として追加されました。`evidence-quality-and-source-trust.md` では、NotebookLM の Source Attribution が、重要ソースの backfill 優先度に入っています。つまり、今日の更新は「長期記憶」と「証拠来歴」という、エージェントを実務で使うときの二大基盤を同時に進めています。片方は何を覚えるか、もう片方は何を根拠に出力したかです。

`agent-harness-landscape.md` では、OpenAI の項目に、Codex iOS app loop と ChatGPT memory が追加されました。ここでの読みどころは、OpenAI のプロダクト群が、開発環境・継続文脈・ツールアクセスをそれぞれ別の点ではなく、同じハーネス設計の要素として広げていることです。エージェントの実力はモデル単体ではなく、テストできるか、プレビューできるか、記憶できるか、根拠を示せるか、価値を測れるかによって決まるというKBの中心仮説に、今日の4本はかなりきれいに重なっています。

実務上の示唆は、AIエージェント導入を評価するときに、ライセンス費やベンチマークだけを見ても足りないということです。Devin 型のROI保証は価値測定を迫り、NotebookLM 型のソース帰属は証拠の追跡可能性を要求し、ChatGPT 型のメモリは継続文脈の管理を前面化し、Codex iOS plugin は開発ループの摩擦を減らします。これらをまとめて見ると、次の競争は「良い回答を出すAI」ではなく、「価値が説明でき、根拠を辿れ、文脈を保ち、現場のループ内で検証できるAI」に寄っています。

Podcastで掘るなら、論点は4つあります。第一に、ROI保証は本当に顧客価値を保証するのか、それとも利用量拡大のための販売メッセージなのか。第二に、ソース帰属は生成物の信頼性をどこまで改善し、どこからユーザーの検証負担になるのか。第三に、永続メモリは便利な継続性と、不要な文脈の持ち越しをどう切り分けるべきか。第四に、Codex のような開発ループ統合は、開発者を速くするだけでなく、レビューやテストの責務をどこへ移すのか。今日の更新は、エージェント時代のプロダクト設計を「能力」ではなく「運用可能性」から読むための材料でした。

## Important Sources

- Cognition / AI Productivity Guarantee: https://x.com/i/status/2062597242167628019
- NotebookLM / Source Attribution: https://x.com/NotebookLM/status/2062653124326863077
- OpenAI / ChatGPT memory dreaming: https://x.com/i/status/2062567556524003631
- OpenAI Developers / Build iOS Apps plugin in Codex: https://x.com/i/status/2062599291479478275

## Changed KB Notes

- `wiki/sources/cognition-ai-productivity-guarantee-x-2026-06-04.md`
- `wiki/sources/notebooklm-source-attribution-x-2026-06-04.md`
- `wiki/sources/openai-chatgpt-memory-dreaming-x-2026-06-04.md`
- `wiki/sources/openai-developers-build-ios-apps-plugin-codex-x-2026-06-04.md`
- `wiki/maps/ai-adoption-roi-and-capability-investment.md`
- `wiki/maps/context-management-decisions.md`
- `wiki/maps/evidence-quality-and-source-trust.md`
- `wiki/maps/agent-harness-landscape.md`


## 重要ソース

### Cognition - AI Productivity Guarantee

Source note: `wiki/sources/cognition-ai-productivity-guarantee-x-2026-06-04.md`

# Cognition - AI Productivity Guarantee

## Source Metadata
- Raw path: [[../../raw/articles/cognition-ai-productivity-guarantee-x-2026-06-04.md]]
- Original URL: https://x.com/i/status/2062597242167628019
- Primary URL: https://x.com/cognition/status/2062597242167628019/photo/1
- Author: Cognition / @cognition
- Posted: 2026-06-04T18:07:58.000Z
- Captured: 2026-06-05 via xurl bookmarks capture
- Type: X post / image card
- Evidence strength: bookmark snapshot metadata plus linked image card
- Public metrics at capture: 65 reposts, 50 replies, 665 likes, 74 quotes, 246 bookmarks, 192661 impressions

## Linked URLs
- https://x.com/i/status/2062597242167628019
- https://x.com/cognition/status/2062597242167628019/photo/1

## Bookmark text
> AI should earn its keep.

## What it says
Cognition is marketing Devin with an explicit productivity guarantee: if the product does not deliver enough engineering value relative to the spend, the company says it will fund usage until it does, up to $10 million.

## Why it matters
This makes the ROI conversation part of the product itself. The post is useful as a vendor-side signal that AI tooling is moving from feature claims to outcome claims.

## Related concepts
- [[../concepts/ai-adoption-j-curve.md]]
- [[../concepts/agentic-product-market-fit.md]]
- [[../concepts/verification-tax.md]]
- [[../concepts/agent-deployment-gates-and-operational-risk.md]]

## Related maps
- [[../maps/ai-adoption-roi-and-capability-investment.md]]
- [[../maps/agent-harness-landscape.md]]

## Backlinks
- [[../../raw/articles/cognition-ai-productivity-guarantee-x-2026-06-04.md]]

### NotebookLM - Source attribution

Source note: `wiki/sources/notebooklm-source-attribution-x-2026-06-04.md`

# NotebookLM - Source attribution

## Source Metadata
- Raw path: [[../../raw/articles/notebooklm-source-attribution-x-2026-06-04.md]]
- Original URL: https://x.com/NotebookLM/status/2062653124326863077
- Primary URL: https://x.com/NotebookLM/status/2062653124326863077/video/1
- Author: NotebookLM
- Posted: 2026-06-04T21:50:01.000Z
- Captured: 2026-06-05 via xurl bookmarks capture
- Type: X post / video card
- Evidence strength: bookmark snapshot metadata plus linked video card
- Public metrics at capture: 41 reposts, 11 replies, 352 likes, 4 quotes, 106 bookmarks, 12409 impressions

## Linked URLs
- https://x.com/NotebookLM/status/2062653124326863077
- https://x.com/NotebookLM/status/2062653124326863077/video/1

## Bookmark text
> No more guessing.

## What it says
NotebookLM is adding Source Attribution so users can see the exact prompts and sources used to create each artifact and then iterate on it.

## Why it matters
This is a strong provenance and evidence-quality signal. It mirrors the KB's own interest in making source lineage visible instead of burying it in hidden context.

## Related concepts
- [[../concepts/evidence-quality.md]]
- [[../concepts/compiled-wiki.md]]
- [[../concepts/agent-knowledge-loop.md]]
- [[../concepts/rich-agent-output-artifact.md]]

## Related maps
- [[../maps/evidence-quality-and-source-trust.md]]
- [[../maps/context-management-decisions.md]]

## Backlinks
- [[../../raw/articles/notebooklm-source-attribution-x-2026-06-04.md]]

### OpenAI - ChatGPT memory dreaming

Source note: `wiki/sources/openai-chatgpt-memory-dreaming-x-2026-06-04.md`

# OpenAI - ChatGPT memory dreaming

## Source Metadata
- Raw path: [[../../raw/articles/openai-chatgpt-memory-dreaming-x-2026-06-04.md]]
- Original URL: https://x.com/i/status/2062567556524003631
- Primary URL: https://openai.com/index/chatgpt-memory-dreaming/
- Author: OpenAI / @OpenAI
- Posted: 2026-06-04T16:10:00.000Z
- Captured: 2026-06-05 via xurl bookmarks capture
- Type: X post / company announcement
- Evidence strength: bookmark snapshot metadata plus linked official announcement
- Public metrics at capture: 644 reposts, 402 replies, 6638 likes, 310 quotes, 1794 bookmarks, 960796 impressions

## Linked URLs
- https://x.com/i/status/2062567556524003631
- https://openai.com/index/chatgpt-memory-dreaming/

## Bookmark text
> more capable memory system in ChatGPT

## What it says
OpenAI says ChatGPT memory is being upgraded to better carry context across conversations and remember preferences in a way that stays fresh and relevant.

## Why it matters
This is a product-level memory and continuity signal. It belongs next to the repo's memory, company-brain, and dreaming sources because it treats persistent context as an explicit user-facing capability.

## Related concepts
- [[../concepts/agent-dreaming.md]]
- [[../concepts/company-brain.md]]
- [[../concepts/context-file-system.md]]
- [[../concepts/agent-knowledge-loop.md]]

## Related maps
- [[../maps/context-management-decisions.md]]
- [[../maps/agent-harness-landscape.md]]

## Backlinks
- [[../../raw/articles/openai-chatgpt-memory-dreaming-x-2026-06-04.md]]

### OpenAI Developers - Build iOS Apps plugin in Codex

Source note: `wiki/sources/openai-developers-build-ios-apps-plugin-codex-x-2026-06-04.md`

# OpenAI Developers - Build iOS Apps plugin in Codex

## Source Metadata
- Raw path: [[../../raw/articles/openai-developers-build-ios-apps-plugin-codex-x-2026-06-04.md]]
- Original URL: https://x.com/i/status/2062599291479478275
- Primary URL: https://x.com/OpenAIDevs/status/2062599291479478275/video/1
- Author: OpenAI Developers / @OpenAIDevs
- Posted: 2026-06-04T18:16:06.000Z
- Captured: 2026-06-05 via xurl bookmarks capture
- Type: X post / video card
- Evidence strength: bookmark snapshot metadata plus linked video card
- Public metrics at capture: 326 reposts, 154 replies, 4817 likes, 170 quotes, 2510 bookmarks, 417911 impressions

## Linked URLs
- https://x.com/i/status/2062599291479478275
- https://x.com/OpenAIDevs/status/2062599291479478275/video/1

## Bookmark text
> More of the iOS app loop, now inside Codex.

## What it says
The Build iOS Apps plugin lets Codex view and test an iOS app inside the in-app browser, open SwiftUI previews, and hot reload edits without leaving Codex.

## Why it matters
This is a good example of tool accessibility moving deeper into the agent surface. The product is absorbing more of the edit-test loop instead of forcing the developer back to separate tools.

## Related concepts
- [[../concepts/tool-accessibility.md]]
- [[../concepts/coding-agents.md]]
- [[../concepts/harness-engineering.md]]
- [[../concepts/workflow-compilation.md]]

## Related maps
- [[../maps/agent-harness-landscape.md]]
- [[../maps/harness-engineering-vendor-comparison.md]]

## Backlinks
- [[../../raw/articles/openai-developers-build-ios-apps-plugin-codex-x-2026-06-04.md]]

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

### AI Adoption ROI and Capability Investment

KB note: `wiki/maps/ai-adoption-roi-and-capability-investment.md`

# AI Adoption ROI and Capability Investment

## Purpose
Map how AI-assisted software development becomes financial value only when capability investments let the organization absorb faster generation safely.

## Core thesis
AI ROI is not a direct function of model quality or code volume. It is a system outcome: AI adoption must be mediated by internal platforms, context/data quality, trust, user focus, verification guardrails, and delivery metrics before it can become durable business value. The strongest upside case is not only cheaper execution of existing backlog, but Jevons-style expansion in software demand when new tools, experiments, and automations become economical.

## Path from AI adoption to ROI

### 1. Capability investment first
The first question is not “which tool?” but “can the system absorb the tool?” DORA's report emphasizes quality internal developer platforms, AI-accessible internal data, clear AI stance/trust, context engineering, user-centric focus, and automated

### Context Management Decision Map

KB note: `wiki/maps/context-management-decisions.md`

# Context Management Decision Map

## Purpose
Compare the main recovery and continuity moves available to long-running agent systems.

## Core moves

### Continue
- Keep the current session and context as-is.
- Best when the session is still coherent and the next task is closely related.

### Rewind
- Remove a failed branch and restart from the last good point.
- Best when the current line of reasoning is clearly wrong but the session still has useful surrounding state.

### Clear
- Explicitly wipe the session context and start over from artifacts.
- Best when the human wants tight control over what remains visible.

### Compact
- Condense the current session into a shorter summary.
- Best when the work is still relevant but the raw history is too large or noisy.

### Delegate
- Spawn a subagent or separate worker for a noisy or specialized subtask.
- Best when the subtask should not pollute the parent context.

### Reset
- Rebuild state from explicit handoff artifacts in a fresh sessi

### Evidence Quality and Source Trust

KB note: `wiki/maps/evidence-quality-and-source-trust.md`

# Evidence Quality and Source Trust

## Purpose
Turn the KB from a flat summary collection into a research OS that can reason about claim strength, provenance, and safe reuse.

## Core thesis
The wiki should not only answer "what does this source say?" It should answer "how much should we trust this source for this specific claim, and what can it safely support?"

## Evidence tiers

### Tier 1: Direct primary evidence
Use for definitions, product behavior, and hard constraints.
- official docs
- source repositories
- papers with clear methods
- reproducible examples or code

Typical confidence: high, unless the capture is partial or outdated.

### Tier 2: Practitioner operational evidence
Use for workflow patterns, heuristics, and lived failure modes.
- first-person engineering reports
- postmortems
- detailed implementation notes
- Masaki operation notes

Typical confidence: medium to high for "this pattern worked in this setting," lower for broad generalization.

### Tier 3: Public s

## NotebookLM Podcast用メモ

- まず今日の全体トレンドを話してから、重要ソースを3本に絞って深掘りする。
- ソース単体の紹介で終わらせず、既存KBの概念や地図がどう更新されたかを会話に含める。
- 最後に、明日以降の調査問いを2〜3個提示する。
