<!-- generated: 2026-05-23T13:02:04.325520+00:00 -->
<!-- kb_daily_digest_date: 2026-05-23 -->
# KB Daily Digest Source — 2026-05-23

このページは、knowledge-base-llm の日次更新を NotebookLM に読み込ませるための公開向けソースページです。
Discord通知よりも文脈を厚めに残し、Podcast化しやすいように、今日追加・更新されたソース、概念、地図を文章中心で整理します。

## 今日の全体像

# KB Daily Digest - 2026-05-23

今日の knowledge-base-llm は、2つの更新クラスターが大きい。1つ目は X bookmarks 由来の3本で、MCPのステートレス化、Karpathy系のcoding-agent guidelines、Bunのlifetime-classify workflowが追加された。2つ目は Anthropic/Claude のPDF「The Founder's Playbook」で、AI-native startup のライフサイクル、agent-first organization、ROI/能力投資の地図にかなり強く接続された。全体としては、昨日までの「agent harness の部品が実務者に触れる形で出てきた」という流れが、今日は「その部品をどう組織・プロトコル・起業運営に埋め込むか」へ広がった日だった。

重要ソースの1本目は、MCP 2026-07-28 release candidate の stateless protocol 化。KBでは `wiki/sources/mcp-2026-07-28-release-candidate-stateless-protocol.md` として入り、`context-management-decisions` に接続された。ポイントは、MCPが単なるツール接続の規格ではなく、長期運用されるagent/tool境界の設計課題を持つプロトコルとして見えてきたこと。ステートレス化は、実装・運用・キャッシュ・セッション管理の責務分担を変えるので、エージェントの作業環境を「どこに状態を置くか」という観点で再整理する材料になる。

2本目は Jiayuan/JY Zhang の Karpathy-guidelines-for-coding-agents repo。これは、coding agentをうまく使うための規律を、単発のプロンプトではなくリポジトリ/ルール/レビュー/作業単位の設計として扱う材料だった。KBでは `coding-agent-harness-patterns` に入り、特に rule-update loop、codebase legibility、context-first short iteration のような既存パターンを補強している。Karpathy系のCLAUDE.md文化や「繰り返し指示を作業規則へ昇格する」流れが、個人の使いこなしからチームで再利用できるharness設計へ寄ってきたと読める。

3本目は Bun の lifetime-classify workflow。Claude Codeを使った具体的な分類・調査ワークフローとして、KBでは `wiki/sources/bun-lifetime-classify-claude-workflow-x.md` に入り、`coding-agent-harness-patterns` と `context-management-decisions` を補強した。ここで重要なのは、エージェントの価値が「コードを書く」だけでなく、コードベースや実行時挙動を調べる反復可能な調査手順にある点。うまくいった調査の型を再利用可能なworkflowとして残すことは、まさにharnessの資産化に近い。

もう1つの大きなソースは Anthropic の「The Founder's Playbook」。`wiki/sources/about-hiroppy-founders-playbook.md` が拡張され、`wiki/concepts/ai-native-startup-lifecycle.md` が新規作成された。Idea、MVP、Launch、Scale の各段階でAIをどう使うかを、Chat / Cowork / Code の使い分けや、検証・スコープ・運用・GTMの課題と結びつけて整理している。特に「AIで作る速度が上がるほど、検証不足やスコープ膨張が危険になる」という見方は、KB内の `verification-tax`、`instability-tax`、`agentic-jevons-paradox` と自然につながる。

概念・地図の更新では、`ai-native-startup-lifecycle` が今日の新しい中核概念になった。これは単なるスタートアップ論ではなく、AIが実行コストを下げた後に、どの段階でどんなartifactやgateが必要になるかを見るための運用モデルとして使える。加えて `agent-first-organization`、`ai-adoption-roi-and-capability-investment`、`operations` navigation、`wiki/INDEX.md` が更新され、AI導入を「ツール採用」ではなく、組織の吸収能力・検証能力・運用面の成熟として扱う方向が強まった。

