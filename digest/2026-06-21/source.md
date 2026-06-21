<!-- generated: 2026-06-21T13:02:18.109159+00:00 -->
<!-- kb_daily_digest_date: 2026-06-21 -->
# KB Daily Digest Source — 2026-06-21

このページは、knowledge-base-llm の日次更新を NotebookLM に読み込ませるための公開向けソースページです。
Discord通知よりも文脈を厚めに残し、Podcast化しやすいように、今日追加・更新されたソース、概念、地図を文章中心で整理します。

## 今日の全体像

# KB Daily Digest 2026-06-21

UTC 2026-06-21 の knowledge-base-llm 更新は、X bookmark ingest 由来の新規ソース2本と、それに伴う概念・地図の小さめだが意味のある更新だった。新規 raw は `raw/articles/aiclambake-ai-engineer-claims-to-have-cracked-linear-a-2026-06-16.md` と `raw/articles/microsoft-presidio-pii-detection-sdk-x-2026-06-18.md`。新規 wiki source は `wiki/sources/aiclambake-ai-engineer-claims-to-have-cracked-linear-a-2026-06-16.md` と `wiki/sources/microsoft-presidio-pii-detection-sdk-x-2026-06-18.md`。概念側では `agent-safety`、`evidence-quality`、`middleware-controls`、`self-verification` が更新され、地図側では `agent-harness-landscape` に「model input 前の data redaction / PII filtering」が control of autonomy の一部として追加された。

全体トレンドは、agent harness を「賢いモデルをうまく使うための作業環境」から、より明示的な検証・安全・前処理のレイヤーとして見る方向に寄っている。Linear A の話は、Claude Code を使った corpus query / cross-reference / lexicon creation という研究支援ワークフローとして面白い一方、主張そのものは専門家レビュー待ちであり、KBでは evidence-quality と self-verification の例として扱うのが妥当だ。Presidio の話は反対に、主張の新規性よりも実務上の再利用性が強い。PII を model call の前で検出・匿名化するという形は、prompt や model behavior に安全性を押し込めるのではなく、middleware control としてリスクを分離する設計を補強する。

重要ソースの1本目は AI Clambake の「AI Engineer Claims to Have Cracked Linear A」。記事は Tom Di Mino による Linear A decipherment claim を紹介し、Claude Code が digitized corpus を検索・照合・整理する Python scripts の構築に使われたと説明している。KB上での読みどころは、「AIが古代文字を解読した」という見出しではなく、AI coding agent が研究用 corpus に対する仮説検証の作業台になっている点だ。ソースノートでは evidence strength を medium-low とし、Rutgers や Cambridge の専門家レビューが進行中であること、記事自体に cautionary edit note があることを明示した。これは、魅力的なAI-assisted research storyをKBに入れるときに、検証前の主張と再現可能な作業フローを分けて扱うためのよい事例になる。

重要ソースの2本目は Microsoft Presidio の PII detection / anonymization SDK。X投稿は短いが、GitHub と公式ドキュメントが示す通り、Presidio は names、emails、SSNs、credit cards、medical records などの sensitive data を検出・redact・mask・anonymize するための data-protection / de-identification framework として位置づけられている。KBでは、これは `agent-safety` と `middleware-controls` に接続された。特に重要なのは、PII対策を「モデルが漏らさないようにする」だけではなく、「モデルに渡す前に入力経路で変換する」制御として扱えることだ。agent が多くの外部ツールや業務データに触れるほど、こうした前段の共通部品は prompt discipline より監査しやすく、再利用もしやすい。

重要ソースの3本目は単独の新規記事ではなく、今回更新された `agent-harness-landscape` 自体だ。これまで landscape は guidance before action、correction after action、continuity、autonomy control、role separation という軸で agent harness を整理していた。今回、autonomy control の項目に data redaction / PII filtering before model input が加わったことで、権限承認や human-in-the-loop だけでなく、入力データの安全な整形も autonomy control の構成要素として扱う方向が明確になった。これは小さな1行追加に見えるが、今後 enterprise connector、personal agent、RAG、tool-calling workflow を読むときの基準になる。

概念更新の意味は、二つのソースがKBの別々の弱点を補ったことにある。Linear A ソースは `evidence-quality` と `self-verification` に入り、AIを使った研究支援が「面白いが未確定」な段階にあるとき、どのように強さを評価するかを示した。Presidio ソースは `agent-safety` と `middleware-controls` に入り、agent安全性を model alignment の抽象論だけにせず、入力経路に置ける具体的なソフトウェア部品として示した。どちらも agent harness の話だが、片方は知識の信頼性、もう片方はデータ境界の安全性を扱っている。

