<!-- generated: 2026-05-31T13:01:46.847298+00:00 -->
<!-- kb_daily_digest_date: 2026-05-31 -->
# KB Daily Digest Source — 2026-05-31

このページは、knowledge-base-llm の日次更新を NotebookLM に読み込ませるための公開向けソースページです。
Discord通知よりも文脈を厚めに残し、Podcast化しやすいように、今日追加・更新されたソース、概念、地図を文章中心で整理します。

## 今日の全体像

# KB Daily Digest 2026-05-31

今日の knowledge-base-llm は、agentic coding の「できるようになったこと」から一歩進んで、「組織がその能力をどう吸収し、どう検証し、どう費用対効果として扱うか」に焦点が移った更新でした。UTC 2026-05-31 の新規 ingest / compile では、Salesforce の組織的な Claude Code 採用、Cognition の agentic development 検証論、OpenAI の GPT-Rosalind / Rosalind Biodefense、Codex 側の dynamic workflows 実装パターン、そして Simon Willison による OpenAI / Anthropic の product-market fit 論が追加されました。全体として、agent harness は単なる開発者個人の作法ではなく、企業の標準ワークフロー、検証基盤、価格設計、安全ガバナンスをつなぐ中核概念として強化されています。

重要ソースの1本目は、Boris Cherny が共有した Salesforce Engineering の agentic 化です。Claude Code を標準ツールとして扱い、トークン制限の撤廃や移行作業の短縮を含む具体的な成果が記録されました。KB上では、これは `agent-harness-landscape` と `ai-adoption-roi-and-capability-investment` の両方に効いています。つまり、agentic coding の価値は「AIがコードを書く」だけでは測れず、組織の権限設計、レビュー経路、標準ツール化、成果KPIに組み込まれて初めてROIの議論になる、という方向です。

2本目は Cognition の “Verifying Agentic Development at Scale” です。ここでの中心は、agent がクラウドで非同期に作業するほど、ローカルな自信や見た目の完成度ではなく、エンドツーエンドの証拠、test-mode、verified PR のような「証明可能な完了」が必要になるという点です。これは `eval-review-reliability` に直接つながり、生成側と評価側を分けるだけでなく、検証をホストされた harness の一部として設計する流れを強めました。agentic work のスループットが上がるほど、検証能力が足りないと review debt や instability tax に転化する、というKBの既存テーマがより明確になっています。

3本目は Simon Willison の product-market fit 論です。Simon は、Claude Code / Cowork や Codex のような coding / agent product が、OpenAI と Anthropic にとって本格的なPMFに近づいていると見ています。KBにとって重要なのは、これは技術論というより経済論だという点です。coding agents は通常のチャットよりはるかに多くのトークンを消費する一方、高価な専門職の日常業務に入り込むため、usage-based enterprise pricing が成立しうる。これは `agentic-product-market-fit`、`agentic-jevons-paradox`、`ai-roi-model` をつなぎ、予算超過を単なる失敗ではなく「需要が想定より広がった可能性」と「検証されない機械作業が増えただけの可能性」の両面から読む必要がある、という見方を追加しました。

OpenAI の Rosalind Biodefense / GPT-Rosalind は、今日の更新の中で少し異なる方向の重要ソースです。汎用チャットやcoding agentではなく、生命科学・公衆衛生・バイオディフェンスという高信頼領域に、アクセス制御された reasoning model を入れる話として位置づけられています。ここでは「強いモデルを誰にでも開く」よりも、許可されたミッション、パートナー、ガバナンス、研究ワークフローの境界が主役になります。KB全体の文脈では、agentic system が普及するほど、harness は生産性だけでなく安全性・権限・監査可能性の設計でもある、という補助線になります。

Dan McAteer の Codex dynamic workflows は、Claude Code の dynamic workflow 的なパターンが Codex 側にも移植可能であることを示す、実務寄りの更新でした。モデルに orchestration script を書かせ、subagent へ並列に仕事を分配し、進捗を会話の外に保存する。このパターンは `orchestration-patterns-faq` の「generated control flow」「resumable execution」「orchestrator-subagent」に相当し、dynamic workflow が単一プロダクト固有機能ではなく、agent harness の再利用可能な形になりつつあることを示しています。