今日の全体トレンドは、「agent harness が個人の作業術から、プロトコル設計・組織設計・起業運営へ拡張している」ことだと思う。MCPはツール接続の状態管理を問い、Karpathy guidelinesとBun workflowはコードベースに対する反復可能なagent作業を問い、Founder Playbookは会社づくりの各段階でAIに何を任せ、何を人間が検証するかを問う。領域は違うが、全部「AIに仕事を渡す前後の構造」を扱っている。

実務上の示唆はかなり明確で、今後のKBでは「良いエージェント利用」をモデル単体で語るより、状態の置き場所、ルールの更新経路、反復workflow、検証gate、組織内の責任者をセットで見る必要がある。特にFounder Playbookは、AI-nativeな小さなチームが速く進めるほど、PMF前の作りすぎ、launch後の運用不足、scale時のfounder knowledgeの属人化が起きやすいことを示す材料として使える。これはエージェント導入のROI地図にも直結する。

NotebookLM Podcast では、まず「今日はagent harnessが、コード作業の外側へ広がった日」と置くと話しやすい。中心に置く3本は MCP stateless RC、Karpathy coding-agent guidelines、Anthropic Founder Playbook。Bun workflowは具体例として挟むと、抽象的な設計論と現場のworkflowがつながる。掘るべき問いは、状態をどこに置くべきか、繰り返し指示をどのタイミングでルール化すべきか、AI-native startupが速く作れる時代にどんな検証gateを残すべきか、の3つ。


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
- [[simon-willison-gitlab-act-2.md]] — Simon Willison on GitLab's Act 2 announcement, organization flattening, smaller empowered R&D teams, and the agentic-era Jevons-style software demand thesis.
- [[google-research-nested-learning-continual-learning.md]] — Google Research on Nested Learning, continuum memory systems, and Hope as a model-internal continual-learning architecture.
- [[anthropic-claude-code-large-codebases.md]] — Anthropic on Claude Code at large-codebase scale: live-code navigation, harness extension points, layered context files, LSP/subagents, and org ownership.
- [[about-hiroppy-founders-playbook.md]] — Anthropic's official founder playbook PDF: AI-native startup lifecycle across Idea, MVP, Launch, and Scale, with Claude Chat/Cowork/Code stage usage, validation gates, agentic technical debt risks, founder bottleneck removal, and moat formation.
- [[izanami-claude-code-large-codebase-best-practices.md]] — Japanese practitioner explainer on Claude Code large-codebase setup: live repo search, thin layered CLAUDE.md, subdirectory startup, hooks, stale-rule pruning, and adoption ownership.
- [[newspicks-harness-engineering-what-is-it.md]] — Japanese explainer separating evaluation harnesses from agent harnesses and decomposing agent harnesses into runtime, context, and safety layers.
- [[tricalt-memory-skills-same-harness-x.md]] — Vasilije / tricalt X Article framing memory and skills as one evolving harness

### Anthropic - The Founder's Playbook

Source note: `wiki/sources/about-hiroppy-founders-playbook.md`

# Anthropic - The Founder's Playbook

## Source metadata
- Raw PDF text: [[../../raw/articles/anthropic-founders-playbook-pdf-2026-05-06.md]]
- Local PDF: [[../../raw/pdfs/anthropic-founders-playbook-2026-05-06.pdf]]
- Prior bookmark capture: [[../../raw/articles/about_hiroppy-founders-playbook-ai-native-startup-x-2026-05-14.md]]
- PDF URL: https://cdn.prod.website-files.com/6889473510b50328dbb70ae6/69fe2a55b93bb0732b1fe33c_The-Founders-Playbook-05062026_v3%20(1).pdf
- Canonical blog URL: https://claude.com/blog/the-founders-playbook
- Publisher: Anthropic / Claude
- Date: 2026-05-06 PDF filename; captured 2026-05-23
- Type: vendor playbook / startup operating guide
- Evidence strength: high for Anthropic's own guidance and product framing; vendor-authored, so claims about AI-native speed and Claude product fit should be treated as product-positioned.

