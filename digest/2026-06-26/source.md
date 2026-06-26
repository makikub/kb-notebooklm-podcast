<!-- generated: 2026-06-26T13:02:16.632653+00:00 -->
<!-- kb_daily_digest_date: 2026-06-26 -->
# KB Daily Digest Source — 2026-06-26

このページは、knowledge-base-llm の日次更新を NotebookLM に読み込ませるための公開向けソースページです。
Discord通知よりも文脈を厚めに残し、Podcast化しやすいように、今日追加・更新されたソース、概念、地図を文章中心で整理します。

## 今日の全体像

# KB Daily Digest 2026-06-26

2026-06-26 UTC の knowledge-base-llm は、X bookmarks の新規取り込みを起点に、agent identity、enterprise rollout、review capacity、integration/E2E test、goal-setting skill、loop engineering の6本を source note として追加した更新だった。新規 raw は `raw/x/bookmarks/bookmarks-20260626T0000Z.json` と、記事メモ6本、GitHub repository メモ1本。wiki 側では sources 6本が追加され、`agent-management`、`approval-policy`、`loop-engineering`、`managed-agents`、`navigable-agent-skills` と、`agent-harness-landscape`、`coding-agent-cognitive-debt-and-review-capacity`、`harness-engineering-vendor-comparison` の各 map が更新された。

全体トレンドは、「agent をどう使うか」から「agent をどの境界・ループ・証拠で運用するか」への移動として読める。Claude Tag の agent identity は、agent が人間の資格情報を借りるのではなく、独自の認証境界を持つ teammate として扱われる方向を示す。CloudNative の Claude Code enterprise starter kit は、managed settings、permissions、hooks、MCP governance、logs を、導入キットではなく公式 control plane として切り分ける。t-wada 氏の loop engineering / cybernetics framing は、目的・評価・収束という古典的な制御の語彙で、最近の agent loop 設計を捉え直している。

重要ソースの1本目は ClaudeDevs の Claude Tag / agent identity。source note は `managed-agents`、`agent-management`、`multi-agent-orchestration`、`tool-accessibility` に接続された。読みどころは、agent の能力そのものよりも、複数人の channel 上で agent をタグ付けしたときに、agent が自分自身の credentials を持つという access model が前面に出ていること。これは audit log、credential rotation、revocation、workspace/thread/task の境界設計を、managed-agent product の中核に押し上げる。

2本目は CloudNative BLOGs の Claude Code enterprise starter kit best practices。KB上では `approval-policy`、`managed-agents`、`tool-accessibility`、`agent-management` に接続されている。このソースは、企業導入で starter kit が担うべき範囲と、製品側の org-level controls が担うべき範囲を分けて読むための材料になる。権限、hooks、MCP、log visibility は配布テンプレートに閉じ込めるものではなく、運用者が監査・変更・段階導入できる control surface として扱う必要がある。

3本目は `gotalab/goal-setter-skill`。これは荒い依頼を、結果、成功証拠、境界、停止条件を持つ compact goal に変換する Codex skill として追加された。KBでは `navigable-agent-skills`、`workflow-compilation`、`task-decomposition`、`feedback-controls` に効いている。特に、長時間作業に必要なのは巨大な手順書ではなく、実装を過剰指定しない短い goal contract だという点が、今日の loop / evaluation / review capacity の流れときれいにつながる。

review capacity の側では、hiraoku 氏の NewsPicks 共有と erukiti 氏の integration/E2E 重視の投稿が対になっている。前者は、AIが生成速度を上げるほど「人間が全部レビューする」という前提が現実的でなくなると指摘し、後者は unit test より integration/E2E が acceptance criteria と refactor safety を担いやすいという実務寄りの主張を置いている。`coding-agent-cognitive-debt-and-review-capacity` map にはこの2本が入り、生成量ではなく、理解可能性・機械チェック・人間の独立判断をどう保つかがさらに強調された。