compile 側では、`agent-harness-landscape`、`eval-review-reliability`、`orchestration-patterns-faq`、`ai-adoption-roi-and-capability-investment` が特に重要です。前者2つは、agent harness を「文脈を渡す仕組み」と「検証を成立させる仕組み」に分解し直しています。後者2つは、multi-agent / dynamic workflow の制御フローと、企業導入における費用対効果の読み方を整理しています。加えて、`agentic-product-market-fit`、`agentic-jevons-paradox`、`ai-roi-model`、`coding-agents`、`glossary`、`operations` も更新され、KBの地図が「個人の開発効率」から「組織の吸収能力・価格・検証・運用」へ広がりました。

今日の全体トレンドを一言でまとめるなら、agentic coding は「速く作れる」段階から、「速く作られたものを組織がどのくらい信用し、どのくらい支払い、どのくらい安全に運用できるか」の段階に移っています。Salesforce は組織導入の成功シグナル、Cognition は検証能力の必要条件、Simon は市場と価格の読み方、OpenAI Rosalind は高信頼領域での境界設計、dynamic workflows は実装パターンの再利用性を示しました。次に追うべき問いは、agentic demand expansion と単なる artifact volume をどう区別するか、verified PR や evaluator loop をどのレベルで標準化すべきか、usage-based pricing が健全なROI測定を促すのか、それとも探索を早すぎる段階で抑制するのか、です。

重要ソース3本:
- Salesforce Engineering became truly agentic: `wiki/sources/bcherny-salesforce-engineering-truly-agentic-x-2026-05-29.md`
- Cognition / Verifying Agentic Development at Scale: `wiki/sources/ido_pesok-verifying-agentic-development-at-scale-x-2026-05-29.md`
- Simon Willison / Anthropic and OpenAI product-market fit: `wiki/sources/simon-willison-product-market-fit.md`

公開ページ / NotebookLM Podcast では、今日の更新を「agentic coding のPMFと検証税」という軸で掘ると話しやすいです。Salesforce の成功事例と Simon の価格論を並べると、企業が高いagent使用料を払える条件が見えます。一方で Cognition と eval map を並べると、速度が増すほど検証が主戦場になることがわかります。OpenAI Rosalind は、その議論を高信頼領域に拡張し、harness を単なる生産性ツールではなく、アクセス制御・安全・責任分界の設計として読むきっかけになります。


## 重要ソース

### Source Notes

Source note: `wiki/sources/README.md`

# Source Notes

Each note in this folder should summarize one source from `raw/`.

Recommended structure:
- source metadata
- short summary
- key claims
- evidence / examples
- evidence quality when the source is anecdotal, preview-only, benchmark-heavy, or captured from truncated material
- related concepts
- open questions
- backlinks to raw material
- [[simon-willison-product-market-fit.md]] — Simon Willison's market analysis that Anthropic/OpenAI have found product-market fit through coding/general-purpose agents, API-aligned enterprise pricing, and high-value professional usage.
- [[simon-willison-gitlab-act-2.md]] — Simon Willison on GitLab's Act 2 announcement, organization flattening, smaller empowered R&D teams, and the agentic-era Jevons-style software demand thesis.
- [[google-research-nested-learning-continual-learning.md]] — Google Research on Nested Learning, continuum memory systems, and Hope as a model-internal continual-learning architecture.
- [[anthropic-claude-code-large-codebases.md]] — Anthropic on Claude Code at large-codebase scale: live-code navigation, harness extension points, layered context files, LSP/subagents, and org ownership.
- [[about-hiroppy-founders-playbook.md]] — Anthropic's official founder playbook PDF: AI-native startup lifecycle across Idea, MVP, Launch, and Scale, with Claude Chat/Cowork/Code stage usage, validation gates, agentic technical debt risks, founder bottleneck removal, and moat formation.
- [[izanami-claude-code-large-codebase-best-practices.md]] — Japanese practitioner explainer on Claude Code large-codebase setup: live repo search, thin layered CLAUDE.md, subdirectory startup, hooks, stale-rule pruning, and adoption ownership.
- [[newspicks-harness-engineering-what-is-it.md]] — Japanese explainer separating evalua