## Summary
Anthropic's playbook remaps the startup lifecycle around AI-native work. It argues that the founder's role shifts from direct execution toward orchestration: using conversational intelligence for research and judgment, Claude Code for agentic coding, and Claude Cowork for recurring operational workflows.

The core lifecycle is four stages: Idea, MVP, Launch, and Scale. Each stage has a goal, exit criteria, predictable failure modes, and stage-appropriate Claude surfaces.

## Key claims
- AI-native startup work compresses timelines, but it does not remove the need for validation, judgment, security, product-market-fit evidence, or operational design.
- In the Idea stage, the main risk is mistaking building for validation. A prototype is a research prop, not evidence by itself.
- In the MVP stage, AI-generated speed creates new debt modes: scope creep without friction, architectural drift, insecure-by-inexperienc

### aweb.ai - How to set up an AI-native organization

Source note: `wiki/sources/aweb-ai-first-company-howto.md`

# aweb.ai - How to set up an AI-native organization

## Source Metadata
- Raw path: raw/articles/aweb-ai-first-company-howto-2026-05-17.md
- Original URL: https://aweb.ai/blog/ai-first-company-howto
- Author: aweb.ai
- Date: 2026-05-17 capture
- Type: company operating-model article / practitioner case study

## Summary
The article argues that AI-native organization design is not just employees using chatbots faster. In an AI-native company, named agents own work surfaces, carry persistent context, message each other directly, and coordinate through durable artifacts such as tasks, decision records, handoffs, status files, release evidence, and signal notes. Humans keep founding judgment, direction, customer trust, hiring, and publishing authority.

The aweb.ai case study describes seven persistent agents plus ephemeral coding agents and two humans. Its main durable claim is not the exact role roster, but the operating discipline: agents need identities, addresses, role docs, a shared taskboard, learning mechanisms, builder/reviewer splits, and artifact-based shared state.

## Key Claims
- AI-assisted work speeds up individual workflows; AI-native organization changes coordination itself.
- Agents should be first-class citizens with stable identities, addresses, named responsibilities, and persistent context.
- Work that matters should produce durable artifacts, not disappear into chat.
- Substantial work needs at least two voices: builder and reviewer.
- Shared state beats status routing: the company should be queryable through taskboards, status files, decision records, and handoffs.
- Solo operators can start with builder+reviewer pairs; organizations should move to named roles when repeated decision surfaces need ownership.
- Feedback should be captured with strengt

### Simon Willison — Thoughts on GitLab Act 2

Source note: `wiki/sources/simon-willison-gitlab-act-2.md`

# Simon Willison — Thoughts on GitLab Act 2

## Metadata
- Raw path: `raw/articles/simon-willison-gitlab-act-2-2026-05-11.md`
- Original/source URL: https://simonwillison.net/2026/May/11/gitlab-act-2/
- Linked primary announcement: https://about.gitlab.com/blog/gitlab-act-2/
- Author: Simon Willison
- Published: 2026-05-11
- Fetched/ingested: 2026-05-12
- Source type: link-blog commentary on GitLab strategy announcement
- Evidence strength: medium for Simon's interpretation and the quoted GitLab claims; lower for forward-looking market predictions because they are strategic/business forecasts and GitLab has a direct commercial incentive

## Summary
Simon Willison reads GitLab's “Act 2” announcement as more than a workforce-reduction note: it is also an organizational redesign and market thesis for the agentic engineering era. The key useful frame is GitLab's belief that cheaper software production will expand demand for software and for developer-platform seats, not merely reduce developer headcount. Simon connects this to a Jevons-paradox-style optimism while explicitly warning that GitLab's incentives make the claim worth discounting.

## Key claims
- GitLab's agentic-era restructuring combines workforce reduction, geographic consolidation, fewer management layers, smaller empowered R&D teams, and a new values framework.
- Flattening management and “player-coach” management are becoming a visible organization-design response to AI-assisted work.
- Smaller end-to-end teams may become more capable when agentic engineering raises each team's execution capacity.
- GitLab's market thesis is Jevons-like: as the cost of producing and managing software collapses, total demand for software and builders expands.
- The same thesis should be treated cautiously because GitLab bene