loop engineering の更新は、t-wada 氏の cybernetics rediscovery framing によって、最近の agent 用語を古い feedback-control の語彙に接続した点が大きい。`loop-engineering` concept には、評価関数、generator-evaluator loop、自己検証、収束条件が単なるプロンプト技法ではなく、loop そのものを設計対象にする話として追記された。今日のソース群をまとめると、agent identity は「誰が動くか」、approval / enterprise controls は「どこまで動けるか」、goal-setter skill は「何を達成したら止まるか」、E2E は「何をもって通ったと言えるか」を補う。

実務上の読みどころは、agent 導入の設計図を4つの問いに分けられることだと思う。まず agent は人間の代理権限で動くのか、それとも独立した identity と credential を持つのか。次に、組織の許可・hook・MCP・ログは starter kit ではなく control plane に載っているか。さらに、依頼は goal contract として成功証拠・境界・停止条件を持っているか。最後に、review bottleneck を人間の努力だけで吸収しようとしていないか、integration/E2E や評価関数で機械チェック可能な境界を作れているか。

Podcastでは、「agent teammate に identity を与えると、権限設計はどう変わるか」「starter kit と policy layer を混同すると何が危ないか」「goal-setting skill は planning skill ではなく stop-condition skill として読めるのではないか」「AI時代に unit/integration/E2E の価値配分はどう変わるか」を掘るとよい。次に追う問いは、1) per-agent credentials の実装と監査ログの最小要件、2) enterprise starter kit が担ってよい governance 範囲、3) review capacity を測る実務指標、4) loop engineering の評価関数をどの粒度で reusable skill / harness に落とすか、の4つ。


## 重要ソース

### hiraoku - code review should not be a human fantasy

Source note: `wiki/sources/2020-hira-code-review-human-fantasy-newspicks-x-2026-06-25.md`

# hiraoku - code review should not be a human fantasy

## Source Metadata
- Raw path: [[../../raw/articles/2020-hira-code-review-human-fantasy-newspicks-x-2026-06-25.md]]
- Raw bookmark capture: [[../../raw/x/bookmarks/bookmarks-20260626T0000Z.json]]
- Original URL: https://x.com/i/status/2069966824629039262
- Primary URL: https://newspicks.com/news/16930133/body/?from=twitter
- Author: hiraoku / @2020_hira
- Posted: 2026-06-25T02:12:03.000Z
- Captured: 2026-06-26 via xurl bookmarks capture
- Type: X bookmark share of NewsPicks article

## Summary
This bookmark highlights a sharp AI-era review-capacity argument: the real bottleneck is not writing more code, but reading and judging the flood of changes that AI makes possible. The post positions human-only review as increasingly unrealistic at higher throughput.

## Key Claims
- AI changes make review the scarce resource.
- Review should be treated as a system design problem, not just an individual discipline.
- The team needs mechanisms that scale what can be understood and checked.

## Evidence / Examples
- The bookmark text explicitly says the old "humans should review everything" assumption no longer holds.
- It points to the pressure AI puts on senior engineers who become the review bottleneck.
- The framing matches the broader KB theme that throughput without comprehension capacity creates debt.

## Evidence Quality
- Source type: X bookmark share of a NewsPicks article
- Confidence: medium-high for the bottleneck diagnosis
- Supports: review capacity, cognitive debt, evaluation tax
- Main limitations: this note is based on a share and excerpt, not a full article read
- Best use: anchor the argument that review tooling and process must scale with generation speed

