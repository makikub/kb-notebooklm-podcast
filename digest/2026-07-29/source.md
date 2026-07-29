<!-- generated: 2026-07-29T13:02:13.832789+00:00 -->
<!-- kb_daily_digest_date: 2026-07-29 -->
# KB Daily Digest Source — 2026-07-29

このページは、knowledge-base-llm の日次更新を NotebookLM に読み込ませるための公開向けソースページです。
Discord通知よりも文脈を厚めに残し、Podcast化しやすいように、今日追加・更新されたソース、概念、地図を文章中心で整理します。

## 今日の全体像

# KB Daily Digest 2026-07-29

2026-07-29 UTC の knowledge-base-llm 更新は、X bookmark の新規取り込みと、Anthropic / Claude の Skills 関連一次情報を中心にした追加コンパイルが重なった日でした。新規 raw は `raw/x/bookmarks/bookmarks-20260729T0000Z.json`、OpenAI Voice / Apple SpeechAnalyzer / OpenAI Codex Security の記事ノート、さらに Anthropic の Skills PDF、Agent Skills engineering blog、Claude Skills 解説、Claude Code チームの skills 運用記事です。wiki 側では `wiki/sources/` に7本の新規 source note が追加され、`agent-harness-landscape`、`coding-agent-harness-patterns`、`eval-review-reliability`、`evidence-quality-and-source-trust` などの地図にも反映されました。

今日の全体トレンドは、「エージェントの能力を上げる」という話が、モデル単体ではなく、再利用可能な手順、音声やデスクトップの操作面、セキュリティ検査、CI、証拠品質までを含む harness design の話に寄っていることです。特に Anthropic / Claude の Skills 系ソースは、プロンプトを毎回頑張るのではなく、手順・ツール・参照資料・スクリプトをフォルダとして保存し、必要なときだけ読み込ませる「progressive disclosure」を強く支える更新でした。

重要ソース1本目は、Anthropic の公式PDF `The Complete Guide to Building Skills for Claude` です。KBでは、Skills の用途を「document and asset creation」「workflow automation」「MCP enhancement」に分ける実務的な分類として取り込みました。ここで大事なのは、MCP が外部サービスへの接続を与える一方で、Skills はその接続をどう使うかという業務知識や判断手順を持つ、という役割分担です。これは単なる Claude 専用機能の説明ではなく、agent harness 全体における reusable workflow packaging の設計原則として使えます。

重要ソース2本目は、Anthropic engineering blog `Equipping agents for the real world with Agent Skills` です。このノートは、Skills を「instructions, scripts, resources を含む composable folder」として整理し、最初に小さなメタデータだけを見せ、必要になったときに `SKILL.md` や deeper files、実行スクリプトを読むという progressive disclosure を中心概念として扱っています。KBの `navigable-agent-skills`、`memory-skill-harness`、`context-file-system` の枝にとって、かなり基礎的な参照点になります。

重要ソース3本目は、Claude Code チームの記事 `Lessons from building Claude Code: How we use skills` です。ここでは Anthropic 内部で hundreds of skills を運用している経験から、9種類の skill type が示されました。特に `Library and API reference`、`Product verification`、`Code quality and review`、`Runbooks`、`Infrastructure operations` は、今後 KB 側で「どのスキルを作るべきか」を棚卸しするときの分類軸として使いやすいです。さらに、verification skills が内部的に品質改善へ大きく効いたという主張は、`eval-review-reliability` と `verification-harness` の実務寄りな根拠になります。

X bookmark 側では、OpenAI の ChatGPT Voice desktop app と Apple SpeechAnalyzer が、音声を単なる会話入力ではなく agent control surface として扱う方向を補強しました。OpenAI の投稿は、デスクトップアプリ上の ChatGPT Voice がコンピュータ操作や複数エージェントへの指示に使えるという product surface の信号です。一方、Apple SpeechAnalyzer は、独自の音声入力・音声分析ワークフローを作るための低レイヤーAPIとして位置づけられます。前者がプロダクト化された操作面、後者がカスタム harness に埋め込める入力 primitive という対比です。

