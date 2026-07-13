<!-- generated: 2026-07-13T13:01:56.989776+00:00 -->
<!-- kb_daily_digest_date: 2026-07-13 -->
# KB Daily Digest Source — 2026-07-13

このページは、knowledge-base-llm の日次更新を NotebookLM に読み込ませるための公開向けソースページです。
Discord通知よりも文脈を厚めに残し、Podcast化しやすいように、今日追加・更新されたソース、概念、地図を文章中心で整理します。

## 今日の全体像

# KB Daily Digest 2026-07-13

今日の knowledge-base-llm は、UTC 2026-07-13 00:06 の `KB ingest: xurl bookmarks 2026-07-13` によって、raw article 2本、raw bookmark snapshot 1本、wiki source 2本、concept 4本、map 1本、`wiki/INDEX.md` が追加・更新された。新規ソースは、Anthropic公式の Claude Fable 5 access extension と、nogu66 さんの asc CLI / App Store Connect / Agent Skills に関する Zenn 記事共有である。大きな流れとしては、エージェント活用が「モデルの賢さ」だけではなく、利用可能な rate limit / capacity headroom と、現場業務をCLIやskillへ落とす tool-access layer の両方に依存していることが強く出た日だった。

1本目の重要ソースは、Anthropic公式アカウントによる Claude Fable 5 access extension。Claude Fable 5 access が paid plans across で延長され、Claude Code の weekly rate limits が July 19 まで 50% higher のまま維持される、という時間つきの availability update である。KBでは `long-running-agents` と `llm-inference-performance` に接続され、長時間・高頻度に回す coding agent では、モデル選択だけでなく、週次上限、利用枠、アクセス延長がそのまま実務上の設計条件になることを示す source anchor になった。

この Anthropic ソースの読みどころは、単なる「新モデルが使える」という告知ではなく、agent product の表面に capacity policy が出てきている点にある。long-running agents は、夜間作業、複数サブエージェント、CI的な反復、review loop などで、短いチャットよりも消費が予測しにくい。だからこそ、Claude Code の rate limit が一時的に 50% 増えるという情報は、開発者体験の細部ではなく、どの程度の自律作業を設計できるかを左右する運用情報として扱う価値がある。

2本目の重要ソースは、nogu66 さんの asc CLI と App Store Connect operations の記事共有。bookmark時点の evidence は X投稿と linked article title が中心だが、App Store Connect の dashboard-heavy な作業を terminal と AI agent / Agent Skills に寄せるという方向性が明確に示されている。KBでは `navigable-agent-skills` と `tool-accessibility` に追加され、release management のような人手の多い運用タスクを、agent がたどれるCLI操作とskillの組み合わせに変換する例として扱われた。

この asc CLI ソースは、agent harness の実務化を考える上でかなりわかりやすい。App Store Connect のような管理画面作業は、手順が決まっている一方で、状態確認、権限、承認、最終判断が絡む。そこで重要なのは、agent にブラウザを雑に操作させることではなく、CLIで明示的な操作面を作り、その上に skill として手順、前提、確認ポイント、禁止事項を重ねることだ。これは `tool-accessibility` の「ツールを渡すだけでは足りず、agentが迷わず使える操作面と安全境界が必要」という論点を補強している。

3本目として扱うべき補助ソースは、`raw/x/bookmarks/bookmarks-20260713T0000Z.json` そのもの、つまり日次 bookmark ingest の選別結果である。`wiki/INDEX.md` の recent additions には、Anthropic と asc CLI を追加しつつ、article-card-only の designers-OSS bookmark、薄い subagent-inheritance reply、既出の harness / design / bookmark duplicates はスキップしたと記録された。これは、KBが単にフィードを保存する場所ではなく、薄い信号、重複、既存概念への接続可能性を見て、source note 化するかどうかを選ぶ編集レイヤーを持っていることを示している。

更新された概念面では、`long-running-agents` と `llm-inference-performance` に Anthropic の availability update が入り、実行時間・自律性・rate limit・inference capacity のつながりが少し太くなった。一方で、`navigable-agent-skills` と `tool-accessibility` には asc CLI が入り、skillを「知識を読むための文書」だけではなく、実際の業務ツールを安全に操作するためのナビゲーション層として見る線が補強された。どちらも agent harness の地味だが重要な部品で、片方は runtime headroom、もう片方は operational surface である。