### Simon Willison - I think Anthropic and OpenAI have found product-market fit

Source note: `wiki/sources/simon-willison-product-market-fit.md`

# Simon Willison - I think Anthropic and OpenAI have found product-market fit

## Metadata
- Raw path: `raw/articles/simon-willison-product-market-fit-2026-05-27.md`
- Original/source URL: https://simonwillison.net/2026/May/27/product-market-fit/
- Author: Simon Willison
- Published: 2026-05-27
- Fetched/ingested: 2026-05-31
- Source type: weblog article / market analysis
- Evidence strength: medium for Simon's interpretation and first-person usage comparison; lower for product-market-fit certainty because the thesis depends on unaudited financial reports, job-listing classification, and future IPO disclosures.

## Summary
Simon Willison argues that Anthropic and OpenAI have likely found product-market fit through coding and general-purpose agent products such as Claude Code/Cowork and Codex. The article's useful KB contribution is the pricing and demand-side frame: coding agents burn far more tokens than ordinary chat, but are valuable enough to become daily tools for high-value knowledge work, making enterprise usage-based pricing a plausible revenue engine.

## Key claims
- Coding agents change the economics of frontier labs because they create much higher token consumption than chat subscriptions while serving professionally valuable workflows.
- April 2026 is a second inflection point after the November 2025 agent-capability inflection: leading labs released more expensive frontier models and moved enterprise agent usage closer to API-token pricing.
- Stories about Uber budget overruns and Microsoft reducing Claude Code licenses may be better read as signs of pricing pressure and demand than as simple AI-failure stories.
- OpenAI and Anthropic job listings suggest heavy investment in enterprise sales, support, and forward-deployed roles, which fits an enterprise-ag

### Boris Cherny - Salesforce engineering became truly agentic

Source note: `wiki/sources/bcherny-salesforce-engineering-truly-agentic-x-2026-05-29.md`

# Boris Cherny - Salesforce engineering became truly agentic

## Source Metadata
- Raw path: `raw/articles/bcherny-salesforce-engineering-truly-agentic-x-2026-05-29.md`
- Original URL: https://x.com/i/status/2060390852619272526
- Primary source: https://www.salesforce.com/news/stories/how-engineering-became-agentic/
- Author: Boris Cherny / @bcherny
- Date: 2026-05-29
- Type: X post / company story
- Evidence strength: bookmark snapshot metadata plus official Salesforce story
- Capture source: xurl bookmarks capture

## Summary

Salesforce is presenting its engineering shift as a concrete agentic transformation: Claude Code becomes the primary AI agent tool, token limits are removed, and a large migration ships in days rather than months.

## Key Claims
- Standardizing on Claude Code changed throughput and quality at Salesforce.
- Removing token limits improved output rather than harming it.
- An agentic workflow can compress a 231-person-day migration into 13 days.

## Evidence / Examples
- The post text points to the Salesforce story and highlights the migration example.
- The official article is the durable source for the organizational change claim.

## Evidence Quality
- Source type: X post plus official company story
- Confidence: high for the organizational signal, moderate for the generalizability
- Supports: [[../concepts/agent-first-organization.md]], [[../concepts/product-responsibility-distribution.md]], [[../concepts/harness-engineering.md]], [[../concepts/organizational-intent-clarity.md]]

## Related Concepts
- [[../concepts/agent-first-organization.md]]
- [[../concepts/product-responsibility-distribution.md]]
- [[../concepts/harness-engineering.md]]
- [[../concepts/organizational-intent-clarity.md]]