もう一つの実務的な更新は、OpenAI Codex Security repo です。KBでは、脆弱性検出が CLI と TypeScript SDK として提供され、リポジトリスキャン、変更レビュー、findings の追跡、CIチェックに入るという点を、`coding-agent-harness-patterns` の「Productized specialized checks」と `eval-review-reliability` のセキュリティレビュー層に接続しました。ここでの含意は、セキュリティレビューを人間の最後の目視だけに置くのではなく、repo / CI / agent workflow の中で再実行可能な検査として扱うことです。ただし、blocking policy、false positive、scan coverage はまだ追加調査が必要です。

KB地図としては、`agent-harness-landscape` が voice and speech primitives を新しい節として明示し、`coding-agent-harness-patterns` は specialized checks をパターンとして強めました。`eval-review-reliability` には OpenAI Codex Security repo が加わり、deterministic checks、independent evaluator loop、trace-driven improvement の議論にセキュリティ領域の具体例が追加されています。`evidence-quality-and-source-trust` も更新され、X bookmark のような入口ソースと、公式ドキュメント・公式ブログ・GitHub repo のような一次ソースの扱い分けがより重要になりました。

実務上の読みどころは、Skills、Voice、Security CLI が別々のニュースではなく、同じ「agent harness の外部化」の流れにあることです。繰り返す手順は skill folder に落とす。人間の操作面は voice / desktop / tool surface に広げる。品質と安全性は CLI / SDK / CI / evaluator に逃がす。こうすると、モデルに毎回すべてを覚えさせるのではなく、周辺のファイル、ツール、検査、UIがエージェントの能力を支える構造になります。

Podcastで掘るなら、第一に「Skills は prompt の上位互換ではなく、手順と資産を必要時に読み込むための知識パッケージである」という話、第二に「MCP は接続、Skills は使い方、CI/CLI は検証、という分業」、第三に「Voice が入ると人間の指示は速くなるが、監査・確認・権限の設計がさらに重要になる」という論点がよさそうです。今日の更新は、エージェントを賢くする話というより、エージェントが働ける環境をどう設計するかに軸足があります。

次に追うべき問いは3つです。第一に、KB内の既存 workflow / runbook / verification ノートを、Claude Code チームの9分類で棚卸しすると何が足りないか。第二に、voice control surface では、音声で発火した操作の確認・ログ・取消・権限境界をどう設計すべきか。第三に、Codex Security のような specialized check を、どこまで merge gate にし、どこから advisory signal にとどめるかです。

## Important Sources

- `https://resources.anthropic.com/hubfs/The-Complete-Guide-to-Building-Skill-for-Claude.pdf`
- `https://www.anthropic.com/engineering/equipping-agents-for-the-real-world-with-agent-skills`
- `https://claude.com/blog/lessons-from-building-claude-code-how-we-use-skills`
- `https://github.com/openai/codex-security`
- `https://developer.apple.com/documentation/speech/speechanalyzer`
- `https://x.com/OpenAI/status/2080378182469857576`

## New / Changed Files

- `raw/x/bookmarks/bookmarks-20260729T0000Z.json`
- `raw/articles/apple-speechanalyzer-x-2026-07-28.md`
- `raw/articles/openai-chatgpt-voice-desktop-app-x-2026-07-23.md`
- `raw/articles/openai-codex-security-cli-typescript-sdk-github-x-2026-07-28.md`
- `raw/articles/anthropic-complete-guide-building-skills-for-claude-pdf-2026.md`
- `raw/articles/anthropic-equipping-agents-real-world-agent-skills-2025-10-16.md`
- `raw/articles/claude-skills-explained-ja-2026-03-05.md`
- `raw/articles/claude-lessons-from-building-claude-code-how-we-use-skills-2026-06-03.md`
- `wiki/sources/apple-speechanalyzer-x-2026-07-28.md`
- `wiki/sources/openai-chatgpt-voice-desktop-app-x-2026-07-23.md`
- `wiki/sources/openai-codex-security-cli-typescript-sdk-github-x-2026-07-28.md`
- `wiki/sources/anthropic-complete-guide-building-skills-for-claude-pdf.md`
- `wiki/sources/anthropic-equipping-agents-real-world-agent-skills.md`
- `wiki/sources/claude-skills-explained-ja.md`
- `wiki/sources/claude-lessons-from-building-claude-code-how-we-use-skills.md`
- `wiki/maps/agent-harness-landscape.md`
- `wiki/maps/coding-agent-harness-patterns.md`
- `wiki/maps/eval-review-reliability.md`
- `wiki/maps/evidence-quality-and-source-trust.md`
- `wiki/INDEX.md`