`wiki/maps/coding-agent-harness-patterns.md` には、July 2026 xurl bookmarks ingest として2つの追記が入った。Anthropic の更新は rate limits と paid-plan availability が agent-product surface の一部であること、nogu66 さんの記事は App Store Connect release work が dashboard clicking から terminal-plus-skill workflow へ移ることを示す、という整理である。今日の全体トレンドを一言で言えば、coding agent harness は「大きなplatform」だけではなく、capacity policy、CLI、skill、選別されたsource note のような小さな運用面の積み重ねで強くなる、という方向だった。

実務上の示唆は2つある。第一に、長時間エージェントを前提にした作業設計では、rate limit を後から気にするのではなく、最初からスケジューリング、並列数、再試行、モデル切り替え、作業粒度の設計に入れる必要がある。第二に、手順化できる業務は「AIに任せる」前に、CLIやAPI、skill、承認点、ログを整備したほうがよい。今日のKB更新は、agentができることを増やすには、モデルの性能と同じくらい、周辺の実行環境と操作面を整える必要があることを示している。

次に追うべき問いは、Claude Code の一時的な rate-limit 増加がどのような利用パターンに効いているのか、release operations の中でどの操作をskill化し、どの操作を人間の明示承認に残すべきか、そして日次bookmark ingest のスキップ判断を将来のKB lintやsource trust mapにどう反映するかである。今日は追加本数こそ少ないが、agent harness を「使える状態」にするための capacity と tool surface の両側が更新された、実務寄りの一日だった。

## Important Sources

- Anthropic - Claude Fable 5 access extension: `wiki/sources/anthropic-claude-fable-5-access-extension-x-2026-07-12.md`
- nogu66 - asc CLI and App Store Connect operations: `wiki/sources/nogu66-asc-cli-app-store-connect-x-2026-07-11.md`
- Daily xurl bookmark snapshot and selection record: `raw/x/bookmarks/bookmarks-20260713T0000Z.json`

## Changed Concepts And Maps

- `wiki/concepts/long-running-agents.md`
- `wiki/concepts/llm-inference-performance.md`
- `wiki/concepts/navigable-agent-skills.md`
- `wiki/concepts/tool-accessibility.md`
- `wiki/maps/coding-agent-harness-patterns.md`


## 重要ソース

### Anthropic - Claude Fable 5 access extension

Source note: `wiki/sources/anthropic-claude-fable-5-access-extension-x-2026-07-12.md`

# Anthropic - Claude Fable 5 access extension

## Source Metadata
- Raw path: `raw/articles/anthropic-claude-fable-5-access-extension-x-2026-07-12.md`
- Raw bookmark capture: `raw/x/bookmarks/bookmarks-20260713T0000Z.json`
- Original URL: https://x.com/i/status/2076351399999557669
- Author: Claude / @claudeai
- Posted: 2026-07-12T17:02:05.000Z
- Captured: 2026-07-13 via xurl bookmarks capture
- Type: X post / product availability update
- Evidence strength: bookmark snapshot metadata plus official account announcement text
- Public metrics at capture: 56810 likes, 5600 reposts, 5210 replies, 6720 quotes, 4645 bookmarks, 10328247 impressions

## Summary
Anthropic says Claude Fable 5 access will remain extended across paid plans and that Claude Code weekly rate limits stay 50% higher through July 19. This reads as a concrete capacity-policy update: Anthropic is still actively shaping access around the load generated by the new model tier.

## Key Claims
- Claude Fable 5 access remains extended across paid plans.
- Claude Code weekly rate limits stay 50% higher through July 19.
- Access policy and rate limits are part of the practical product surface, not just backend implementation details.

## Evidence / Examples
- The post text states the paid-plan extension and the 50% higher limit directly.
- Because the post comes from the official Anthropic account, the claim is first-party and time-bounded.
- The explicit July 19 date gives this note a concrete operational window.

## Evidence Quality
- Source type: official product availability update
- Confidence: high for the access and limit claim, medium for any inference about demand pressure
- Supports: long-running-agents, llm-inference-performance, harness-engineering, agent-autonomy
- Main limitations: the post does not e

### nogu66 - asc CLI and App Store Connect operations

Source note: `wiki/sources/nogu66-asc-cli-app-store-connect-x-2026-07-11.md`