## Related Maps
- [[../maps/agent-harness-landscape.md

### Dan McAteer - Codex Dynamic workflows

Source note: `wiki/sources/daniel_mac8-codex-dynamic-workflows-x-2026-05-30.md`

# Dan McAteer - Codex Dynamic workflows

## Source Metadata
- Raw path: `raw/articles/daniel_mac8-codex-dynamic-workflows-x-2026-05-30.md`
- Original URL: https://x.com/i/status/2060677155055427844
- Primary source: https://claude.com/blog/introducing-dynamic-workflows-in-claude-code
- Author: Dan McAteer / @daniel_mac8
- Date: 2026-05-30
- Type: X post / workflow demo
- Evidence strength: xurl bookmarks capture plus primary Claude product post
- Capture source: xurl bookmarks capture

## Summary

This bookmark is a portable-pattern signal: the post shows a Codex-side skill or workflow that recreates Claude-style dynamic orchestration by generating an orchestration script, fanning out to parallel subagents, and keeping coordination outside the main chat thread.

## Key Claims
- Dynamic workflows can be recreated as a reusable agent skill pattern.
- The useful unit is orchestration, not just a better prompt.
- Parallel subagents and generated control flow are the main lever.

## Evidence / Examples
- The bookmark text is largely operational instruction, so the main evidence is the post's description of the workflow shape.
- The linked Claude launch post supplies the strongest anchor for the pattern definition.

## Evidence Quality
- Source type: X post plus primary vendor launch post
- Confidence: moderate for the pattern, lower for the specific Codex implementation details
- Supports: [[../concepts/multi-agent-orchestration.md]], [[../concepts/workflow-compilation.md]], [[../concepts/harness-engineering.md]], [[../concepts/navigable-agent-skills.md]]

## Related Concepts
- [[../concepts/multi-agent-orchestration.md]]
- [[../concepts/workflow-compilation.md]]
- [[../concepts/harness-engineering.md]]
- [[../concepts/navigable-agent-skills.md]]
- [[../concepts/self-verific

### Ido Pesok - Verifying Agentic Development at Scale

Source note: `wiki/sources/ido_pesok-verifying-agentic-development-at-scale-x-2026-05-29.md`

# Ido Pesok - Verifying Agentic Development at Scale

## Source Metadata
- Raw path: `raw/articles/ido_pesok-verifying-agentic-development-at-scale-x-2026-05-29.md`
- Original URL: https://x.com/i/status/2060416230641881336
- Primary source: https://cognition.ai/blog/testing-development
- Author: Ido Pesok / @ido_pesok
- Date: 2026-05-29
- Type: X article card / blog post
- Evidence strength: bookmark snapshot metadata plus official Cognition article
- Capture source: xurl bookmarks capture

## Summary

Cognition frames agentic development as an asynchronous system problem: if Devins can trigger work in the cloud, then verification must also happen in the cloud and return a ready-to-merge result.

## Key Claims
- Agentic development at scale needs end-to-end verification, not just code generation.
- Cloud test runs are the natural place to verify async agent output.
- The review bottleneck shifts from "can we inspect it?" to "can we prove it?"

## Evidence / Examples
- The bookmark exposes the article title and official source URL.
- The supporting post text highlights test-mode Devins and the shift to async software engineering.

## Evidence Quality
- Source type: X article card plus primary company blog
- Confidence: high for the verification thesis, moderate for exact implementation details
- Supports: [[../concepts/real-world-evaluation.md]], [[../concepts/self-verification.md]], [[../concepts/verification-tax.md]], [[../concepts/human-in-the-loop.md]]

## Related Concepts
- [[../concepts/real-world-evaluation.md]]
- [[../concepts/self-verification.md]]
- [[../concepts/verification-tax.md]]
- [[../concepts/human-in-the-loop.md]]
- [[../concepts/agent-safety.md]]

## Related Maps
- [[../maps/eval-review-reliability.md]]
- [[../maps/agent-deployment-gates-and-operatio

### OpenAI - Rosalind Biodefense and GPT-Rosalind

Source note: `wiki/sources/openai-rosalind-biodefense-gpt-rosalind-x-2026-05-29.md`

# OpenAI - Rosalind Biodefense and GPT-Rosalind

## Source Metadata
- Raw path: `raw/articles/openai-rosalind-biodefense-gpt-rosalind-x-2026-05-29.md`
- Original URL: https://x.com/i/status/2060376598642405492
- Primary sources:
  - https://openai.com/index/strengthening-societal-resilience-with-rosalind-biodefense/
  - https://openai.com/index/introducing-gpt-rosalind/
  - https://help.openai.com/en/articles/20001193-introducing-gpt-rosalind-for-life-sciences-research
- Author: OpenAI / @OpenAI
- Date: 2026-05-29
- Type: X post / product announcement
- Evidence strength: bookmark snapshot metadata plus official OpenAI announcement and help-center pages
- Capture source: xurl bookmarks capture

## Summary

OpenAI is positioning GPT-Rosalind as a life-sciences reasoning model and pairing it with a biodefense initiative. The key signal is the combination of frontier biological reasoning, trusted access, and mission-bounded deployment.

## Key Claims
- GPT-Rosalind is available for qualified research workflows in ChatGPT, Codex, and the API.
- Rosalind Biodefense is meant to support defensive biological work.
- Trusted access and governance are part of the product, not an afterthought.

## Evidence / Examples
- The X post provides the launch signal and the intended audience.
- The OpenAI blog and help-center pages provide the durable product framing.

## Evidence Quality
- Source type: X post plus official OpenAI announcement and docs
- Confidence: high for the launch and access framing
- Supports: [[../concepts/agent-safety.md]], [[../concepts/real-world-evaluation.md]], [[../concepts/evidence-quality.md]], [[../concepts/human-in-the-loop.md]]

## Related Concepts
- [[../concepts/agent-safety.md]]
- [[../concepts/real-world-evaluation.md]]
- [[../concepts/evidence-quality

## 更新された概念・地図

### Agentic Jevons Paradox

KB note: `wiki/concepts/agentic-jevons-paradox.md`

---
aliases:
  - Agentic Jevons Paradox
  - Jevons paradox for software agents
  - AI software demand expansion
---

# Agentic Jevons Paradox

## Definition
The thesis that as AI agents reduce the cost of producing and managing software, total demand for software, software experiments, and agent-supported builders may expand rather than shrink.

## Why It Matters
This is the optimistic economic counterpoint to headcount-reduction narratives. If software becomes cheaper to create, organizations may ask for more internal tools, integrations, experiments, personalization, and automation. The bottleneck then shifts from “can we write the code?” to “can we choose, verify, operate, and maintain the extra software?”

## Related Concepts
- [[coding-agents.md]]
- [[ai-roi-model.md]]
- [[ai-adoption-j-curve.md]]
- [[verification-tax.md]]
- [[instability-tax.md]]
- [[comprehension-debt.md]]
- [[organizational-intent-clarity.md]]
- [[sustainable-ai-work.md]]

## Supporting Sources
OpenClaw spend s

### Agentic Product-Market Fit

KB note: `wiki/concepts/agentic-product-market-fit.md`

---
aliases:
  - Agentic Product-Market Fit
  - Coding-agent product-market fit
  - Agent PMF
---

# Agentic Product-Market Fit

## Definition
The point where agent products become valuable and habit-forming enough that users or enterprises accept high recurring usage costs, operational changes, and workflow dependency around them.

## Why It Matters
Agentic product-market fit is stronger than generic chatbot popularity. It implies that agents are doing enough economically valuable work that customers tolerate usage-based bills, enterprise procurement, governance, and workflow redesign.

## Related Concepts
- [[coding-agents.md]]
- [[ai-roi-model.md]]
- [[agentic-jevons-paradox.md]]
- [[ai-adoption-j-curve.md]]
- [[verification-tax.md]]
- [[instability-tax.md]]
- [[evidence-quality.md]]

## Supporting Sources
- [[../sources/simon-willison-product-market-fit.md]]
- [[../sources/simon-willison-gitlab-act-2.md]]
- [[../sources/dora-roi-ai-assisted-software-development.md]]
- [[../sources/

### AI ROI Model

KB note: `wiki/concepts/ai-roi-model.md`

---
aliases:
  - AI ROI Model
  - ROI of AI-assisted Software Development
  - AI Value Model
---

# AI ROI Model

## Definition
A structured way to estimate the return on AI-assisted software development by linking AI adoption to delivery metrics, business value, and adoption costs.

## Why It Matters
AI productivity claims are not enough for enterprise adoption. A credible model connects engineering indicators to financial outcomes while accounting for hard costs, learning costs, instability, and uncertainty.

## Related Concepts
- [[ai-adoption-j-curve]]
- [[verification-tax]]
- [[evidence-quality]]
- [[organizational-intent-clarity]]
- [[product-responsibility-distribution]]
- [[sustainable-ai-work]]
- [[agentic-jevons-paradox]]

## Supporting Sources
- [[../sources/dora-roi-ai-assisted-software-development.md]]
- [[../sources/simon-willison-gitlab-act-2.md]]
- [[../sources/simon-willison-product-market-fit.md]]
- [[../sources/tsunoda-legalon-ai-driven-hiring-token-budget-x-2026-05-

### Coding Agents

KB note: `wiki/concepts/coding-agents.md`

---
aliases:
  - Coding Agents
---

# Coding Agents

## Definition
Agents that operate in software development environments using code editing, terminal commands, tests, and repository context as part of their task execution.

## Why It Matters
Coding agents are one of the most concrete and operationally demanding forms of LLM agents, making them useful for studying autonomy and oversight in practice.

## Related Concepts
- [[agent-autonomy]]
- [[approval-policy]]
- [[human-in-the-loop]]
- [[spec-code-test-loop.md]]

## Supporting Sources
- [[../sources/anthropic-claude-code-auto-mode.md]]
- [[../sources/anthropic-claude-code-on-the-web-docs.md]]
- [[../sources/openai-codex-plugin-cc-github.md]]
- [[../sources/openai-codex-chrome-plugin-x.md]]
- [[../sources/aws-agent-toolkit-for-aws-x.md]]
- [[../sources/nukonuko-code-with-claude-workshops-x.md]]
- [[../sources/anthropic-claude-code-init-interview-x.md]]
- [[../sources/cursor-3-blog.md]]
- [[../sources/storybook-mcp-react-blog.md]]
- 

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

### Navigation: Operations / Long-Running Work

KB note: `wiki/navigation/operations.md`

# Navigation: Operations / Long-Running Work

## Use When
The question is about running agents over time: background agents, routines, scheduled work, handoffs, context resets, delegation, or monitoring.

## Start Maps
- [[../maps/ai-adoption-roi-and-capability-investment.md]]
- [[../maps/context-management-decisions.md]]
- [[../maps/orchestration-patterns-faq.md]]
- [[../maps/approval-policy-patterns-and-escalation.md]]

## Core Concepts
- [[../concepts/ai-adoption-j-curve.md]]
- [[../concepts/agentic-product-market-fit.md]]
- [[../concepts/ai-native-startup-lifecycle.md]]
- [[../concepts/verification-tax.md]]
- [[../concepts/ai-roi-model.md]]
- [[../concepts/agentic-jevons-paradox.md]]
- [[../concepts/long-running-agents.md]]
- [[../concepts/background-agents.md]]
- [[../concepts/agent-first-organization.md]]
- [[../concepts/managed-agents.md]]
- [[../concepts/agent-dreaming.md]]
- [[../concepts/outcomes.md]]
- [[../concepts/gateway-control-plane.md]]
- [[../concepts/structured-hando

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

## NotebookLM Podcast用メモ

- まず今日の全体トレンドを話してから、重要ソースを3本に絞って深掘りする。
- ソース単体の紹介で終わらせず、既存KBの概念や地図がどう更新されたかを会話に含める。
- 最後に、明日以降の調査問いを2〜3個提示する。