## 重要ソース

### Apple - SpeechAnalyzer documentation

Source note: `wiki/sources/apple-speechanalyzer-x-2026-07-28.md`

# Apple - SpeechAnalyzer documentation

## Source Metadata
- Raw path: `../../raw/articles/apple-speechanalyzer-x-2026-07-28.md`
- Raw bookmark capture: `../../raw/x/bookmarks/bookmarks-20260729T0000Z.json`
- Original URL: https://x.com/i/status/2082101877546832246
- Primary URL: https://developer.apple.com/documentation/speech/speechanalyzer
- Author: 松濤Vimmer / @shotovim
- Posted: 2026-07-28T13:52:25.000Z
- Captured: 2026-07-29T00:00:25.239Z via xurl bookmarks capture
- Type: X bookmark to Apple Developer Documentation
- Evidence strength: high that the docs page exists; medium for the workflow claim
- Public metrics at capture: 30 likes, 4 reposts, 0 replies, 0 quotes, 53 bookmarks, 2615 impressions

## Summary
Apple's SpeechAnalyzer documentation is a useful signal that speech-analysis APIs are mature enough to support custom voice-input workflows. The bookmarked post is anecdotal, but it claims the author replaced several subscription voice-input tools with a self-built app using SpeechAnalyzer and found the result comparable.

## Key Claims
- Apple has a documented SpeechAnalyzer API/page.
- The bookmark's author used SpeechAnalyzer to build a usable voice-input app.
- Speech analysis can be part of a practical local or custom app workflow instead of only a vendor subscription.

## Evidence / Examples
- The card title names SpeechAnalyzer directly.
- The card description says it analyzes spoken audio content in various ways and manages the analysis session.
- The bookmark text says the author now operates a self-built voice-input app using SpeechAnalyzer without obvious loss in usefulness.

## Evidence Quality
- Source type: X bookmark pointing to Apple documentation
- Confidence: high for the existence of the docs page, medium for the anecdotal usability claim
- 

### OpenAI - ChatGPT Voice desktop app

Source note: `wiki/sources/openai-chatgpt-voice-desktop-app-x-2026-07-23.md`

# OpenAI - ChatGPT Voice desktop app

## Source Metadata
- Raw path: `../../raw/articles/openai-chatgpt-voice-desktop-app-x-2026-07-23.md`
- Raw bookmark capture: `../../raw/x/bookmarks/bookmarks-20260729T0000Z.json`
- Original URL: https://x.com/i/status/2080378182469857576
- Media URL: https://x.com/OpenAI/status/2080378182469857576/video/1
- Author: OpenAI / @OpenAI
- Posted: 2026-07-23T19:43:04.000Z
- Captured: 2026-07-29T00:00:25.239Z via xurl bookmarks capture
- Type: X product announcement / video
- Evidence strength: high for feature existence; low for unverified implementation details
- Public metrics at capture: 12874 likes, 1382 reposts, 1217 replies, 1245 quotes, 3400 bookmarks, 4453959 impressions

## Summary
OpenAI announced ChatGPT Voice in the desktop app and framed it as a way to control the computer and direct multiple agents in ChatGPT Work or Codex using voice. The bookmark matters because it treats voice as a live control surface rather than only a conversational input mode.

## Key Claims
- ChatGPT Voice is available in the desktop app.
- Voice can be used to control the computer and direct multiple agents.
- The voice surface spans ChatGPT Work and Codex.
- The product is being positioned as speaking, listening, and coordinating work in one app.

## Evidence / Examples
- The post text explicitly says ChatGPT Voice is now in the desktop app.
- The post says voice can control the computer and direct multiple agents.
- The announcement says the capability is rolling out globally.

## Evidence Quality
- Source type: first-party product announcement
- Confidence: high for the product-surface claim, low for implementation details not captured in the post
- Supports: tool-accessibility, managed-agents, coding-agents, agent-management
- Main limitations: 

