<!-- generated: 2026-06-12T13:01:35.199668+00:00 -->
<!-- kb_daily_digest_date: 2026-06-12 -->
# KB Daily Digest Source — 2026-06-12

このページは、knowledge-base-llm の日次更新を NotebookLM に読み込ませるための公開向けソースページです。
Discord通知よりも文脈を厚めに残し、Podcast化しやすいように、今日追加・更新されたソース、概念、地図を文章中心で整理します。

## 今日の全体像

# KB Daily Digest 2026-06-12

今日の knowledge-base-llm は、Fable 5 / Mythos 5 世代の強いモデルを「単発プロンプト」ではなく、ループ、ルーチン、ファイルベースの記憶、ハンドオフで運用する方向に大きく寄った更新でした。UTC 2026-06-12 の新規 ingest は 3 コミットで、X ブックマーク由来の raw 記録が 7 件、wiki/source ノートが 7 件追加され、`agent-knowledge-loop`、`loop-engineering`、`long-running-agents`、`structured-handoff-artifacts`、`context-file-system`、`skill-optimization` などの概念ページが更新されています。

全体トレンドは、「モデルが強くなるほど、価値の中心がプロンプト文面から運用ループの設計へ移る」というものです。0xCodez の Fable 5 self-improving agent system 記事は本文の完全取得まではできていませんが、公開断片からは loops、dynamic workflows、routines を組み合わせる方向が示されていました。KB 側ではこれを、モデル自身が重みを更新する意味の自己改善ではなく、外部化されたルーチン、スキル、ワークフロー、検証ゲートを継続的に改善していく実務パターンとして整理しています。

重要ソースの1本目は、0xCodez の「Build self-improving agent system with Fable 5」です。14ステップ本文は未取得なので強い根拠としては扱わず、Fable 5 周辺の実践者が「ループを設計する」「動的ワークフローを使う」「ルーチン化する」という語彙で新世代モデルの使い方を説明し始めている、という弱いが有用な市場シグナルとして取り込みました。この更新により、`agent-knowledge-loop` と `skill-optimization` には「自己改善」という言葉を過大解釈しないための注意が追加されています。

重要ソースの2本目は、Harry Tandy による Fable 5 overnight sub-agent setup の投稿です。こちらも10ステップ全体は取得できていませんが、見えている範囲だけでも `CLAUDE.md` にスタック、コマンド、コードスタイル、禁止ファイル、レビュー規則を置き、`PROJECT_MEMORY.md` に検証済み事実、失敗した試行、前回セッション、次回実行を置くという、かなり実用的な最小構成が示されています。KB ではこれを `context-file-system`、`long-running-agents`、`structured-handoff-artifacts` に接続し、夜間サブエージェントや長時間実行を増やす前に必要な文脈基盤として位置づけました。

重要ソースの3本目は、Cognition の Devin CLI `/handoff` オープンソース化です。投稿の取得内容は短いものの、「ラップトップを閉じてもクラウド側でエージェントが作業を続ける」という分離が明確で、これは長時間エージェントのプロダクトプリミティブとして重要です。KB の既存テーマである long-running agents、structured handoff、cloud agents と自然につながり、作業の継続性をチャット履歴ではなく、クラウド常駐の実行状態と明示的なハンドオフ機構で支える流れを補強しています。

周辺ソースでは、社内メンバーだけがアクセス可能な CLI / MCP を作るという farstep の記事カード、Figma 公式 Chrome 拡張で Web UI を編集可能レイヤーとして Figma に取り込む話、Apple Foundation Models framework から Claude を呼べるという ClaudeDevs の投稿、Apple Container 1.0 リリースが追加されました。これらは一見ばらばらですが、共通して「AIエージェントの作業面が、チャット単体から、社内権限、デザイン構造、Apple ネイティブ統合、ローカルサンドボックスへ広がっている」という読み方ができます。

概念更新としては、`loop-engineering` に self-improving agent claims を外部化されたループ改善とモデル内部の継続学習に分けて扱う注意が入り、`skill-optimization` には実践者の自己改善レシピを「固定モデルの周囲にある routine / skill 改善」と見る整理が追加されました。`context-file-system` では `CLAUDE.md` と `PROJECT_MEMORY.md` の分担が、`structured-handoff-artifacts` では PROJECT_MEMORY 風ファイルが軽量な引き継ぎ成果物になることが明示されました。