### Rak — Bun Claude workflow: lifetime-classify

Source note: `wiki/sources/bun-lifetime-classify-claude-workflow-x.md`

# Rak — Bun Claude workflow: lifetime-classify

## Source Metadata
- Raw path: raw/articles/bun-lifetime-classify-claude-workflow-x-2026-05-22.md
- Original URL: https://x.com/rakutek/status/2057632977644081257
- Primary URL: https://raw.githubusercontent.com/oven-sh/bun/23427dbc12fdcff30c23a96a3d6a66d62fdc091d/.claude/workflows/lifetime-classify.workflow.js
- Author: ラク (@rakutek)
- Posted: 2026-05-22T01:21:45.000Z
- Captured: 2026-05-23 via xurl bookmarks capture
- Type: X post / repo workflow promo
- Evidence strength: bookmark commentary plus direct workflow file

## What it says
The Bun repo contains a .claude/workflows/lifetime-classify.workflow.js file that turns a repeatable Claude Code task into a structured workflow. It classifies pointer-like Zig struct fields into Rust ownership categories, verifies uncertain classifications with multiple votes, and synthesizes the results into TSV-style output.

The important KB signal is not just that Bun uses Claude workflows. It is the shape of the workflow itself: explicit phases, a taxonomy, evidence strings, verification on uncertain cases, and a machine-readable output format.

## Key Claims
- Repo-local .claude/workflows files can encode reusable agent procedures.
- Multi-phase workflows can make analysis tasks more inspectable and repeatable.
- Verification can be built into the workflow instead of being left to a human after the fact.
- A small taxonomy can turn a fuzzy classification problem into a structured pipeline.
- Output should be machine-friendly when the task is operational rather than narrative.

## Evidence / Examples
- The file defines Classify, Verify, and Synthesize phases.
- The classification stage records evidence and a confidence level for each field.
- The verify stage refutes uncertain or samp

### Jiayuan (JY) Zhang — Karpathy Guidelines for coding agents

Source note: `wiki/sources/jiayuan-jy-zhang-karpathy-guidelines-for-coding-agents-github-repo-x.md`

# Jiayuan (JY) Zhang — Karpathy Guidelines for coding agents

## Source Metadata
- Raw path: raw/articles/jiayuan-jy-zhang-karpathy-guidelines-for-coding-agents-github-repo-x-2026-01-27.md
- Original URL: https://x.com/jiayuan_jy/status/2016000962641723668
- Primary URL: https://github.com/multica-ai/andrej-karpathy-skills
- Author: Jiayuan (JY) Zhang (@jiayuan_jy)
- Posted: 2026-01-27T04:10:59.000Z
- Captured: 2026-05-23 via xurl bookmarks capture
- Type: X post / GitHub repo promo
- Evidence strength: bookmark text plus GitHub repo README preview

## What it says
The repo packages a small, reusable CLAUDE.md-style ruleset derived from Andrej Karpathy's observations about LLM coding pitfalls. It presents four principles that are meant to be copied into projects or installed as a Claude Code plugin: think before coding, simplicity first, surgical changes, and goal-driven execution.

The repository's point is not just the rules themselves. It is the packaging choice: turn advice into a portable repository artifact, keep the shared file short, and leave project-specific details in local overrides rather than bloating the common ruleset.

## Key Claims
- Karpathy-style coding guidance can fit into one compact rule file.
- The four rules are explicitly operational, not inspirational.
- The repo is intended to be reused across projects as a plugin or file template.
- The shared rules should stay separate from project-specific instructions.
- Goal-driven execution should express success criteria and verification loops, not vague imperatives.

## Evidence / Examples
- The repo README quotes Karpathy's own observations about model confusion, overcomplication, and unrelated edits.
- It translates those observations into short rule sections with actionable language.
- It provides

### MCP — 2026-07-28 release candidate

Source note: `wiki/sources/mcp-2026-07-28-release-candidate-stateless-protocol.md`