## Related Concepts
- [[../concepts/human-in-the-loo

### ClaudeDevs - Claude Tag and agent identity

Source note: `wiki/sources/claudedevs-agent-identity-claude-tag-x-2026-06-25.md`

# ClaudeDevs - Claude Tag and agent identity

## Source Metadata
- Raw path: [[../../raw/articles/claudedevs-agent-identity-claude-tag-x-2026-06-25.md]]
- Raw bookmark capture: [[../../raw/x/bookmarks/bookmarks-20260626T0000Z.json]]
- Original URL: https://x.com/i/status/2070235730295865661
- Primary URL: https://x.com/ClaudeDevs/status/2070235730295865661/video/1
- Author: ClaudeDevs (@ClaudeDevs)
- Posted: 2026-06-25T20:00:35.000Z
- Captured: 2026-06-26 via xurl bookmarks capture
- Type: X post / video card

## Summary
Claude Tag is presented as a productized agent-identity model: when Claude is tagged in a channel, it gets provisioned with its own credentials rather than borrowing a human's identity. That makes the agent look more like a teammate with its own access boundary.

## Key Claims
- Agent identity is becoming a visible product surface.
- Tagged agents can be provisioned with their own credentials.
- Multi-user collaboration changes the importance of identity, not just prompts or tool access.

## Evidence / Examples
- The bookmark text explicitly says Claude gets its own credentials when tagged.
- The post frames this as "the next evolution of agents," which ties identity to the broader managed-agent story.
- The multi-person channel context implies this is about shared workspace use, not solo automation.

## Evidence Quality
- Source type: X post / video card
- Confidence: medium-high for the access-model claim
- Supports: agent identity, credential scoping, collaboration surfaces
- Main limitations: the linked video card does not expose full implementation details
- Best use: connect managed-agent products to authorization and audit questions

## Related Concepts
- [[../concepts/managed-agents.md]]
- [[../concepts/agent-management.md]]
- [[../concepts/mult

### CloudNative BLOGs - Claude Code enterprise starter kit best practices

Source note: `wiki/sources/cloudnative-claude-code-enterprise-starter-kit-best-practices-x-2026-06-24.md`

# CloudNative BLOGs - Claude Code enterprise starter kit best practices

## Source Metadata
- Raw path: [[../../raw/articles/cloudnative-claude-code-enterprise-starter-kit-best-practices-x-2026-06-24.md]]
- Raw bookmark capture: [[../../raw/x/bookmarks/bookmarks-20260626T0000Z.json]]
- Original URL: https://x.com/i/status/2069923527688667446
- Primary URL: https://blog.cloudnative.co.jp/articles/claude-code-enterprise-starter-kit-best-practices/
- Author: 天野 / @AmanoH0909
- Posted: 2026-06-24T23:20:00.000Z
- Captured: 2026-06-26 via xurl bookmarks capture
- Type: X bookmark share of a blog post

## Summary
This bookmark points to a practical enterprise-distribution guide for Claude Code. The framing is that official org-level controls do the hard governance work, while a starter kit helps teams adopt the tool without turning the kit into the policy layer itself.

## Key Claims
- Managed settings and permissions are the official control plane for enterprise use.
- Hooks, MCP governance, and logs matter for safe distribution.
- The starter kit is a deployment helper, not a replacement for org policy.

## Evidence / Examples
- The bookmark description explicitly mentions managed settings, permissions, hooks, MCP control, and log visibility.
- The linked blog title frames the topic as safe enterprise distribution.
- The post is useful because it distinguishes product features from rollout scaffolding.

## Evidence Quality
- Source type: X bookmark share of a blog post
- Confidence: medium-high for the rollout framing
- Supports: enterprise governance, approval policy, tool accessibility
- Main limitations: this note relies on bookmark metadata unless the blog itself is separately ingested
- Best use: remind readers that adoption scaffolding and policy controls are different

### erukiti - integration tests and E2E over unit tests

Source note: `wiki/sources/erukiti-integration-tests-e2e-over-unit-tests-x-2026-06-24.md`

# erukiti - integration tests and E2E over unit tests

## Source Metadata
- Raw path: [[../../raw/articles/erukiti-integration-tests-e2e-over-unit-tests-x-2026-06-24.md]]
- Raw bookmark capture: [[../../raw/x/bookmarks/bookmarks-20260626T0000Z.json]]
- Original URL: https://x.com/i/status/2069931454986064199
- Primary URL: https://twitter.com/nuits_jp/status/2069580384602567100
- Author: erukiti (@erukiti)
- Posted: 2026-06-24T23:51:30.000Z
- Captured: 2026-06-26 via xurl bookmarks capture
- Type: X post / quote post

## Summary
This post is a strong practitioner opinion that the test layers with the most value are integration and E2E, not unit tests. The underlying idea is that the tests closest to real user flow provide the clearest acceptance boundary and the best refactor safety.

## Key Claims
- Unit tests are low leverage compared with integration/E2E in many product workflows.
- Integration and E2E tests can double as acceptance criteria.
- Robust end-to-end coverage makes large refactors easier to justify.

## Evidence / Examples
- The bookmark text states the claim directly and gives two reasons: acceptance criteria and refactor support.
- The post uses a concrete team-development framing rather than a generic test philosophy slogan.
- Because this is a quote post, the strongest evidence is the quoted opinion itself, not a full technical explanation.

## Evidence Quality
- Source type: X quote post
- Confidence: medium
- Supports: real-world evaluation, self-verification, test strategy
- Main limitations: it is an opinionated summary, not a rigorous benchmark
- Best use: reinforce the case for testing at the level that matches actual product risk

## Related Concepts
- [[../concepts/real-world-evaluation.md]]
- [[../concepts/self-verification.md]]
- [[../concep

### Gota - goal-setter-skill repository

Source note: `wiki/sources/gotalab-goal-setter-skill.md`

# Gota - goal-setter-skill repository

## Source Metadata
- Raw path: [[../../raw/repos/gotalab-goal-setter-skill.md]]
- Raw bookmark capture: [[../../raw/x/bookmarks/bookmarks-20260626T0000Z.json]]
- Original URL: https://x.com/i/status/2070071191512174779
- Primary URL: https://github.com/gotalab/goal-setter-skill
- Author: Gota / @gota_bara
- Posted: 2026-06-25T09:06:46.000Z
- Captured: 2026-06-26 via xurl bookmarks capture
- Type: GitHub repository / Codex skill

## Summary
This repository packages goal drafting as a reusable Codex skill. Its purpose is to convert rough requests into compact goals that define the result, evidence, boundaries, and stop conditions without over-specifying the implementation.

## Key Claims
- Goal drafting can be standardized as a skill.
- Long-running work benefits from explicit success evidence and stop rules.
- The right abstraction is a short goal contract, not a giant procedural recipe.

## Evidence / Examples
- The repository README says the skill turns rough long-running work into a compact `/goal`.
- It emphasizes verification targets rather than rule-heavy procedures.
- The install instructions show that the pattern is meant to be reused in both Codex and Claude Code contexts.

## Evidence Quality
- Source type: GitHub repository
- Confidence: high for the repository's own design claims
- Supports: goal-setting, navigable agent skills, workflow compilation
- Main limitations: this note is based on repository documentation, not a live operational deployment study
- Best use: show how request shaping can be turned into a shareable skill artifact

## Related Concepts
- [[../concepts/navigable-agent-skills.md]]
- [[../concepts/workflow-compilation.md]]
- [[../concepts/task-decomposition.md]]
- [[../concepts/feedback-controls.md]]



### t_wada - loop engineering as cybernetics rediscovery

Source note: `wiki/sources/t-wada-loop-engineering-cybernetics-rediscovery-x-2026-06-24.md`

# t_wada - loop engineering as cybernetics rediscovery

## Source Metadata
- Raw path: [[../../raw/articles/t-wada-loop-engineering-cybernetics-rediscovery-x-2026-06-24.md]]
- Raw bookmark capture: [[../../raw/x/bookmarks/bookmarks-20260626T0000Z.json]]
- Original URL: https://x.com/i/status/2069695760464318816
- Primary URL: https://htn.to/U3La2cAJiV
- Author: Takuto Wada (@t_wada)
- Posted: 2026-06-24T08:14:57.000Z
- Captured: 2026-06-26 via xurl bookmarks capture
- Type: X bookmark share of a Hatena blog post

## Summary
This bookmark reinforces the loop-engineering thesis by framing it as a rediscovery of cybernetics: define the target state, attach evaluation, and let the loop converge. The note is useful because it links the current agent-era vocabulary back to older control-theory language.

## Key Claims
- Loop engineering is not just a trendy label; it maps to older feedback-control ideas.
- Evaluation functions are central to agent convergence.
- The useful unit is the loop, not a single prompt or isolated action.

## Evidence / Examples
- The bookmark text directly quotes the loop/cybernetics framing.
- It cites t-wada as having anticipated the structure earlier than the recent term.
- The linked article is a commentary source, so the strongest claim here is about framing rather than implementation.

## Evidence Quality
- Source type: X bookmark share of a blog post
- Confidence: medium
- Supports: loop engineering, feedback controls, generator-evaluator loops
- Main limitations: this is a secondary interpretation of earlier practitioner ideas
- Best use: vocabulary bridge between control theory and agent loop design

## Related Concepts
- [[../concepts/loop-engineering.md]]
- [[../concepts/feedback-controls.md]]
- [[../concepts/generator-evaluator-loop.md]]


## 更新された概念・地図

### Agent Management

KB note: `wiki/concepts/agent-management.md`

---
aliases:
  - Agent Management
---

# Agent Management

## Definition
The human work of assigning tasks, monitoring progress, adjusting the environment, and deciding when to intervene in agent workflows.

## Why It Matters
As agents become more capable, value comes not just from using them but from managing them well. The current source set suggests that workflow design, escalation choices, and background-task supervision are becoming durable human responsibilities rather than temporary scaffolding.

## Related Concepts
- [[agent-captain]]
- [[background-agents]]
- [[harness-engineering]]

## Supporting Sources
- [[../sources/ignorance-ai-emerging-harness-engineering-playbook.md]]
- [[../sources/mitchell-hashimoto-ai-adoption-journey.md]]
- [[../sources/anthropic-claude-code-web-scheduled-tasks-docs.md]]
- [[../sources/nyk-builderz-4-agent-hermes-operator-layer-x.md]]
- [[../sources/sydneyrunkle-agent-harness-vs-runtime-production-x.md]]
- [[../sources/brett-goldstein-agentic-micro-

### Approval Policy

KB note: `wiki/concepts/approval-policy.md`

---
aliases:
  - Approval Policy
---

# Approval Policy

## Definition
A rule system that decides which actions an agent may take automatically and which require explicit user approval.

## Why It Matters
Approval policy is one of the main levers for balancing agent speed and operational safety.

## Related Concepts
- [[human-in-the-loop]]
- [[agent-autonomy]]
- [[agent-safety]]
- [[coding-agents]]

## Supporting Sources
- [[../sources/anthropic-claude-code-auto-mode.md]]
- [[../sources/codex-subagents-docs.md]]
- [[../sources/openai-codex-plugin-cc-github.md]]
- [[../sources/anthropic-claude-code-web-scheduled-tasks-docs.md]]
- [[../sources/claudecode-love-boris-30-claude-code-tips-x.md]]
- [[../sources/blader-adversarial-subagent-review-gate-goal-x-2026-05-23.md]]
- [[../sources/bcherny-auto-mode-multi-clauding-x-2026-05-24.md]]
- [[../sources/cloudflare-agents-stripe-projects-blog.md]]
- [[../sources/openclaw-clawsweeper-repo.md]]
- [[../sources/google-workspace-mcp-servers-docs.md]

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

### Managed Agents

KB note: `wiki/concepts/managed-agents.md`

---
aliases:
  - Managed Agent
  - Managed Agents
---

# Managed Agents

## Definition
Hosted or product-managed agent runtimes that package model execution with tools, permissions, memory, tracing, sandboxing, and operational controls.

## Why It Matters
Managed agents turn agent operation into a deployable surface rather than a local prompt pattern. They make it easier to build roleful domain agents, but they also move important governance decisions into the runtime: what tools are exposed, how memory persists, what is sandboxed, and how humans inspect or intervene.

## Related Concepts
- [[multi-agent-orchestration.md]]
- [[agent-dreaming.md]]
- [[outcomes.md]]
- [[tool-accessibility.md]]
- [[agent-management.md]]
- [[agent-safety.md]]
- [[background-agents.md]]
- [[context-engineering.md]]

## Supporting Sources
- [[../sources/claudeai-claude-managed-agents-intro-x.md]]
- [[../sources/claude-new-in-managed-agents-dreaming-outcomes-orchestration.md]]
- [[../sources/oikon48-claude-ma

### Navigable Agent Skills

KB note: `wiki/concepts/navigable-agent-skills.md`

---
aliases:
  - Navigable Agent Skills
  - Corpus2Skill
  - Hierarchical RAG
---

# Navigable Agent Skills

## Definition
A retrieval architecture where a corpus is compiled into a hierarchy of human/model-readable skill or index files, so an agent can navigate the corpus structure before retrieving underlying documents.

## Why It Matters
It changes the model’s role from passive consumer of search results to active navigator of an information architecture. This is especially useful for broad or completeness-oriented questions where top-k vector retrieval may miss scattered evidence.

## Related Concepts
- [[compiled-wiki.md]]
- [[agent-knowledge-loop.md]]
- [[context-graph.md]]
- [[tool-accessibility.md]]
- [[agent-recognizable-repository.md]]

## Supporting Sources
- [[../sources/coreyganim-karpathy-second-brain-clearly-explained-x.md]]
- [[../sources/knowledgesense-corpus2skill-zenn.md]]
- [[../sources/aws-agent-toolkit-for-aws-x.md]]
- [[../sources/googlecloudjp-agent-skills-repos

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

### Coding-Agent Cognitive Debt and Review Capacity

KB note: `wiki/maps/coding-agent-cognitive-debt-and-review-capacity.md`

# Coding-Agent Cognitive Debt and Review Capacity

## Purpose
Map sources that warn coding-agent throughput can outrun human comprehension, review skill, and implementation judgment.

## Core thesis
The central risk in agentic coding is not only that models make mistakes. It is that teams may produce and accept more code than they can understand, while also weakening the skills required to detect mistakes. Good harnesses must therefore preserve human review capacity and implementation contact, not merely automate more steps.

## Main patterns

### 1. Throughput beyond review capacity
Coding agents can generate large diffs quickly. If review remains shallow, the system shifts risk from typing speed to hidden architectural and maintainability debt.

### 2. Supervision paradox
The human supervisor needs coding, debugging, and architectural skill to judge agent output. Heavy agent use can reduce hands-on practice and erode the very skill required for supervision.

### 3. Coding as design d

### Harness Engineering Vendor / Practitioner Comparison

KB note: `wiki/maps/harness-engineering-vendor-comparison.md`

# Harness Engineering Vendor / Practitioner Comparison

## Purpose
Compare how different sources frame harness engineering, what they optimize for, and what distinctive mechanisms they emphasize.

## Source anchors
- [[../sources/openai-harness-engineering.md]]
- [[../sources/openai-codex-plugin-cc-github.md]]
- [[../sources/codex-subagents-docs.md]]
- [[../sources/anthropic-effective-harnesses-long-running-agents.md]]
- [[../sources/anthropic-harness-design-long-running-apps.md]]
- [[../sources/anthropic-claude-code-on-the-web-docs.md]]
- [[../sources/anthropic-claude-code-skills-docs.md]]
- [[../sources/anthropic-claude-code-web-scheduled-tasks-docs.md]]
- [[../sources/cursor-3-blog.md]]
- [[../sources/anthropic-claude-code-large-codebases.md]]
- [[../sources/anthropic-2026-agentic-coding-trends-report.md]]
- [[../sources/gargetisha-openclaw-under-the-hood-x-article.md]]

## Comparison axes

### OpenAI
- Focus: repository design, machine-enforced invariants, agent-recognizable contex

## NotebookLM Podcast用メモ

- まず今日の全体トレンドを話してから、重要ソースを3本に絞って深掘りする。
- ソース単体の紹介で終わらせず、既存KBの概念や地図がどう更新されたかを会話に含める。
- 最後に、明日以降の調査問いを2〜3個提示する。