実務上の読みどころは、強いモデルを使うほど「どこまで任せるか」より先に「何を読ませ、何を禁止し、どこに状態を残し、どの証拠で完了判定するか」を決める必要がある点です。今日の更新は、長時間・夜間・クラウド常駐のエージェント運用に対して、コンテキストファイル、ハンドオフ、アクセス制御、検証ゲートを同じ地図上に置き直す更新になっています。

次に追う問いは、Fable 5 系の「自己改善」記事本文や動画内チェックリストをどこまで一次情報として取得できるか、Devin `/handoff` のオープンソース実装がどの粒度で状態を保存・移送しているか、社内 CLI / MCP のアクセス制御を KB の tool-access / gateway-control-plane にどう接続するかです。Podcast では、自己改善という言葉の危うさ、夜間サブエージェントを安全に回す最小ファイル構成、そしてクラウド handoff がもたらす働き方の変化を軸に掘るとよさそうです。

## 重要ソース3本

- `wiki/sources/0xcodez-fable-5-self-improving-agent-system-x-2026-06-11.md`
- `wiki/sources/harrytandy-fable-5-overnight-subagents-setup-x-2026-06-11.md`
- `wiki/sources/cognition-devin-handoff-open-source-x.md`

## 更新された主なKBノート

- `wiki/concepts/agent-knowledge-loop.md`
- `wiki/concepts/context-file-system.md`
- `wiki/concepts/long-running-agents.md`
- `wiki/concepts/loop-engineering.md`
- `wiki/concepts/structured-handoff-artifacts.md`
- `wiki/concepts/skill-optimization.md`
- `wiki/navigation/operations.md`


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

### Harry Tandy - Fable 5 overnight sub-agent setup

Source note: `wiki/sources/harrytandy-fable-5-overnight-subagents-setup-x-2026-06-11.md`

# Harry Tandy - Fable 5 overnight sub-agent setup

## Metadata
- Source: X post by Harry Tandy
- URL: https://x.com/harrytandy/status/2065112964768645150
- Author: Harry Tandy (@HarryTandy)
- Date: 2026-06-11
- Raw capture: [[../../raw/x/harrytandy-fable-5-overnight-subagents-setup-x-2026-06-11.md]]
- Quoted source: [[0xcodez-fable-5-self-improving-agent-system-x-2026-06-11.md]]
- Evidence quality: partial text capture; X API exposed only the beginning of the 10-step setup and a video attachment, not a full transcript.

## Summary
Harry Tandy reframes Boris Cherny's reported overnight sub-agent workflow as a copyable Fable 5 setup. The visible setup starts with two file-backed context artifacts: `CLAUDE.md` for project operating rules and `PROJECT_MEMORY.md` for durable state across sessions. This strengthens the KB's pattern that long-running coding-agent work needs explicit context files and handoff memory before it can safely run overnight or across many subagents.

## Key Claims
- Overnight or background sub-agent work depends on explicit project rules and persistent memory, not only model strength.
- `CLAUDE.md` acts as a repo-local operating contract: stack, commands, style, forbidden files, and review rules.
- `PROJECT_MEMORY.md` acts as a continuation surface: verified facts, failed attempts, last session, and next run.
- The post connects Fable 5 practitioner guidance to routines, loops, and long-running sub-agent operation.

## Evidence / Examples
- The X API capture includes the visible text for steps 1 and 2.
- The post quotes the earlier 0xCodez Fable 5 self-improving agent article.
- Public search results around the Boris quote point to secondary reporting that Cherny runs multiple Claude Code sessions with many subagents and uses `/loops` and Routines for

### 0xCodez - Fable 5 self-improving agent system

Source note: `wiki/sources/0xcodez-fable-5-self-improving-agent-system-x-2026-06-11.md`

# 0xCodez - Fable 5 self-improving agent system

## Metadata
- Source: X Article shared by Codez
- URL: https://x.com/0xcodez/status/2065089060104720776
- Article URL: https://x.com/0xCodez/article/2065089060104720776
- Author: Codez (@0xCodez)
- Date: 2026-06-11
- Raw capture: [[../../raw/articles/0xcodez-fable-5-self-improving-agent-system-x-2026-06-11.md]]
- Evidence quality: partial capture; X API provided metadata and title, while body-level claims are inferred only from public search-visible fragments.