実務上の示唆は、AI導入の判断では「その主張は本当に正しいのか」と「失敗しても被害が広がらない構造になっているか」を別々に見る必要があるということだ。Linear A のような研究 claim は、生成された artifacts、corpus、scripts、外部レビュー、反証可能性を揃えて初めて強い根拠になる。Presidio のような middleware は、モデルの応答品質とは独立に、名前やメールや医療情報がLLM pipelineへ素通りする危険を下げられる。ただし anonymization が downstream reasoning に必要な文脈を壊す場合もあるので、semantic fidelity、構造化データ、画像や添付ファイルの扱いは別途設計が必要になる。

Podcastで掘るなら、今日は「agent harness は検証装置でもあり、安全装置でもある」というテーマがよい。前半で Linear A の事例を使い、Claude Code が研究者の作業をどこまで助け、どこから先は専門家レビューが必要なのかを話す。後半で Presidio を使い、PII redaction を prompt のお願いではなく pipeline の middleware として置く意味を話す。最後に、KBの地図更新として、autonomy control が承認や権限だけでなく、入力データの整形・匿名化まで含むようになったことを確認すると、今日の2本が一本の流れとしてつながる。

次に追う問いは、Linear A claim の peer review 結果や再現性、Claude Code が生成した scripts / lexicon / manuscript の公開範囲、Presidio を agent toolchain に入れたときの検出漏れ・過剰redaction・多言語対応、そしてPII以外の機密情報を同じ middleware pattern で扱えるかどうかの4つ。今日の更新は量としては小さいが、KBの読み方としては重要で、「AIが何を可能にしたか」と同じくらい「どの段階で検証し、どの経路で安全にするか」を前面に出している。

公開HTML: https://makikub.github.io/kb-notebooklm-podcast/digest/2026-06-21/

NotebookLM用 source.md: https://makikub.github.io/kb-notebooklm-podcast/digest/2026-06-21/source.md


## 重要ソース

### AI Clambake - AI Engineer Claims to Have Cracked Linear A

Source note: `wiki/sources/aiclambake-ai-engineer-claims-to-have-cracked-linear-a-2026-06-16.md`

# AI Clambake - AI Engineer Claims to Have Cracked Linear A

## Source Metadata
- Raw path: [[../../raw/articles/aiclambake-ai-engineer-claims-to-have-cracked-linear-a-2026-06-16.md]]
- Original URL: https://x.com/i/status/2068064304503660962
- Shared article URL: https://aiclambake.com/clamtakes/linear-a/
- X post author: Boris Cherny (@bcherny)
- Article date: 2026-06-16
- X post date: 2026-06-19T20:12:07.000Z
- Type: article / X bookmark
- Evidence strength: medium-low; the article is detailed, but the core decipherment claim is explicitly still under peer review
- Capture source: xurl bookmarks capture

## Summary
AI Clambake reports on Tom Di Mino's claim that Linear A can be decoded as an extinct Semitic language. The article says the work is being reviewed by linguistics experts and highlights that Claude Code was used to build Python scripts for querying, cross-referencing, and organizing the digitized corpus.

## Key Claims
- Claude Code can be used as a research workflow engine for corpus-driven hypothesis testing.
- The claimed Linear A decipherment is not settled; review by specialists is still pending.
- The workflow produced a larger artifact set, including a lexicon and draft manuscript.

## Evidence / Examples
- The article explicitly states that Claude Code was used to build scripts around the Linear A corpus.
- The article also states that the claim is under review by Rutgers and Cambridge experts.
- The article includes a cautionary edit note, which is a useful signal that the story may evolve.

## Why It Matters
This source is a good evidence-quality example. It shows how a compelling AI-assisted research claim can be paired with explicit caveats, external review, and a reproducible data workflow. That combination is more useful to the KB than the cl

### Microsoft Presidio - PII detection and anonymization SDK

Source note: `wiki/sources/microsoft-presidio-pii-detection-sdk-x-2026-06-18.md`

# Microsoft Presidio - PII detection and anonymization SDK

## Source Metadata
- Raw path: [[../../raw/articles/microsoft-presidio-pii-detection-sdk-x-2026-06-18.md]]
- Original URL: https://x.com/i/status/2067543602302230576
- Author: Vaishnavi (@_vmlops)
- Date: 2026-06-18
- Type: X post / product mention
- Evidence strength: moderate; the bookmark text is terse, but the project docs are explicit about the SDK's purpose
- Capture source: xurl bookmarks capture
- Primary URLs:
  - https://github.com/microsoft/presidio
  - https://microsoft.github.io/presidio/

