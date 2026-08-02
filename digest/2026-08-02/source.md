<!-- generated: 2026-08-02T13:02:00.261507+00:00 -->
<!-- kb_daily_digest_date: 2026-08-02 -->
# KB Daily Digest Source — 2026-08-02

このページは、knowledge-base-llm の日次更新を NotebookLM に読み込ませるための公開向けソースページです。
Discord通知よりも文脈を厚めに残し、Podcast化しやすいように、今日追加・更新されたソース、概念、地図を文章中心で整理します。

## 今日の全体像

# KB Daily Digest 2026-08-02

2026-08-02 UTC の knowledge-base-llm 更新は、X bookmarks batch から3本の source note が新規追加され、2つの map が更新された日でした。新規 raw は `raw/x/bookmarks/bookmarks-20260802T0000Z.json` と、GPT-5.6 routing、PDF routing、GPT-5.6 pricing に関する3本の article note です。wiki 側には `daniel_mac8-sol-advisor-gpt-56-routing-x-2026-08-01.md`、`nickscamara-pdf-inspector-fast-pdf-routing-x-2026-07-31.md`、`openai-gpt-56-pricing-update-luna-terra-fast-sol-x-2026-07-30.md` が追加され、`agent-harness-landscape` と `ai-adoption-roi-and-capability-investment` が更新されました。

今日の全体トレンドは、「モデルを選ぶ」から「モデル・前処理・実行経路を組み合わせて routing する」への移行です。OpenAI の価格/速度更新、Dan McAteer の Sol/Luna/Terra 使い分け、Nicolas Camara の `pdf-inspector` は別々の話題に見えますが、KB では同じ設計論に接続します。高いモデルに全部を投げるのではなく、どの入力をどの処理経路へ流すかを harness 側で決めることが、コスト、レイテンシ、品質、レビュー負荷を左右するという読みです。

重要ソース1本目は OpenAI の GPT-5.6 pricing update です。公式 X post として、GPT-5.6 Luna が80%安くなり、GPT-5.6 Terra が20%安くなり、GPT-5.6 Sol にはより速い API option が出る、という一次情報として扱えます。KB 上では `ai-roi-model`、`llm-inference-performance`、`worker-based-composition`、`agentic-jevons-paradox` に接続されました。ポイントは値下げそのものだけではなく、モデルファミリー内で cost/speed/capability の差が明示的な routing surface になってきたことです。

重要ソース2本目は Dan McAteer の "sol-advisor" routing pattern です。GPT-5.6 Sol High を orchestrator、Luna Max を routine implementation、Terra Max を more complex implementation に使うという実践的な分担案で、評価データや詳細な policy はまだ捕捉されていませんが、モデル tier を composition system として扱う具体例になっています。OpenAI の価格更新と合わせて読むと、安くなった worker tier と速くなった orchestrator tier をどう組ませるか、という実務上の問いが立ち上がります。

重要ソース3本目は Nicolas Camara の `pdf-inspector` です。Rust library として PDF inspection、classification、text extraction を行い、PDF が scanned か text-based かを高速に判定して、OCR など重い処理へ進む前に経路を分けられる、という主張が捕捉されています。200 PDFs を2.8秒で処理したという具体例もあり、KB では `llm-inference-performance`、`feedback-controls`、`task-decomposition`、`harness-engineering`、`evidence-quality` に接続されました。こちらはモデル routing ではなく document pipeline routing ですが、発想は同じです。

`agent-harness-landscape` の更新では、GPT-5.6 family の価格と routing が harness 設計の一部として追加されました。これまでの地図は、repo 構造、tests、review loops、memory、tool surface、cloud runtime といった周辺設計を中心に扱っていましたが、今回の更新で「どの model tier にどの役割を持たせるか」も同じ harness 問題としてはっきり入りました。さらに `pdf-inspector` は agentic fetch/extraction の枝に加わり、agent が読む前の軽量な分類・抽出も harness primitive として位置づけられました。

`ai-adoption-roi-and-capability-investment` では、GPT-5.6 の価格更新と sol-advisor pattern が ROI モデルに追加されました。Luna/Terra が安くなると、これまで高コストで見送っていた routine implementation や parallel worker execution が現実的になる可能性があります。一方で、安くなったからといって自動的に ROI が出るわけではありません。安い worker を増やすほど review capacity、verification tax、instability tax も増えうるため、価格低下は「使えば得」ではなく「routing と検証を設計すれば投資余地が増える」と読むのが安全です。