## Summary
This X Article is a practitioner signal that Fable 5 should be used with a self-improving agent-system frame: loops, dynamic workflows, and routines. The durable point is not the exact 14-step checklist, which was not captured, but the implied operating shift from prompting a stronger model directly to designing a recurring process around it.

## Key Claims
- Stronger coding models increase the value of process design around the model: loops, routines, dynamic workflows, and persistent improvement surfaces.
- "Self-improving agent system" should be read as a harness pattern unless stronger evidence shows actual model-weight learning.
- Fable 5 practitioner guidance is converging around larger task scopes plus explicit review/update loops rather than only better single prompts.

## Evidence / Examples
- X API confirms the title, author, date, public metrics, and article attachment.
- Public search snippets expose the article's framing around Fable 5, loops, dynamic workflows, and routines.
- Existing adjacent sources in the KB already support the broader pattern: Lance Martin on designing loops with Fable 5, Anthropic's Fable 5 / Mythos 5 launch cluster, dynamic workflow docs, and SkillOpt-style skill update loops.

## Related Concepts
- [[../concepts/loo

### ClaudeDevs — Apple Foundation Models support for Claude

Source note: `wiki/sources/claude-devs-apple-foundation-models-claude-x.md`

# ClaudeDevs — Apple Foundation Models support for Claude

## Source Metadata
- Raw path: `raw/articles/claude-devs-apple-foundation-models-claude-x-2026-06-10.md`
- Original URL: https://x.com/ClaudeDevs/status/2064756984617021807
- Author: ClaudeDevs (@ClaudeDevs)
- Published: 2026-06-10
- Type: X post / image card
- Capture source: xurl bookmarks capture

## Short Summary
The post says Apple's Foundation Models framework can now call Claude for multi-step reasoning, code generation, and longer-context work. The important signal is that Claude is being embedded into Apple's developer framework surface rather than only used through a standalone chat product.

## Key Claims
- Apple developers can call Claude through the Foundation Models framework.
- The use cases called out are multi-step reasoning, code generation, and longer-context tasks.
- The integration is framed as a developer-facing feature.

## Evidence / Examples
- The bookmark text itself names the supported tasks.
- The linked image card was not separately fetched, so the note stays close to the text evidence.

## Evidence Quality
- Source type: X post / image card
- Confidence: Medium
- Supports: tool accessibility, managed agent surfaces, long-running agent workflows, cross-platform integration
- Main limitations: the visual card was not separately fetched in this ingest
- Best use: as a signal that model access is moving into platform-native developer frameworks

## Related Concepts
- [[../concepts/tool-accessibility.md]]
- [[../concepts/managed-agents.md]]
- [[../concepts/long-running-agents.md]]
- [[../concepts/multi-agent-orchestration.md]]

## KB Contribution
This source widens the KB's integration-surface cluster. It shows Claude being exposed as a callable capability inside another platform's frame

### Cognition — Devin CLI handoff open source

Source note: `wiki/sources/cognition-devin-handoff-open-source-x.md`

# Cognition — Devin CLI handoff open source

## Source Metadata
- Raw path: `raw/articles/cognition-devin-handoff-open-source-x-2026-06-11.md`
- Original URL: https://x.com/cognition/status/2065156301668171873
- Author: Cognition (@cognition)
- Published: 2026-06-11
- Type: X post
- Capture source: xurl bookmarks capture

## Short Summary
The post says `/handoff` is one of Devin CLI's most powerful features and that Cognition has open sourced it. The core idea is that a user can close the laptop while the agent keeps working from the cloud, with the handoff mechanism carrying continuity across sessions.

## Key Claims
- `handoff` is a central Devin CLI feature.
- The feature supports continuation after the local machine is closed.
- Cognition has open sourced the handoff mechanism.

## Evidence / Examples
- The bookmark text directly states that agents keep working from the cloud after the laptop is closed.
- The external quote link suggests the feature is part of a broader Devin workflow discussion, but this ingest did not fetch the quote source.

## Evidence Quality
- Source type: X post / product signal
- Confidence: Medium
- Supports: structured handoff artifacts, long-running agents, background agents, cloud continuation
- Main limitations: the open-source artifact itself was not fetched in this ingest
- Best use: as practitioner evidence that session handoff is becoming a productized, reusable runtime primitive

## Related Concepts
- [[../concepts/structured-handoff-artifacts.md]]
- [[../concepts/long-running-agents.md]]
- [[../concepts/background-agents.md]]
- [[../concepts/context-resets.md]]

## KB Contribution
This source reinforces the KB's handoff cluster with a direct vendor statement that the handoff mechanism itself is worth open sourcing. That is stronge

### farstep_ — private CLI / MCP access control article

Source note: `wiki/sources/farstep-private-cli-mcp-access-x.md`

# farstep_ — private CLI / MCP access control article

## Source Metadata
- Raw path: `raw/articles/farstep-private-cli-mcp-access-x-2026-06-11.md`
- Original URL: https://x.com/farstep_/status/2064860995466809848
- Author: farstep (@farstep_)
- Published: 2026-06-11
- Type: X post / X Article card
- Article title: `社内のメンバーだけがアクセス可能な CLI / MCP を作る`
- Capture source: xurl bookmarks capture

## Short Summary
The article-card title points at a common but under-documented problem: internal CLI and MCP tools need to be accessible only to the right people inside the company. The useful signal is that access control is part of the design, not an afterthought.

## Key Claims
- Internal CLI and MCP tools should not be treated as public by default.
- Access boundaries are a first-class part of the tool design.
- A private tool surface can still be useful if it is packaged well for the company.

## Evidence / Examples
- The bookmark only preserves the article title, so this note keeps the claim level intentionally narrow.
- The title itself is enough to mark the source as a tool-access / security pattern rather than a generic CLI post.

## Evidence Quality
- Source type: X Article card
- Confidence: Medium-low
- Supports: tool accessibility, internal tool scoping, agent-recognizable repositories, gateway/control-plane design
- Main limitations: the article body was not fetched in this ingest
- Best use: as a navigation hint for internal-tool security and access scoping questions

## Related Concepts
- [[../concepts/tool-accessibility.md]]
- [[../concepts/agent-recognizable-repository.md]]
- [[../concepts/gateway-control-plane.md]]

## KB Contribution
This source helps distinguish "a CLI exists" from "a CLI is safely operable inside a company." That boundary is central to turning a

### kgsi — Figma official Chrome extension for editable UI capture

Source note: `wiki/sources/kgsi-figma-editable-layers-chrome-extension-x.md`

# kgsi — Figma official Chrome extension for editable UI capture

## Source Metadata
- Raw path: `raw/articles/kgsi-figma-editable-layers-chrome-extension-x-2026-06-11.md`
- Original URL: https://x.com/kgsi/status/2065116383441191387
- Author: こぎそ (@kgsi)
- Published: 2026-06-11
- Type: X post / video
- Capture source: xurl bookmarks capture

## Short Summary
The post says Figma's official Chrome extension can capture a whole web page or a specific UI and import it into Figma as editable layers rather than a flat image. The useful detail is that the capture stays structured enough to edit as text, frames, images, and shapes.

## Key Claims
- The extension can capture either an entire page or a selected UI region.
- The imported result is editable structure, not just a bitmap.
- The resulting artifact keeps text and layout elements in a form Figma can continue to manipulate.

## Evidence / Examples
- The bookmark text explicitly contrasts editable layers with a pasted image.
- The post had substantial engagement at capture time, but the evidence here is still the bookmark text rather than a product demo transcript.

## Evidence Quality
- Source type: X post / video bookmark
- Confidence: Medium
- Supports: rich agent output artifacts, editable design captures, structured handoff from browser to design workspace
- Main limitations: the release details and demo behavior were not separately fetched in this ingest
- Best use: as a practitioner signal that browser-to-design capture is becoming an editable workflow primitive

## Related Concepts
- [[../concepts/rich-agent-output-artifact.md]]
- [[../concepts/structured-handoff-artifacts.md]]
- [[../concepts/agent-recognizable-repository.md]]

## KB Contribution
This source adds a concrete example of rich output becoming editab

### 渋川よしき — Apple Container 1.0

Source note: `wiki/sources/shibu-jp-apple-container-1-0-x.md`

# 渋川よしき — Apple Container 1.0

## Source Metadata
- Raw path: `raw/articles/shibu-jp-apple-container-1-0-x-2026-06-10.md`
- Original URL: https://x.com/shibu_jp/status/2064572435048145097
- Author: 渋川よしき (@shibu_jp)
- Published: 2026-06-10
- Type: X post / GitHub link
- Repository URL: https://github.com/apple/container
- Capture source: xurl bookmarks capture

## Short Summary
The post announces that Apple Container has reached version 1.0. The linked repository describes a Mac-focused tool for creating and running Linux containers using lightweight virtual machines on Apple silicon.

## Key Claims
- Apple Container is at version 1.0.
- The tool runs Linux containers on Mac using lightweight VMs.
- The implementation is optimized for Apple silicon.

## Evidence / Examples
- The bookmark text directly points to the GitHub repository.
- The repository title in the capture identifies the runtime model clearly enough for KB classification.

## Evidence Quality
- Source type: X post linking to a GitHub repo
- Confidence: Medium
- Supports: long-running agents, background execution environments, tool accessibility, sandboxed local workflows
- Main limitations: the repository contents were not separately fetched in this ingest
- Best use: as infrastructure evidence for local isolated agent environments on Mac

## Related Concepts
- [[../concepts/long-running-agents.md]]
- [[../concepts/background-agents.md]]
- [[../concepts/tool-accessibility.md]]

## KB Contribution
This source adds a concrete Apple-platform runtime to the local-agent environment cluster. The practical value is not just containers in general, but a first-party Mac path for isolated Linux execution.

## Open Questions
- How much of the agent workflow can stay local on Apple silicon before needing remote compu

## 更新された概念・地図

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
- [[compiled-wiki.md]]
- [[obsidian-as-interface.md]]
- [[durability]]
- [[tool-accessibility.md]]

## Supporting Sources
- [[../sources/gargetisha-openclaw-under-the-hood-x-article.md]]
- [[../sources/aiedge-supercharge-claude-memory-x.md]]
- [[../sources/obsidian-mind-github.md]]
- [[../sources/sukh-saroy-obsidian-mind-x.md]]
- [[../sources/karpathy-personal-llm-kb.md]]
- [[../sources/coreyganim-karpath

### Long-Running Agents

KB note: `wiki/concepts/long-running-agents.md`

---
aliases:
  - Long-Running Agents
---

# Long-Running Agents

## Definition
Agents that work on tasks spanning multiple context windows, often across hours or days, while needing to maintain useful continuity.

## Why It Matters
Many practical agent tasks cannot fit cleanly into a single session, so state transfer becomes part of the architecture.

## Related Concepts
- [[durability]]
- [[structured-handoff-artifacts]]
- [[initializer-agent]]
- [[incremental-progress]]
- [[context-resets]]

## Supporting Sources
- [[../sources/anthropic-effective-harnesses-long-running-agents.md]]
- [[../sources/anthropic-cwc-long-running-agents-repo.md]]
- [[../sources/anthropic-harness-design-long-running-apps.md]]
- [[../sources/anthropic-claude-code-web-scheduled-tasks-docs.md]]
- [[../sources/trq212-claude-code-usage-context-management-x.md]]
- [[../sources/arxiv-autogenesis-self-evolving-agent-protocol.md]]
- [[../sources/aparnadhinak-harness-vs-sandbox-trajectory-x.md]]
- [[../sources/sydneyr

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

## Why It Matters
As models handle larger tasks, the operator's leverage shifts from writing one perfect prompt toward defining a loop that can generate work, evaluate it, and converge. This makes loop design a practical sub-surface of [[harness-engineering.md]].

## Related Concepts
- [[harness-engineering.md]]
- [[generator-evaluator-loop.md]]
- [[task-decomposition.md]]
- [[feedback-controls.md]]
- [[heavy-thinking.md]]
- [[long-running-agents.md]]

## Supporting Sources
- [[../sources/rlancemartin-designing-loops-with-fable-5-x-2026-06-09.md]]
- [[../sources/0xcodez-fable-5-self-improving-agent-system-x-2026-06-11.md]]
- [[../sources/harrytandy-fable-5-overnight-subagents-setup-x-2

### Structured Handoff Artifacts

KB note: `wiki/concepts/structured-handoff-artifacts.md`

---
aliases:
  - Structured Handoff Artifacts
---

# Structured Handoff Artifacts

## Definition
Persistent artifacts such as progress logs, feature lists, plans, and commit history that allow one agent session to hand work off to another cleanly.

## Why It Matters
Without structured handoffs, long-running work across multiple context windows becomes brittle and repetitive.

## Related Concepts
- [[initializer-agent]]
- [[rich-agent-output-artifact.md]]
- [[context-resets]]
- [[incremental-progress]]
- [[long-running-agents]]

## Supporting Sources
- [[../sources/openai-harness-engineering.md]]
- [[../sources/anthropic-effective-harnesses-long-running-agents.md]]
- [[../sources/oikon48-team-onboarding-x.md]]
- [[../sources/oikon48-ultraplan-x.md]]
- [[../sources/anthropic-claude-code-ultraplan-docs.md]]
- [[../sources/cursor-pr-demos-x.md]]
- [[../sources/noahzweben-autofix-pr-x.md]]
- [[../sources/aparnadhinak-harness-vs-sandbox-trajectory-x.md]]
- [[../sources/nyk-builderz-4-agent-h

### Agent Knowledge Loop

KB note: `wiki/concepts/agent-knowledge-loop.md`

---
aliases:
  - Agent Knowledge Loop
---

# Agent Knowledge Loop

## Definition
A recurring loop where an LLM ingests sources, compiles notes, answers questions over the resulting wiki, and files useful outputs back into the knowledge base.

## Why It Matters
This loop turns the knowledge base into a compounding system rather than a static archive.

## Related Concepts
- [[compiled-wiki.md]]
- [[knowledge-base-linting.md]]
- [[agent-autonomy.md]]

## Supporting Sources
- [[../sources/karpathy-personal-llm-kb.md]]
- [[../sources/coreyganim-karpathy-second-brain-clearly-explained-x.md]]
- [[../sources/coreyganim-second-brain-monthly-audit-x.md]]
- [[../sources/shannholmberg-llm-wikid-x.md]]
- [[../sources/artemxtech-llm-wiki-vs-notebooklm-x.md]]
- [[../sources/arxiv-externalization-in-llm-agents.md]]
- [[../sources/carnot-cyclist-continual-learning-desiderata-x.md]]
- [[../sources/google-research-nested-learning-continual-learning.md]]
- [[../sources/akshay-pachaar-wiki-plus-graph-db-kb

### Skill Optimization

KB note: `wiki/concepts/skill-optimization.md`

---
aliases:
  - Skill Optimization
  - Text-Space Skill Optimization
  - Trainable Skill Document
---

# Skill Optimization

## Definition
Skill optimization is the practice of improving a reusable agent skill document through scored execution evidence, bounded text edits, and validation gates, while keeping the task-execution model and harness fixed.

## Why It Matters
Skills are increasingly used as procedural memory for agents. If they remain purely hand-written or one-shot generated, they improve only when a human notices a pattern and edits the file. Skill optimization makes the update loop more systematic: traces supply evidence, an optimizer proposes small edits, and held-out checks decide whether the skill actually improved.

## Related Concepts
- [[memory-skill-harness.md]]
- [[rule-update-loop.md]]
- [[trace-driven-improvement.md]]
- [[feedback-controls.md]]
- [[machine-checkable-invariants.md]]
- [[behavioral-stability.md]]
- [[workflow-compilation.md]]
- [[navigable-agent-

### Navigation: Operations / Long-Running Work

KB note: `wiki/navigation/operations.md`

# Navigation: Operations / Long-Running Work

## Use When
The question is about running agents over time: background agents, routines, scheduled work, handoffs, context resets, delegation, or monitoring.
It also covers whether a recurring workflow should stay explicit or be compiled into model behavior.

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
- [[

## NotebookLM Podcast用メモ

- まず今日の全体トレンドを話してから、重要ソースを3本に絞って深掘りする。
- ソース単体の紹介で終わらせず、既存KBの概念や地図がどう更新されたかを会話に含める。
- 最後に、明日以降の調査問いを2〜3個提示する。