### OpenAI - Codex Security CLI and TypeScript SDK

Source note: `wiki/sources/openai-codex-security-cli-typescript-sdk-github-x-2026-07-28.md`

# OpenAI - Codex Security CLI and TypeScript SDK

## Source Metadata
- Raw path: `../../raw/articles/openai-codex-security-cli-typescript-sdk-github-x-2026-07-28.md`
- Raw bookmark capture: `../../raw/x/bookmarks/bookmarks-20260729T0000Z.json`
- Original URL: https://x.com/i/status/2082241164850364555
- Primary URL: https://github.com/openai/codex-security
- Author: Tibo / @thsottiaux
- Posted: 2026-07-28T23:05:54.000Z
- Captured: 2026-07-29T00:00:25.239Z via xurl bookmarks capture
- Type: X bookmark linking to GitHub repository
- Evidence strength: high for repo existence; medium for product scope until repo docs are read
- Public metrics at capture: 2160 likes, 177 reposts, 168 replies, 23 quotes, 1380 bookmarks, 67651 impressions

## Summary
OpenAI's Codex Security repo is a notable harness signal because it packages vulnerability finding as both a CLI and a TypeScript SDK. The bookmark explicitly says it can find, validate, and fix security issues, scan repositories, review changes, track findings over time, and run security checks in CI.

## Key Claims
- Codex Security is available as an open-source CLI and TypeScript SDK.
- The tool is intended to find, validate, and fix vulnerabilities.
- It supports repository scans, change review, longitudinal finding tracking, and CI checks.
- Security review is being productized as a reusable developer workflow surface.

## Evidence / Examples
- The bookmark text spells out the CLI and TypeScript SDK shape.
- The post explicitly mentions repository scanning and CI integration.
- The linked GitHub repo is the stronger source for implementation detail, but the bookmark is already strong enough to justify an indexable source note.

## Evidence Quality
- Source type: X bookmark to GitHub repository
- Confidence: high for the repo

### Anthropic - The Complete Guide to Building Skills for Claude

Source note: `wiki/sources/anthropic-complete-guide-building-skills-for-claude-pdf.md`

# Anthropic - The Complete Guide to Building Skills for Claude

## Source Metadata
- Raw path: `../../raw/articles/anthropic-complete-guide-building-skills-for-claude-pdf-2026.md`
- Original URL: https://resources.anthropic.com/hubfs/The-Complete-Guide-to-Building-Skill-for-Claude.pdf
- Author: Anthropic
- Captured: 2026-07-29
- Type: official PDF guide
- Evidence strength: high for Anthropic's recommended skill design categories and authoring heuristics

## Summary
Anthropic's guide explains skills as reusable instruction folders for Claude, then walks through planning, structure, testing, distribution, and troubleshooting. Its most reusable taxonomy is the three common skill use case categories: document and asset creation, workflow automation, and MCP enhancement.

## Key Claims
- Skills are useful when workflows repeat and the user would otherwise need to restate preferences, process, or domain expertise.
- Strong skills usually start from 2-3 concrete use cases with trigger phrases, steps, required tools, embedded knowledge, and success criteria.
- Common skill categories are document/asset creation, workflow automation, and MCP enhancement.
- MCP gives Claude access to services; skills encode the workflow knowledge for using that access well.

## Evidence / Examples
- Document & Asset Creation covers consistent outputs such as documents, presentations, apps, designs, and code.
- Workflow Automation covers multi-step processes with methodology, validation gates, templates, and iterative refinement.
- MCP Enhancement covers domain workflow guidance layered on top of MCP servers, including call sequencing, context, and error handling.

## Evidence Quality
- Source type: first-party Anthropic PDF guide.
- Confidence: high for Anthropic's skill authoring guidance; medi

### Anthropic - Equipping agents for the real world with Agent Skills

Source note: `wiki/sources/anthropic-equipping-agents-real-world-agent-skills.md`

# Anthropic - Equipping agents for the real world with Agent Skills