実務上の示唆は、agent harness の設計単位が少し細かくなってきたことです。コード作業なら、Sol のような上位モデルに plan/review/orchestration を寄せ、Luna/Terra のような worker tier に routine/complex implementation を振り分ける。文書処理なら、PDF をいきなり OCR/LLM に投げず、先に scanned/text-based を判定して cheap path と expensive path を分ける。どちらも、入口で分類し、仕事を分解し、処理ごとの期待値とコストを変えるという同じ control loop です。

Podcast で掘るなら、まず「価格改定は単なる節約ニュースではなく、agent 設計の選択肢を増やすニュースである」という観点から始めるとよさそうです。次に、sol-advisor を例に model-tier orchestration の具体像を話し、最後に `pdf-inspector` を並べて「入力を読む前に route する」ことの価値へ広げられます。議論の中心は、強いモデルをどう使うかではなく、強いモデルに任せる前に何を切り分け、安い worker やローカル前処理でどこまで済ませるか、です。

次に追うべき問いは3つあります。まず、Sol/Luna/Terra の routing criteria をどう測るのか。難易度、uncertainty、blast radius、review cost のどれを使うべきか。次に、PDF routing のような軽量 classifier は、実データでどの程度誤判定し、その誤判定が downstream の品質とコストにどのくらい効くのか。最後に、価格低下で task volume が増えたとき、review と eval の capacity をどう先回りして増やすべきか、です。

## Important Sources

- `https://x.com/i/status/2082878156483219672`
- `https://x.com/i/status/2083607027813662810`
- `https://x.com/i/status/2083295265793212827`
- `https://github.com/firecrawl/pdf-inspector`

## New / Changed Files

- `raw/x/bookmarks/bookmarks-20260802T0000Z.json`
- `raw/articles/daniel_mac8-sol-advisor-gpt-56-routing-x-2026-08-01.md`
- `raw/articles/nickscamara-pdf-inspector-fast-pdf-routing-x-2026-07-31.md`
- `raw/articles/openai-gpt-56-pricing-update-luna-terra-fast-sol-x-2026-07-30.md`
- `wiki/sources/daniel_mac8-sol-advisor-gpt-56-routing-x-2026-08-01.md`
- `wiki/sources/nickscamara-pdf-inspector-fast-pdf-routing-x-2026-07-31.md`
- `wiki/sources/openai-gpt-56-pricing-update-luna-terra-fast-sol-x-2026-07-30.md`
- `wiki/INDEX.md`
- `wiki/maps/agent-harness-landscape.md`
- `wiki/maps/ai-adoption-roi-and-capability-investment.md`


## 重要ソース

### Dan McAteer - sol-advisor for GPT-5.6 routing

Source note: `wiki/sources/daniel_mac8-sol-advisor-gpt-56-routing-x-2026-08-01.md`

# Dan McAteer - sol-advisor for GPT-5.6 routing

## Source Metadata
- Raw path: `../../raw/articles/daniel_mac8-sol-advisor-gpt-56-routing-x-2026-08-01.md`
- Raw bookmark capture: `../../raw/x/bookmarks/bookmarks-20260802T0000Z.json`
- Original URL: https://x.com/i/status/2083607027813662810
- Referenced X URL: https://twitter.com/daniel_mac8/status/2083218469680549930
- Linked media URL: https://x.com/daniel_mac8/status/2083607027813662810/video/1
- Author: Dan McAteer (@daniel_mac8)
- Posted: 2026-08-01T17:33:21.000Z
- Captured: 2026-08-02T00:00:27.089Z via xurl bookmarks capture
- Type: X post / routing pattern
- Evidence strength: medium; the bookmark gives a concrete routing heuristic but does not explain the full decision policy
- Public metrics at capture: 1378 likes, 98 reposts, 38 replies, 7 quotes, 2560 bookmarks, 144750 impressions

## Summary
Dan McAteer proposes "sol-advisor" as a practical tiered-model routing pattern: GPT-5.6 Sol High orchestrates the work, GPT-5.6 Luna Max handles routine implementation, and GPT-5.6 Terra Max handles more complex implementation. The useful signal is that the model family is being treated as a composition system rather than as a single monolithic choice.

## Key Claims
- GPT-5.6 Sol High can act as an orchestrator.
- GPT-5.6 Luna Max can be used for routine implementation tasks.
- GPT-5.6 Terra Max can be used for more complex implementation tasks.
- The overall pattern is explicitly framed as a way to take advantage of GPT-5.6 efficiency and capability.

## Evidence / Examples
- The bookmark text names the three roles directly.
- The attached X video suggests the author is demonstrating the routing pattern rather than merely discussing it abstractly.
- The referenced X post may provide the larger context, but this note s