# nogu66 - asc CLI and App Store Connect operations

## Source Metadata
- Raw path: `raw/articles/nogu66-asc-cli-app-store-connect-x-2026-07-11.md`
- Raw bookmark capture: `raw/x/bookmarks/bookmarks-20260713T0000Z.json`
- Original URL: https://x.com/i/status/2075898501909938318
- Primary URL: https://zenn.dev/nogu66/articles/asc-cli-app-store-connect
- Author: nogu66 / @_nogu66
- Posted: 2026-07-11T11:02:25.000Z
- Captured: 2026-07-13 via xurl bookmarks capture
- Type: X post / article share
- Evidence strength: bookmark snapshot metadata plus linked article title
- Public metrics at capture: 17 likes, 1 reposts, 2 replies, 3 quotes, 19 bookmarks, 5021 impressions

## Summary
This bookmark points to a Zenn article about using asc CLI and Agent Skills to operate App Store Connect from the terminal and via AI agents. The practical signal is that app-release operations can be reframed as a navigable tool-and-skill workflow rather than a dashboard-only chore.

## Key Claims
- asc CLI can handle App Store Connect from the terminal.
- Agent Skills can delegate the workflow to Claude Code and Codex.
- App Store Connect tasks are a good candidate for an explicit tool-access layer.

## Evidence / Examples
- The bookmark text says the author is replacing manual App Store Connect dashboard work with asc CLI and Agent Skills.
- The linked article title directly names terminal and AI control.
- The low but nonzero engagement is enough for a narrow workflow note, though not for a broad adoption claim.

## Evidence Quality
- Source type: X post / article share
- Confidence: medium for the workflow framing, lower for the generalization to all release operations
- Supports: navigable-agent-skills, tool-accessibility, harness-engineering, context-first-development
- Main limitations: the

## 更新された概念・地図

### LLM Inference Performance

KB note: `wiki/concepts/llm-inference-performance.md`

---
aliases:
  - LLM Inference Performance
  - Time to First Token
  - Inter-Token Latency
  - TTFT
  - ITL
---

# LLM Inference Performance

## Definition
The runtime behavior of an LLM serving request, especially the latency, memory, and throughput tradeoffs between prompt processing and token streaming.

## Why It Matters
Agent and harness design often treats context as only a reasoning-quality input. Inference performance adds another constraint: longer prompts, larger caches, and longer outputs change latency and concurrency even when answer quality improves.

## Core Distinction
- **Prefill:** process the full prompt before the first output token. Usually parallel and compute-bound; measured by time-to-first-token (TTFT).
- **Decode:** generate output one token at a time after prefill. Usually sequential and memory-bound; measured by inter-token latency (ITL).

## Operational Implications
- If an agent is slow to start, inspect prompt length, retrieved context, tool-output bloat,

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

### Tool Accessibility

KB note: `wiki/concepts/tool-accessibility.md`

---
aliases:
  - Tool Accessibility
---

# Tool Accessibility

## Definition
The degree to which the tools humans rely on are exposed in forms agents can discover and use effectively.

## Why It Matters
If agents cannot access the relevant tools and context, their practical usefulness stays artificially low.

## Related Concepts
- [[harness-engineering]]
- [[agent-recognizable-repository]]
- [[coding-agents]]

## Supporting Sources
- [[../sources/gargetisha-openclaw-under-the-hood-x-article.md]]
- [[../sources/ignorance-ai-emerging-harness-engineering-playbook.md]]
- [[../sources/anthropic-harnessing-claudes-intelligence.md]]
- [[../sources/anthropic-claude-code-on-the-web-docs.md]]
- [[../sources/anthropic-claude-code-skills-docs.md]]
- [[../sources/anthropic-claude-code-web-setup-x.md]]
- [[../sources/storybook-mcp-react-blog.md]]
- [[../sources/browser-use-cli-2-changelog.md]]
- [[../sources/google-gemma-4-blog.md]]
- [[../sources/difit-review-blog.md]]
- [[../sources/jerry-liu-rese

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



## NotebookLM Podcast用メモ

- まず今日の全体トレンドを話してから、重要ソースを3本に絞って深掘りする。
- ソース単体の紹介で終わらせず、既存KBの概念や地図がどう更新されたかを会話に含める。
- 最後に、明日以降の調査問いを2〜3個提示する。