## Summary
Microsoft Presidio is an open-source SDK for detecting, redacting, masking, and anonymizing PII. The bookmark frames it as a way to keep sensitive data out of LLM pipelines before model input is ever processed.

## Key Claims
- PII detection belongs in the input path, not only in downstream review.
- Anonymization/redaction can be treated as a reusable middleware control.
- Text pipelines carrying names, emails, SSNs, credit cards, or medical records need a dedicated safety layer.

## Evidence / Examples
- The tweet explicitly says Presidio detects and anonymizes sensitive data before it reaches the model.
- The official Presidio docs and GitHub repo describe the SDK as a data-protection and de-identification framework.

## Why It Matters
This is a concrete example of an agent-safety control that does not depend on the model becoming better behaved. It shifts one class of risk into a pre-model normalization step, which is easier to audit and reuse across prompts, tools, and agent surfaces.

## Related Concepts
- [[../concepts/agent-safety.md]]
- [[../concepts/middleware-controls.md]]
- [[../concepts/harness-engineering.md]]
- [[../concepts/feedback-controls.md]]

## Open Questions
- How much semantic f

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

### Evidence Quality

KB note: `wiki/concepts/evidence-quality.md`

---
aliases:
  - Evidence Quality
  - Source Trust
---

# Evidence Quality

## Definition
Evidence quality is the explicit confidence layer attached to a source note or synthesis claim: what kind of source it is, how directly it supports a claim, what limitations apply, and which concepts it can safely support.

## Why It Matters
A compiled wiki becomes dangerous when all notes look equally authoritative. Evidence quality lets the KB distinguish primary docs, research papers, implementation repos, practitioner reports, product announcements, social threads, and speculative synthesis before those notes are reused in maps or answers.

## Operational Fields
Use these fields when a source anchors an important concept or map:
- Source type: primary docs, official blog, paper, repository, practitioner report, X thread, second-order summary, internal operation note, speculative synthesis.
- Confidence: high / medium / low.
- Supports: concepts or map claims the source can directly support.
- 

### Middleware Controls

KB note: `wiki/concepts/middleware-controls.md`

---
aliases:
  - Middleware Controls
---

# Middleware Controls

## Definition
Hooks or interception layers around model and tool calls that can inject context, apply checks, or alter execution flow.

## Why It Matters
They offer a flexible way to shape behavior without changing the underlying model.

## Related Concepts
- [[feedback-controls]]
- [[self-verification]]
- [[harness-engineering]]
- [[agent-safety]]

## Supporting Sources
- [[../sources/langchain-deep-agents-harness-engineering.md]]
- [[../sources/arxiv-skill-rag-failure-state-aware-retrieval.md]]
- [[../sources/microsoft-presidio-pii-detection-sdk-x-2026-06-18.md]]

## Tradeoffs / Tensions
- Too much middleware can make behavior hard to reason about.
- Middleware-specific heuristics may age poorly as models improve.

## Open Questions
- Which middleware controls generalize across agent types?
- When should hidden-state diagnostics or skill routing sit in middleware rather than inside the base prompt loop?

### Self-Verification

KB note: `wiki/concepts/self-verification.md`

---
aliases:
  - Self-Verification
---

# Self-Verification

## Definition
A pattern in which an agent explicitly checks its work against external tests, task requirements, or runtime evidence before declaring completion.

## Why It Matters
Agents often stop too early or trust their own code reading too much. Verification creates a correction loop.

## Related Concepts
- [[feedback-controls]]
- [[task-decomposition]]
- [[trace-driven-improvement]]
- [[heavy-thinking.md]]

## Supporting Sources
- [[../sources/arxiv-social-meta-learning-language-feedback.md]]
- [[../sources/arxiv-heavyskill-heavy-thinking.md]]
- [[../sources/langchain-deep-agents-harness-engineering.md]]
- [[../sources/mitchell-hashimoto-ai-adoption-journey.md]]
- [[../sources/openai-codex-plugin-cc-github.md]]
- [[../sources/openai-codex-plugin-cc-x.md]]
- [[../sources/anthropic-claude-mythos-preview.md]]
- [[../sources/anthropic-dynamic-skill-context-x.md]]
- [[../sources/storybook-mcp-react-blog.md]]
- [[../sources/di

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