### Nicolas Camara - pdf-inspector for fast PDF routing

Source note: `wiki/sources/nickscamara-pdf-inspector-fast-pdf-routing-x-2026-07-31.md`

# Nicolas Camara - pdf-inspector for fast PDF routing

## Source Metadata
- Raw path: `../../raw/articles/nickscamara-pdf-inspector-fast-pdf-routing-x-2026-07-31.md`
- Raw bookmark capture: `../../raw/x/bookmarks/bookmarks-20260802T0000Z.json`
- Original URL: https://x.com/i/status/2083295265793212827
- Primary URL: https://github.com/firecrawl/pdf-inspector
- Linked media URL: https://x.com/nickscamara_/status/2083295265793212827/photo/1
- Author: Nicolas Camara (@nickscamara_)
- Posted: 2026-07-31T20:54:31.000Z
- Captured: 2026-08-02T00:00:27.089Z via xurl bookmarks capture
- Type: X post / GitHub repo highlight
- Evidence strength: medium-high; the post includes a specific repo card and concrete performance claims, but this note does not inspect the repo contents directly
- Public metrics at capture: 6128 likes, 445 reposts, 152 replies, 74 quotes, 11924 bookmarks, 1001890 impressions

## Summary
Nicolas Camara's bookmark highlights `pdf-inspector`, a Rust library for PDF inspection, classification, and text extraction. The operationally interesting part is the claim that it can quickly classify PDFs as scanned or text-based so the pipeline can choose a cheaper path before OCR or other heavier extraction work.

## Key Claims
- `pdf-inspector` is a Rust library for PDF inspection, classification, and text extraction.
- It can detect scanned versus text-based PDFs quickly, around the 20 ms range.
- It extracts markdown locally and is framed as helping agents avoid waiting on OCR.
- The repo card claims strong table and graph extraction quality.

## Evidence / Examples
- The bookmark text states the classification and local extraction claims directly.
- The GitHub repo card title reinforces that the project is about PDF inspection and text extraction.
- The post include

### OpenAI - GPT-5.6 pricing update and faster Sol API option

Source note: `wiki/sources/openai-gpt-56-pricing-update-luna-terra-fast-sol-x-2026-07-30.md`

# OpenAI - GPT-5.6 pricing update and faster Sol API option

## Source Metadata
- Raw path: `../../raw/articles/openai-gpt-56-pricing-update-luna-terra-fast-sol-x-2026-07-30.md`
- Raw bookmark capture: `../../raw/x/bookmarks/bookmarks-20260802T0000Z.json`
- Original URL: https://x.com/i/status/2082878156483219672
- Linked media URL: https://x.com/OpenAI/status/2082878156483219672/photo/1
- Author: OpenAI (@OpenAI)
- Posted: 2026-07-30T17:17:05.000Z
- Captured: 2026-08-02T00:00:27.089Z via xurl bookmarks capture
- Type: X post / pricing update
- Evidence strength: high for the pricing announcement, medium for broader interpretation without the linked product page
- Public metrics at capture: 18427 likes, 1873 reposts, 1201 replies, 1788 quotes, 2599 bookmarks, 10682320 impressions

## Summary
OpenAI says GPT-5.6 Luna becomes 80 percent cheaper, GPT-5.6 Terra becomes 20 percent cheaper, and GPT-5.6 Sol gets a faster API option. The note is useful because it shows model family tiering as an active cost and speed control surface.

## Key Claims
- GPT-5.6 Luna prices are being reduced by 80 percent.
- GPT-5.6 Terra prices are being reduced by 20 percent.
- A faster GPT-5.6 Sol option is being offered in the API.
- OpenAI is explicitly tying the update to cost efficiency, capability, and speed.

## Evidence / Examples
- The bookmark text states the price changes directly.
- The tweet is an official OpenAI product post, so the pricing and API-option claims are first-party.
- The visible card suggests a product announcement rather than a casual commentary thread.

## Evidence Quality
- Source type: official OpenAI X post
- Confidence: high for the pricing changes and fast-Sol API signal, medium for any inferred product-strategy implications
- Supports: [[../concepts/ai-roi-mode

## 更新された概念・地図

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

## NotebookLM Podcast用メモ

- まず今日の全体トレンドを話してから、重要ソースを3本に絞って深掘りする。
- ソース単体の紹介で終わらせず、既存KBの概念や地図がどう更新されたかを会話に含める。
- 最後に、明日以降の調査問いを2〜3個提示する。