## Source Metadata
- Raw path: `../../raw/articles/anthropic-equipping-agents-real-world-agent-skills-2025-10-16.md`
- Original URL: https://www.anthropic.com/engineering/equipping-agents-for-the-real-world-with-agent-skills
- Author: Anthropic
- Published: 2025-10-16
- Captured: 2026-07-29
- Type: engineering blog
- Evidence strength: high for Anthropic's Agent Skills design pattern and best-practice framing

## Summary
Anthropic presents Agent Skills as composable folders of instructions, scripts, and resources that let general-purpose agents dynamically load domain-specific expertise. The key design pattern is progressive disclosure: the agent sees small metadata first, reads the core `SKILL.md` only when relevant, and opens deeper files or executes bundled code only as the task requires.

## Key Claims
- Real work requires procedural knowledge and organizational context, not just model capability.
- Skills let teams specialize agents by packaging expertise instead of creating many fragmented custom agents.
- The skill folder pattern scales because it keeps most context out of the prompt until needed.
- Executable scripts inside skills can make deterministic sub-tasks cheaper and more reliable than token generation.
- Useful skills should be built from observed task gaps, representative evaluations, and iteration on actual agent behavior.
- Skills can complement MCP by teaching agents workflows over external tools, not merely granting access to those tools.

## Evidence / Examples
- The article walks through a PDF skill with `SKILL.md`, supporting files, and a Python script for form extraction.
- It recommends starting with evaluation, splitting large skills into referenced files, monitoring real us

### Claude - Lessons from building Claude Code: How we use skills

Source note: `wiki/sources/claude-lessons-from-building-claude-code-how-we-use-skills.md`

# Claude - Lessons from building Claude Code: How we use skills

## Source Metadata
- Raw path: `../../raw/articles/claude-lessons-from-building-claude-code-how-we-use-skills-2026-06-03.md`
- Original URL: https://claude.com/blog/lessons-from-building-claude-code-how-we-use-skills
- Author: Thariq Shihipar / Anthropic
- Published: 2026-06-03
- Captured: 2026-07-29
- Type: Claude blog / Claude Code practice article
- Evidence strength: high for Anthropic's internal skill taxonomy and practical skill-authoring guidance

## Summary
Anthropic's Claude Code team reports lessons from building and scaling hundreds of internal skills. The core contribution is a nine-category taxonomy of skill types, led by "Library and API reference," plus pragmatic advice for writing skills that add high-signal context rather than repeating what Claude already knows.

## Key Claims
- Skills are one of Claude Code's most-used extension points internally at Anthropic.
- Useful skills tend to fit cleanly into one skill type; overly broad skills that straddle several types can confuse the agent.
- Library/API reference skills are valuable because they explain correct library, CLI, or SDK usage and capture gotchas.
- Verification skills had the most measurable internal impact on Claude output quality.
- Good skills use gotchas sections, filesystem-based progressive disclosure, scripts, setup config, usage logging, and careful marketplace/distribution practices.

## Nine Skill Types
- Library and API reference
- Product verification
- Data fetching and analysis
- Business process and team automation
- Code scaffolding and templates
- Code quality and review
- CI/CD and deployment
- Runbooks
- Infrastructure operations

## Evidence Quality
- Source type: first-party Claude Code team practice article.

### Claude - スキル解説：スキルとプロンプト、プロジェクト、MCP、サブエージェントとの比較

Source note: `wiki/sources/claude-skills-explained-ja.md`

# Claude - スキル解説：スキルとプロンプト、プロジェクト、MCP、サブエージェントとの比較

## Source Metadata
- Raw path: `../../raw/articles/claude-skills-explained-ja-2026-03-05.md`
- Original URL: https://claude.com/ja/blog/skills-explained
- Canonical URL: https://claude.com/blog/skills-explained
- Author: Claude / Anthropic
- Published: 2026-03-05
- Captured: 2026-07-29
- Type: Claude blog guidance article
- Evidence strength: high for Anthropic's recommended "when to use skills" taxonomy

## Summary
This Claude blog article explains where skills fit relative to prompts, projects, MCP, subagents, and related agent-building tools. Its most relevant taxonomy is the "when to use skills" section: skills are useful for specialized work that should be performed reliably and efficiently across repeated tasks.

