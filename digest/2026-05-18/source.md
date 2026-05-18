<!-- generated: 2026-05-18T13:02:05.630468+00:00 -->
<!-- kb_daily_digest_date: 2026-05-18 -->
# KB Daily Digest Source — 2026-05-18

このページは、knowledge-base-llm の日次更新を NotebookLM に読み込ませるための公開向けソースページです。
Discord通知よりも文脈を厚めに残し、Podcast化しやすいように、今日追加・更新されたソース、概念、地図を文章中心で整理します。

## 今日の全体像

# KB Daily Digest - 2026-05-18

2026-05-18 UTC の knowledge-base-llm は、前日に続いて「AIエージェントをどう組織と作業環境に定着させるか」に寄った更新だった。新規 raw/wiki/source としては、X bookmarks ingest 由来の5件と、Jason Liu の Codex-maxxing heartbeats 節が入り、既存の coding-agent harness / context management / operations navigation が更新された。単発のツール紹介ではなく、長く動くエージェント、ファイルに残る記憶、セキュリティ境界、組織ロールの再設計が同じ束として扱われるようになったのが今日の大きな流れ。

いちばん重要なソースは Jason Liu の「Codex-maxxing」。ここでは Codex を単なるコーディング補助ではなく、ピン留めされた長期スレッド、file-backed memory、heartbeats、browser/computer/connectors、レビュー可能な artifact surface を組み合わせた作業OSとして扱っている。KB側ではこれを \`coding-agent-harness-patterns\` に取り込み、durable operating threads と artifact-native review surface という2つの実務パターンを追加した。特に、継続性をチャット履歴だけに預けず、diff可能なファイル記憶とレビュー面に逃がす点が、OpenClaw運用やNotebookLMページ生成とも直接つながる。

2本目の重要ソースは Keisuke Nishitani の Qiita 記事「AIエージェントを会社で使いたい！→ セキュリティどうするの？」。エージェント導入の論点を、プロンプト・出力・ツール呼び出しという新しい攻撃面として整理し、ログ、リスクスコア、ブロック、承認、監査レポートを agent layer に置くべきだと説明している。これにより \`agent-safety\`、\`tool-accessibility\`、\`gateway-control-plane\` の関係が強くなり、企業導入に必要なのは「賢いモデルを使うこと」だけではなく、何を実行してよいかを制御・記録する harness だという方向が明確になった。

3本目は、Mitchell Hashimoto の投稿を引用した iwashi86 の AI blind faith / cloud-era design conflict のメモ。内容は短いが、現在のAI導入論争を「モデル性能への期待」ではなく「組織設計と判断基準の衝突」として見る視点を足している。これに builder-oriented PdM、Claude Code による management memory、Hermes Agent の X search 事例が並ぶことで、今日の更新は「個人が便利に使うAI」から「組織が役割・記憶・権限・評価を作り直すAI」へ視界を広げている。

更新された地図としては \`coding-agent-harness-patterns\` が最重要。既存の plan files、verifier split、deterministic checks、rule-update loop に加えて、長期運用スレッドと artifact-native review surface が追加され、実装前後だけでなく、運用中の監視・再開・再レビューまで含む harness 像になった。 \`context-management-decisions\` も、file-backed memory と thread continuity を背景に、記憶をどこへ置き、どの粒度で更新し、どうレビューするかを問う方向へ寄っている。

概念面では、\`agent-first-organization\`、\`agent-management\`、\`agent-safety\`、\`background-agents\`、\`context-file-system\`、\`memory-skill-harness\`、\`organizational-intent-clarity\`、\`rule-update-loop\`、\`tool-accessibility\` がまとめて動いた。つまり今日の compile は、単に6本のソースを追加しただけではなく、KB内の「長く動くエージェントを安全に組織へ入れるための語彙」を補強している。特に、heartbeats と security gatekeeper は対になる論点で、前者はエージェントを動かし続ける仕組み、後者は動き続ける対象を逸脱させない仕組みとして読める。

実務上の示唆はかなりはっきりしている。エージェント導入は、ツール選定より先に、記憶の置き場所、承認境界、ログ設計、レビュー面、担当者の役割を決める必要がある。逆に言うと、小さく始めるなら、大きな multi-agent platform を作るより、1つの長期スレッド、1つのファイル記憶、1つの定期 heartbeat、1つのチェックコマンド、1つのレビュー用 artifact を揃える方が早い。今日のKB更新はその最小構成を具体例で支えている。

次に追うべき問いは3つ。第一に、heartbeat 型の自律運用をどこまで「通知・下書き」に留め、どこから「実行」まで許すのか。第二に、agent security gatekeeper のルールは harness 内に置くべきか、既存のDLP/EDR/SIEMに寄せるべきか。第三に、PdMやマネージャーの builder 化、management memory の構造化は、どの artifact と評価基準に落とすと再利用可能になるのか。このあたりを掘ると、agent-first organization の地図がさらに実務寄りに育ちそう。

## Important Sources

- Jason Liu - Codex-maxxing: \`wiki/sources/jason-liu-codex-maxxing-heartbeats.md\`
- Keisuke Nishitani - AI agent security for enterprise adoption: \`wiki/sources/keisuke69-ai-agent-security-enterprise-adoption-qiita.md\`
- iwashi86 - Mitchell Hashimoto on AI blind faith and cloud-era design conflict: \`wiki/sources/iwashi86-mitchellh-ai-blind-faith-cloud-analogy-x.md\`

## Verification Notes

- New/changed material was detected from git log and mtime under \`raw/\`, \`wiki/\`, and \`outputs/\` for 2026-05-18 UTC.
- Key commits: \`bf4c338 Add daily X bookmarks ingest notes\`, \`f7ebd33 Add Codex Maxxing heartbeat notes\`.
- Evidence limits: several X article/card sources expose only title or metadata-level evidence, and their source notes keep confidence low to medium where the body was not captured.


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
- [[izanami-claude-code-large-codebase-best-practices.md]] — Japanese practitioner explainer on Claude Code large-codebase setup: live repo search, thin layered CLAUDE.md, subdirectory startup, hooks, stale-rule pruning, and adoption ownership.
- [[newspicks-harness-engineering-what-is-it.md]] — Japanese explainer separating evaluation harnesses from agent harnesses and decomposing agent harnesses into runtime, context, and safety layers.
- [[tricalt-memory-skills-same-harness-x.md]] — Vasilije / tricalt X Article framing memory and skills as one evolving harness/world-model loop.
- [[1osabori-anthropic-memory-dreaming-jp-x.md]] — Japanese X/video explainer of Anthropic Memory and Dreaming as agent experience accumulation, with secondary-source evidence limits.
- [[jason-liu-codex-maxxing-heartbeats.md]] — Jason Liu on Codex as a durable work sur

### Jason Liu - Codex-maxxing

Source note: `wiki/sources/jason-liu-codex-maxxing-heartbeats.md`

# Jason Liu - Codex-maxxing

## Source Metadata
- Raw path: `raw/articles/jason-liu-codex-maxxing-heartbeats-2026-05-10.md`
- Original URL: https://jxnl.github.io/blog/writing/2026/05/10/codex-maxxing/#heartbeats
- Raw Markdown URL: https://raw.githubusercontent.com/jxnl/blog/main/docs/writing/posts/codex-maxxing.md
- Author: Jason Liu / jxnl
- Date: 2026-05-10
- Type: practitioner blog post

## Summary
Jason Liu frames Codex as a durable operating surface for work, not just a coding assistant. The article's main pattern is an operating loop made from pinned long-running threads, explicit file-backed memory, steering, computer/browser/connectors, remote control, heartbeats, goal criteria, and side-panel artifact review.

## Key Claims
- Long-running pinned threads become useful when they are paired with compaction and external memory artifacts, not only chat history.
- File-backed memory turns thread learning into inspectable, editable, diffable artifacts that survive compaction, thread death, or cache/cost issues.
- Heartbeats make pinned threads recur: a thread can schedule itself, monitor external surfaces, adjust cadence, and keep work moving until a condition is met.
- Connectors plus browser/computer control let recurring loops cross tool boundaries, such as Slack feedback, Remotion rendering, and GUI upload.
- Goals work best when they include a real oracle, such as a unit test suite, rather than merely pointing at an implementation plan.
- The side panel turns artifacts and web surfaces into shared review objects that both the human and agent can inspect and annotate.

## Evidence / Examples
- Chief-of-staff heartbeat: check Slack and Gmail every 30 minutes, prioritize, research answers, and draft replies without sending.
- Feedback heartbeat: monitor a Slack vi

### iwashi86 - Mitchell Hashimoto on AI blind faith and cloud-era design conflict

Source note: `wiki/sources/iwashi86-mitchellh-ai-blind-faith-cloud-analogy-x.md`

# iwashi86 - Mitchell Hashimoto on AI blind faith and cloud-era design conflict

## Source Metadata
- Raw path: raw/articles/iwashi86-mitchellh-ai-blind-faith-x-2026-05-16.md
- Original URL: https://x.com/i/status/2055599591626789303
- Quoted URL: https://twitter.com/mitchellh/status/2055380239711457578
- Author: Corey Ganim / bookmark by iwashi86
- Date: 2026-05-16
- Type: X commentary post

## Summary
The bookmark comments on Mitchell Hashimoto's post as a warning against the current wave of AI blind faith. The analogy is that the disagreement now looks like the infrastructure-design split that showed up during the cloud migration era.

## Key Claims
- Some companies are treating AI with excessive, irrational faith.
- The current debate resembles earlier infrastructure-design conflicts from the cloud era.
- The issue is organizational design and judgment, not just model capability.

## Evidence / Examples
- The post is a commentary on a Mitchell Hashimoto tweet rather than the original post itself.
- The quoted URL is included in the bookmark metadata, which gives provenance but not the full source body.

## Evidence Quality
- Source type: X commentary post.
- Confidence: medium.
- Supports: organizational intent clarity and agent-management thinking.

## Related Concepts
- [[../concepts/organizational-intent-clarity.md]]
- [[../concepts/agent-management.md]]
- [[../concepts/agent-first-organization.md]]

## KB Contribution
Adds an explicit caution that AI adoption debates are often really fights over organizational design, not raw model capability.

## Open Questions
- Which parts of current AI adoption are actually capability gaps versus intent/coordination gaps?
- How should a team tell the difference between justified skepticism and reflexive resistance?

## Backl

### Keisuke Nishitani - AI agent security for enterprise adoption

Source note: `wiki/sources/keisuke69-ai-agent-security-enterprise-adoption-qiita.md`

# Keisuke Nishitani - AI agent security for enterprise adoption

## Source Metadata
- Raw path: raw/articles/keisuke69-ai-agent-security-enterprise-adoption-qiita-2026-05-16.md
- Original URL: https://qiita.com/sharu389no/items/ede7d1c0be4a14024857
- Bookmark post URL: https://x.com/i/status/2055688977735413884
- Bookmark post id: 2055688977735413884
- Author: Keisuke Nishitani (@Keisuke69)
- Date: 2026-05-16
- Type: Qiita article referenced from X bookmark

## Summary
This article argues that AI agent adoption in companies needs a dedicated security layer around the agent's input, output, and tool surfaces. The central move is to treat agent action as something that must be logged, risk-scored, gated, and auditable rather than simply allowed to run because the model is "smart enough."

## Key Claims
- Agent adoption creates a new security surface: prompts, outputs, and tool calls.
- Existing DLP / EDR / SIEM / firewall tooling does not fully cover the agent layer.
- A dedicated gatekeeper can log, score, block, or require approval for dangerous actions.
- Externally sourced text should not be allowed to directly trigger strong actions.
- Compliance and audit reporting should be generated from the recorded action history.
- Self-training rule updates can raise the floor over time, but they do not replace policy review.

## Evidence / Examples
- The article uses Aigis as the concrete OSS implementation example.
- It describes logs that capture time, actor, operation, target, risk score, and disposition.
- It names practical control points such as dangerous shell commands, .env writes, and git push.
- It presents four-stage screening and tag-based isolation as the core guard design.

## Evidence Quality
- Source type: Qiita article.
- Confidence: high for the article's co

### Claude Code - structural memory for management

Source note: `wiki/sources/kenichiota0711-claude-code-management-memory-x.md`

# Claude Code - structural memory for management

## Source Metadata
- Raw path: raw/articles/kenichiota0711-claude-code-management-memory-x-2026-04-13.md
- Original URL: https://x.com/i/status/2043643311039426670
- Article URL: https://x.com/i/article/2043637369711312896
- Author: 太田賢一／Design Mgr (@kenichiota0711)
- Date: 2026-04-13
- Type: X article card

## Summary
The bookmark title suggests a workflow for structuring management memory with Claude Code so that evaluation quality improves. Because the body text was not captured, this note stays deliberately close to the title-level evidence.

## Key Claims
- Management memory can be turned into structured artifacts instead of remaining in chat or in someone's head.
- Better structure appears to improve the quality of evaluation.
- Claude Code is being used as the operational medium for that structuring, not just as a text generator.

## Evidence / Examples
- The bookmark exposes only the title card, so the evidence is limited to the article framing.
- The card still gives a strong signal that management memory belongs in a reusable artifact system.

## Evidence Quality
- Source type: X article card.
- Confidence: low to medium because the body was not captured.
- Supports: memory-skill harness, context-file-system, and rule-update-loop thinking.

## Related Concepts
- [[../concepts/memory-skill-harness.md]]
- [[../concepts/context-file-system.md]]
- [[../concepts/rule-update-loop.md]]
- [[../concepts/agent-knowledge-loop.md]]

## KB Contribution
Adds a management-oriented example of treating memory as a structured artifact that can change evaluation quality.

## Open Questions
- What minimum structure is enough to make management memory reusable?
- How much of the workflow belongs in files versus in chat?

## Backlin

### Hermes Agent - X search without API keys

Source note: `wiki/sources/nukonuko-hermes-agent-x-search-api-free-x.md`

# Hermes Agent - X search without API keys

## Source Metadata
- Raw path: raw/articles/nukonuko-hermes-agent-x-search-x-2026-05-16.md
- Original URL: https://x.com/i/status/2055789273727877128
- Quoted URL: https://twitter.com/xai/status/2055745332919808181
- Author: ぬこぬこ / NUKO 🇯🇵 (@nukonuko)
- Date: 2026-05-16
- Type: X commentary post

## Summary
The bookmark says that X Premium subscribers can use Hermes Agent to search X posts without needing an API key. That makes the post a concrete example of subscription-gated tool access for a background agent workflow.

## Key Claims
- Hermes Agent can search X posts.
- The path described does not require a separate API key.
- X Premium subscription access is enough for the workflow the poster is describing.

## Evidence / Examples
- The bookmark text itself is short but explicit.
- The quoted original X post is included in the metadata for provenance.

## Evidence Quality
- Source type: X commentary post.
- Confidence: medium.
- Supports: background agents, agent management, and tool accessibility.

## Related Concepts
- [[../concepts/background-agents.md]]
- [[../concepts/agent-management.md]]
- [[../concepts/tool-accessibility.md]]

## KB Contribution
Adds a concrete example of consumer-subscription-based access enabling agentic X search without a dedicated API key.

## Open Questions
- Which other subscription-gated tools become practically useful once wrapped as an agent workflow?
- How should a harness distinguish between convenience access and production-grade access?

## Backlinks
- [[../../raw/articles/nukonuko-hermes-agent-x-search-x-2026-05-16.md]]

### PdM - builder-oriented hiring and role design

Source note: `wiki/sources/tsubotax-pdm-builder-x.md`

# PdM - builder-oriented hiring and role design

## Source Metadata
- Raw path: raw/articles/tsubotax-pdm-builder-x-2026-05-14.md
- Original URL: https://x.com/i/status/2054720240144290291
- Article URL: https://x.com/i/article/2054682036863156224
- Author: 坪田 朋 / クラシル CPO (@tsubotax)
- Date: 2026-05-14
- Type: X article card

## Summary
The bookmark title frames a product-management role shift: PdM hiring should be revised so that the role is closer to a builder than to a pure coordinator. The article appears to ground that shift in the Kurashiru hiring criteria.

## Key Claims
- PdMs are increasingly expected to build, not just coordinate.
- Role design and hiring criteria should reflect that shift.
- The article treats the builder framing as a concrete organizational adjustment, not just a slogan.

## Evidence / Examples
- The bookmark capture exposes only the title card, so the evidence is title-level.
- Even at title level, the article is clearly about redefining the PdM role around building.

## Evidence Quality
- Source type: X article card.
- Confidence: low to medium because the body was not captured.
- Supports: agent-first organization, organizational intent clarity, and agent management.

## Related Concepts
- [[../concepts/agent-first-organization.md]]
- [[../concepts/agent-management.md]]
- [[../concepts/organizational-intent-clarity.md]]
- [[../concepts/multi-agent-orchestration.md]]

## KB Contribution
Provides a product-management-facing example of the builder shift that often appears once AI-heavy workflows become operational rather than exploratory.

## Open Questions
- Which PdM tasks remain coordination, and which become hands-on building in AI-heavy teams?
- What evaluation criteria distinguish builder-oriented PdMs from traditional coordination-he

## 更新された概念・地図

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
- [[../concepts/context-resets.md]]
- [[../concepts/context-engineering.md]]
- 

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

## Supporting Sources
- [[../sources/newspicks-harness-engineering-what-is-it.md]]
- [[../sources/anthropic-emotion-concepts.md]]
- [[../sources/anthropic-claude-code-auto-mode.md]]
- [[../sources/anthropic-claude-code-web-scheduled-tasks-docs.md]]
- [[../sources/anthropic-claude-code-on-the-web-docs.md]]
- [[../sources/anthropic-claude-mythos-preview.md]]
- [[../sources/spillwave-ai-coding-hangover-harness-engineering.md]]
- [[../sources/openclaw-release-v2026-4-11-github.md]]
- [[../sources/keisuke69-ai-agent-security-enterprise-adoption-qiita.md]]

- [

### Background Agents

KB note: `wiki/concepts/background-agents.md`

---
aliases:
  - Background Agents
---

# Background Agents

## Definition
Agents launched to work asynchronously while the human focuses elsewhere or is offline.

## Why It Matters
They can create leverage by using otherwise idle time and by parallelizing exploratory work.

## Related Concepts
- [[long-running-agents]]
- [[task-decomposition]]
- [[agent-management]]

## Supporting Sources
- [[../sources/gargetisha-openclaw-under-the-hood-x-article.md]]
- [[../sources/mitchell-hashimoto-ai-adoption-journey.md]]
- [[../sources/anthropic-claude-code-on-the-web-docs.md]]
- [[../sources/anthropic-claude-code-web-scheduled-tasks-docs.md]]
- [[../sources/anthropic-claude-code-scheduled-tasks-x.md]]
- [[../sources/anthropic-claude-code-scheduled-tasks-dynamic-loop-docs.md]]
- [[../sources/noahzweben-dynamic-loop-x.md]]
- [[../sources/oikon48-monitor-tool-x.md]]
- [[../sources/noahzweben-autofix-pr-x.md]]
- [[../sources/openai-codex-plugin-cc-github.md]]
- [[../sources/cursor-3-blog.md]]
- [[.

### Context File System

KB note: `wiki/concepts/context-file-system.md`

---
aliases:
  - Context File System
---

# Context File System

## Definition
A lightweight external-memory pattern where an assistant reads and updates a small set of durable files such as instructions, memory, and project context instead of relying only on chat history or product-native saved memory.

## Why It Matters
It offers a practical middle layer between built-in chat memory and a full knowledge graph or second-brain system. For many workflows, a few well-maintained files provide enough persistence, inspectability, and editability to improve consistency.

## Related Concepts
- [[compiled wiki]]
- [[obsidian as interface]]
- [[durability]]
- [[tool accessibility]]

## Supporting Sources
- [[../sources/gargetisha-openclaw-under-the-hood-x-article.md]]
- [[../sources/aiedge-supercharge-claude-memory-x.md]]
- [[../sources/obsidian-mind-github.md]]
- [[../sources/sukh-saroy-obsidian-mind-x.md]]
- [[../sources/karpathy-personal-llm-kb.md]]
- [[../sources/coreyganim-karpathy-second-

## NotebookLM Podcast用メモ

- まず今日の全体トレンドを話してから、重要ソースを3本に絞って深掘りする。
- ソース単体の紹介で終わらせず、既存KBの概念や地図がどう更新されたかを会話に含める。
- 最後に、明日以降の調査問いを2〜3個提示する。