# MCP — 2026-07-28 release candidate

## Source Metadata
- Raw path: raw/articles/mcp-2026-07-28-release-candidate-stateless-protocol-x-2026-05-22.md
- Original URL: https://x.com/dsp_/status/2057780712187580924
- Primary URL: https://blog.modelcontextprotocol.io/posts/2026-07-28-release-candidate/
- Author: David Soria Parra (@dsp_)
- Posted: 2026-05-22T11:08:48.000Z
- Captured: 2026-05-23 via xurl bookmarks capture
- Type: X post / official protocol announcement
- Evidence strength: bookmark summary plus official MCP release-candidate article

## What it says
The MCP 2026-07-28 release candidate makes the protocol stateless at the transport layer: the initialize/initialized handshake disappears, session ids disappear, and requests can land on any server instance. The same release also formalizes extensions, hardens authorization, and introduces a deprecation policy so the protocol can evolve without ad hoc breakage.

The practical deployment angle is just as important as the protocol shift. The RC moves MCP toward ordinary HTTP routing and caching: Mcp-Method and Mcp-Name make routing easier, ttlMs and cacheScope give cache semantics to list/read results, and server/discover lets clients fetch capabilities on demand.

## Key Claims
- MCP is becoming stateless at the protocol layer.
- The session-oriented handshake is removed.
- Extensions are now first-class, including MCP Apps and Tasks.
- Authorization is being aligned more closely with OAuth / OpenID Connect reality.
- The spec now has a formal deprecation policy.
- Stateless transport makes ordinary HTTP infrastructure more viable for MCP deployments.

## Evidence / Examples
- The official RC shows the new single-request shape with protocol-version and method headers.
- It explicitly explains that no sticky sessio

## 更新された概念・地図

### Agent-First Organization

KB note: `wiki/concepts/agent-first-organization.md`

---
aliases:
  - Agent-First Organization
  - AI-Native Organization
  - AI-First Company
---

# Agent-First Organization

## Definition
An agent-first organization is an operating model where named AI agents own durable work surfaces, carry persistent context, coordinate through shared artifacts, and communicate with each other directly, while humans retain direction, judgment, trust work, and external accountability.

## Why It Matters
Most AI adoption starts as individual acceleration. Agent-first organization design asks a harder question: what changes when the company itself coordinates through agents, taskboards, status files, decision records, handoffs, and review loops rather than through humans relaying every message?

## Minimum Operating Surfaces
- Named agent identities and addresses.
- Written role docs such as AGENTS.md or CLAUDE.md.
- Shared taskboard with IDs, owners, status, and priorities.
- Decision records and status files.
- Structured handoffs between role surface

### AI-Native Startup Lifecycle

KB note: `wiki/concepts/ai-native-startup-lifecycle.md`

---
aliases:
  - AI-Native Startup Lifecycle
  - AI-native startup stage model
  - Founder orchestration lifecycle
---

# AI-Native Startup Lifecycle

## Definition
An operating model for startups where AI is treated as core infrastructure across the Idea, MVP, Launch, and Scale stages, changing the founder role from direct execution toward orchestration of research, coding, operational, and go-to-market agents.

## Why It Matters
AI lowers the cost of building, but it also removes natural bottlenecks that used to force validation, scope discipline, security review, and operational handoff. The lifecycle lens keeps the question stage-specific: not just "can AI build this?" but "what evidence, artifact, or operating surface is needed at this stage?"

## Stage Pattern
- Idea: validate problem-solution fit before building; use AI for adversarial research, competitive mapping, interview design, and synthesis.
- MVP: build the smallest product that can generate product-market-fit evidence; 

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
- [[../concepts/structured-handoff-artifacts.md]]
- [[../concepts/context-resets

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

## NotebookLM Podcast用メモ

- まず今日の全体トレンドを話してから、重要ソースを3本に絞って深掘りする。
- ソース単体の紹介で終わらせず、既存KBの概念や地図がどう更新されたかを会話に含める。
- 最後に、明日以降の調査問いを2〜3個提示する。