## Key Claims
- Skills are dynamically discovered instruction/resource folders for specialized work.
- Skills are best for repeatable specialized work, not one-off conversational instructions.
- The article names three useful-skill categories: organizational workflows, domain expertise, and personal preferences.
- Prompts remain better for one-off, conversational, immediate context.
- MCP provides external tool access; skills encode reusable workflow knowledge around when and how to do the work.

## Evidence / Examples
- Organizational workflows: brand guidelines, compliance procedures, document templates.
- Domain expertise: Excel formulas, PDF operations, data analysis.
- Personal preferences: note-taking systems, coding patterns, research methods.

## Evidence Quality
- Source type: first-party Claude blog guidance.
- Confidence: high for taxonomy and product-positioning guidance.
- Supports: navigable-agent-skills, memory-skill-harness, tool-accessibility, workflow packaging
- Main limitations: produ

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

### Coding-Agent Harness Patterns

KB note: `wiki/maps/coding-agent-harness-patterns.md`

# Coding-Agent Harness Patterns

## Purpose
Synthesize practical harness patterns for coding-agent workflows using the KB's control vocabulary plus a concrete real-world operator example.

## Core claim
A coding-agent workflow becomes harness engineering when quality and reliability depend on the surrounding artifacts, controls, and review loops rather than on the model prompt alone.

## Pattern 1. Plan as handoff artifact
Use a session-scoped plan file such as `plan.md` as a durable handoff contract.

Why it matters:
- makes intent inspectable
- supports context resets and reviewer alignment
- creates a stable object for verifier agents to critique

## Pattern 2. Verifier split without full multi-agent overhead
Use heavy thinking for hard, bounded reasoning: spawn independent temporary thinkers, then have one deliberator critique and synthesize their outputs.

Use a second agent or model mainly for plan review or implementation review instead of duplicating the whole execution role.



### Eval and Review Reliability

KB note: `wiki/maps/eval-review-reliability.md`

# Eval and Review Reliability

## Purpose
Collect the KB's evaluation and review ideas into one map focused on practical reliability: how to know whether an agent-produced artifact is good enough, and how to keep review load from becoming the bottleneck.

## Core thesis
Agent output quality improves when evaluation is treated as a separate harness layer, not as an informal final glance by the same agent that produced the work.

## Reliability layers

### 1. Deterministic checks first
Use cheap checks before semantic review:
- lint and typecheck
- tests and smoke tests
- formatting and structural checks
- repository-specific machine-checkable invariants

Related concepts: [[../concepts/machine-checkable-invariants.md]], [[../concepts/feedback-controls.md]].

### 2. Task-fit review
Check whether the work actually satisfies the request:
- requirements coverage
- edge cases
- backward compatibility
- user-facing behavior
- maintainability

Related maps: [[coding-agent-review-rubric.md]], [

### Evidence Quality and Source Trust

KB note: `wiki/maps/evidence-quality-and-source-trust.md`

# Evidence Quality and Source Trust

## Purpose
Turn the KB from a flat summary collection into a research OS that can reason about claim strength, provenance, and safe reuse.

## Core thesis
The wiki should not only answer "what does this source say?" It should answer "how much should we trust this source for this specific claim, and what can it safely support?"

## Source anchors
- [[../sources/karpathy-personal-llm-kb.md]]
- [[../sources/contextconor-enterprise-understanding-context-graph-x.md]]
- [[../sources/masaki-claude-code-harness-operation-note.md]]
- [[../sources/anthropic-april-23-postmortem-claude-code-quality.md]]
- [[../sources/arxiv-aris-autonomous-research-adversarial-multi-agent-collaboration.md]]
- [[../sources/openai-harness-engineering.md]]
- [[../sources/spillwave-ai-coding-hangover-harness-engineering.md]]

## Evidence tiers

### Tier 1: Direct primary evidence
Use for definitions, product behavior, and hard constraints.
- official docs
- source repositories
- pa

## NotebookLM Podcast用メモ

- まず今日の全体トレンドを話してから、重要ソースを3本に絞って深掘りする。
- ソース単体の紹介で終わらせず、既存KBの概念や地図がどう更新されたかを会話に含める。
- 最後に、明日以降の調査問いを2〜3個提示する。
