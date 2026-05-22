<!-- generated: 2026-05-22T13:01:19.615622+00:00 -->
<!-- kb_daily_digest_date: 2026-05-22 -->
# KB Daily Digest Source — 2026-05-22

このページは、knowledge-base-llm の日次更新を NotebookLM に読み込ませるための公開向けソースページです。
Discord通知よりも文脈を厚めに残し、Podcast化しやすいように、今日追加・更新されたソース、概念、地図を文章中心で整理します。

## 今日の全体像

# KB Daily Digest - 2026-05-22

今日の knowledge-base-llm は、X bookmarks capture から5本の新規ソースノートを追加し、7つの概念ノートを更新した。全体の流れは、「エージェントをどう賢くするか」よりも一段実務寄りで、エージェントが動く作業面、反復可能なスキル、レビュー、OS/VMまで含めた実行環境の整備に寄っている。昨日の「agent harness がプロダクト化している」という流れを、さらに現場の手触りに寄せた更新になった。

重要ソースの1本目は Claude Code 2.1.147 のリリースクラスター。workflow tool が deterministic multi-agent orchestration のための明示的な機能として入り、さらに `/simplify` が `/code-review` に改名されて effort level を持つようになった。KB上では `multi-agent-orchestration`、`managed-agents`、`tool-accessibility` に接続されていて、複数エージェントの分解・制御・レビューが、プロンプトの工夫ではなく製品上の操作面として扱われ始めたことが重要。

2本目は Jason Liu の「Codex-maxxing」。これは単発のプロンプト術というより、Codex を長時間の仕事が住める場所として使うための daily primitives の話として取り込まれた。persistent threads、memory、steering、connectors、heartbeats、artifact review のような要素がひとまとまりの作業基盤になっていく、という見方で、`harness-engineering` と `agent-recognizable-repository` の文脈をかなり補強している。

3本目は Devin の Windows VM 対応。Devin が Windows ネイティブアプリをビルド、実行、テストできる managed runtime を持つという話で、これは「コードを書くエージェント」から「対象プラットフォームを実際に動かして検証できるエージェント」への拡張として読める。KBでは `managed-agents` と `long-running-agents` に関わる材料で、実務上の差分はモデルの返答品質だけでなく、実行環境をどこまでエージェント側に持たせるかにも出る。

Goodpatch のデザイナーAIプロトタイプ活用記事は、AIをデザイン作業へどう入れるかを、抽象論ではなくプロトタイプ生成のワークフローとして扱っている。ここで面白いのは、成果物そのものがデザインの会話や検証を進める「rich artifact」になっている点。KBでは `rich-agent-output-artifact` と `tool-accessibility` に接続され、エージェントの価値がテキスト回答ではなく、作業の次の一手を早める成果物に宿る、という見方を補強した。

Figma Make の custom skills は、反復ワークフローをユーザーが作成・呼び出しできる単位として扱う更新だった。これは `navigable-agent-skills` と `memory-skill-harness` にとってかなり直球のソースで、スキルが単なる内部実装ではなく、チームや組織で共有・レビューされる可能性のある操作単位になっていく流れを示している。今後は、スキルのバージョン管理、レビュー、共有範囲が実務上の論点になりそう。

概念更新としては、`harness-engineering`、`managed-agents`、`memory-skill-harness`、`multi-agent-orchestration`、`navigable-agent-skills`、`rich-agent-output-artifact`、`tool-accessibility` が更新された。新しい地図ノートは増えていないが、既存概念への支持ソースが増えたことで、KB全体では「エージェント実務は、作業面・実行環境・スキル化・レビューの組み合わせで成熟する」という軸がかなり濃くなった。

全体トレンドを一言で言うと、2026-05-22 の更新は「agent harness の部品が、実務者に触れる形で外へ出てきた」日だった。Claude Code は workflow と code review、Codex-maxxing は長時間作業の運用プリミティブ、Devin はWindows VM、Goodpatch はデザインプロトタイプ、Figma はcustom skills。領域は違うが、どれもエージェントに任せるための準備、境界、検証、再利用を具体的な操作面に落としている。

NotebookLM Podcast では、まず「今日の話はモデル性能ではなく、エージェントの仕事場がどう変わっているか」という導入にするとよさそう。中心に置く3本は Claude Code 2.1.147、Codex-maxxing、Devin Windows VM。そこに Goodpatch と Figma を加えると、開発者向け harness だけでなく、デザインやプロダクト作業にも同じ構造が広がっていることを話せる。掘るべき問いは、どのワークフローをスキル化すべきか、どの実行環境をエージェントに渡すべきか、レビュー effort をどう設計すると人間の負担が減るのか、の3つ。


## 重要ソース

### Claude Code Changelog - Claude Code 2.1.147 release cluster

Source note: `wiki/sources/claude-code-log-2-1-147-workflow-tool-code-review-rename-cluster-x-2026-05-21.md`

# Claude Code Changelog - Claude Code 2.1.147 release cluster

## Source Metadata
- Source type: X bookmark snapshot
- X posts:
  - https://x.com/ClaudeCodeLog/status/2057564555174113732
  - https://x.com/dani_avila7/status/2057285380186222745
- Authors:
  - Claude Code Changelog (@ClaudeCodeLog)
  - Daniel San (@dani_avila7)
- Tweet created: 2026-05-21T20:49:52.000Z / 2026-05-21T02:20:31.000Z
- Captured: 2026-05-22 via xurl bookmarks capture
- Evidence strength: bookmark snapshot metadata plus release-card/video-card previews
- Public metrics at capture:
  - Claude Code Changelog post: 193 likes, 74 bookmarks, 11 reposts, 13 replies, 17987 impressions
  - Daniel San post: 659 likes, 525 bookmarks, 48 reposts, 37 replies, 77797 impressions
- Raw path: [[../../raw/articles/claude-code-log-2-1-147-workflow-tool-code-review-rename-cluster-x-2026-05-21.md]]

## Linked URLs
- https://x.com/ClaudeCodeLog/status/2057564555174113732/video/1
- https://x.com/dani_avila7/status/2057285380186222745/video/1

## Bookmark text
> Claude Code 2.1.147 has been released.
>
> 35 CLI changes
>
> Highlights:
> - Workflow tool added for deterministic multi-agent orchestration; off by default, set CLAUDE_CODE_WORKFLOWS=1
> - /simplify→/code-review renamed; flags correctness bugs at effort level, can post inline GitHub

> Claude Code /simplify is now /code-review
>
> Now accepts an effort parameter:
>
> - low: short, scoped, latency-sensitive tasks that aren't intelligence-sensitive
> - medium: cost-sensitive work that can trade off some intelligence for fewer tokens
> - high: balances tokens and quality

## What it says
Claude Code is pushing review and orchestration into named product surfaces. The release story is not just more capability; it is more explicit control over how agent work is d

### Cognition - Devin Windows VM

Source note: `wiki/sources/cognition-devin-windows-vm-x-2026-05-21.md`

# Cognition - Devin Windows VM

## Source Metadata
- Source type: X bookmark snapshot
- X post: https://x.com/cognition/status/2057496130225668360
- Author: Cognition (@cognition)
- Tweet created: 2026-05-21T16:17:58.000Z
- Captured: 2026-05-22 via xurl bookmarks capture
- Evidence strength: bookmark snapshot metadata plus video-card preview
- Public metrics at capture: 260 likes, 54 bookmarks, 32 reposts, 14 replies, 67713 impressions
- Raw path: [[../../raw/articles/cognition-devin-windows-vm-x-2026-05-21.md]]

## Linked URLs
- https://x.com/cognition/status/2057496130225668360/video/1

## Bookmark text
> Devin is getting a Windows PC.
>
> Devin can now natively run in a Windows VM, so it can build, run, and test native Windows applications.

## What it says
Devin is expanding from a general coding agent into a platform-aware agent runtime that can exercise Windows-native applications inside a managed VM.

## Why it matters
This is a concrete managed-agent capability jump: the runtime now owns not just code execution but OS-specific app execution and verification.

## Related concepts
- [[../concepts/managed-agents.md]]
- [[../concepts/multi-agent-orchestration.md]]
- [[../concepts/long-running-agents.md]]
- [[../concepts/harness-engineering.md]]

## Open questions
- Which classes of Windows tasks become newly practical when the agent can run inside a Windows VM?
- How much extra verification does a platform-specific VM reduce versus add?

### Figma - custom skills in Make

Source note: `wiki/sources/figma-custom-skills-in-make-x-2026-05-11.md`

# Figma - custom skills in Make

## Source Metadata
- Source type: X bookmark snapshot
- X post: https://x.com/figma/status/2053867832761553052
- Author: Figma (@figma)
- Tweet created: 2026-05-11T16:00:25.000Z
- Captured: 2026-05-22 via xurl bookmarks capture
- Evidence strength: bookmark snapshot metadata plus video-card preview
- Public metrics at capture: 625 likes, 404 bookmarks, 71 reposts, 16 replies, 64479 impressions
- Raw path: [[../../raw/articles/figma-custom-skills-in-make-x-2026-05-11.md]]

## Linked URLs
- https://x.com/figma/status/2053867832761553052/video/1

## Bookmark text
> /custom-skills-are-now-in-make-so-you-can-create-and-call-repeated-workflows
>
> Note: you can create and manage your own skills now. Sharing skills with your team and org is coming soon.

## What it says
Figma is turning repeated workflows into named skills inside Make. That makes procedures more shareable and more inspectable.

## Why it matters
This is a concrete example of skills as reusable operational units, which is close to how agent systems will need to package repeatable work.

## Related concepts
- [[../concepts/navigable-agent-skills.md]]
- [[../concepts/memory-skill-harness.md]]
- [[../concepts/tool-accessibility.md]]
- [[../concepts/managed-agents.md]]

## Open questions
- How should custom skills be versioned and reviewed across a team?
- Which skills should stay local to a user versus shared at org scope?

### Goodpatch - designer AI prototype workflow

Source note: `wiki/sources/goodpatch-designer-ai-prototype-workflow-x-2026-05-21.md`

# Goodpatch - designer AI prototype workflow

## Source Metadata
- Source type: X bookmark snapshot
- X post: https://x.com/kc_at_/status/2057302285097869401
- Primary source: https://goodpatch.com/blog/2026-05-prototype
- Secondary X source: https://twitter.com/GoodpatchTokyo/status/2057270807920054456
- Author: けいし/ Goodpatch (@kc_at_)
- Tweet created: 2026-05-21T03:27:42.000Z
- Captured: 2026-05-22 via xurl bookmarks capture
- Evidence strength: bookmark snapshot metadata plus primary blog card
- Public metrics at capture: 159 likes, 158 bookmarks, 12 reposts, 0 replies, 17322 impressions
- Raw path: [[../../raw/articles/goodpatch-designer-ai-prototype-workflow-x-2026-05-21.md]]

## Linked URLs
- https://goodpatch.com/blog/2026-05-prototype
- https://x.com/kc_at_/status/2057302285097869401/photo/1

## Bookmark text
> Goodpatch Blog書きました！
>
> Goodpatchのデザイナーが現場で具体的にどうAIを活用しているのか、その1つの例としてのリアルを書きました。
>
> 「AIをデザインの仕事にどう活かせばいいんだろう」と模索しているデザイナーの方の参考になれば嬉しいです

## What it says
This is a practitioner note about using AI inside design work, with the blog card pointing to a prototype workflow story rather than a speculative design vision.

## Why it matters
Prototype generation is moving closer to the actual work surface. That makes the output artifact itself part of the design harness.

## Related concepts
- [[../concepts/field-deployed-engineer.md]]
- [[../concepts/rich-agent-output-artifact.md]]
- [[../concepts/tool-accessibility.md]]
- [[../concepts/product-responsibility-distribution.md]]

## Open questions
- Which parts of the prototype workflow should remain human-directed?
- When does a fast prototype become a product commitment?

### Jason Liu - Codex-maxxing

Source note: `wiki/sources/jxnlco-codex-maxxing-x-2026-05-17.md`

# Jason Liu - Codex-maxxing

## Source Metadata
- Source type: X bookmark snapshot
- X post: https://x.com/jxnlco/status/2056139571641872765
- Primary source: https://jxnl.github.io/blog/writing/2026/05/10/codex-maxxing/
- Author: jason (@jxnlco)
- Tweet created: 2026-05-17T22:27:29.000Z
- Captured: 2026-05-22 via xurl bookmarks capture
- Evidence strength: bookmark snapshot metadata plus primary blog card
- Public metrics at capture: 3504 likes, 6076 bookmarks, 220 reposts, 151 replies, 371688 impressions
- Raw path: [[../../raw/articles/jxnlco-codex-maxxing-x-2026-05-17.md]]

## Linked URLs
- https://jxnl.github.io/blog/writing/2026/05/10/codex-maxxing/

## Bookmark text
> jason from the codex team here,
> heres a draft on codex maxxing and the primatives i use on a daily basis

## What it says
Codex is framed as an operating substrate for long-running work. The value proposition is a stack of reusable primitives rather than one-off chat completions.

## Why it matters
This is a strong harness-engineering example because it emphasizes compounding work surfaces: persistent threads, memory, steering, connectors, and reviewable artifacts.

## Related concepts
- [[../concepts/harness-engineering.md]]
- [[../concepts/agent-recognizable-repository.md]]
- [[../concepts/structured-handoff-artifacts.md]]
- [[../concepts/long-running-agents.md]]
- [[../concepts/context-file-system.md]]

## Open questions
- Which primitives should become default infrastructure versus optional power-user workflows?
- What is the minimum persistent state that makes long-running work tractable without becoming brittle?

## 更新された概念・地図

### Harness Engineering

KB note: `wiki/concepts/harness-engineering.md`

---
aliases:
  - Harness Engineering
---

# Harness Engineering

## Definition
The design of the environment, artifacts, controls, tooling, and feedback loops around an agent so that it can produce more reliable results over time.

## Why It Matters
As agents become more capable, performance depends less on the model alone and more on the structure that surrounds it.

## Related Concepts
- [[guides and sensors]]
- [[agent recognizable repository]]
- [[structured handoff artifacts]]
- [[machine-checkable invariants]]
- [[heavy-thinking.md]]

## Supporting Sources
- [[../sources/openai-harness-engineering.md]]
- [[../sources/martin-fowler-harness-engineering.md]]
- [[../sources/gota-purpose-first-harness-design-speakerdeck.md]]
- [[../sources/rkaga-how-to-approach-harness-engineering-speakerdeck.md]]
- [[../sources/rkaga-what-harness-engineering-is-and-is-not-zenn.md]]
- [[../sources/sergicalsix-harness-engineering-overview-design-philosophy-speakerdeck.md]]
- [[../sources/yuukiyo-ai-dlc

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

### Memory-Skill Harness

KB note: `wiki/concepts/memory-skill-harness.md`

---
aliases:
  - Unified Memory-Skill Harness
  - Memory-Skill Harness
---

# Memory-Skill Harness

## Definition
A harness pattern where memory and skills are treated as one evolving world model: memory stores the state and evidence an agent acts from, while skills store reusable procedures derived from successful or corrected traces.

## Why It Matters
Separating memory from skills can make both brittle. Memory becomes passive storage if it cannot route the right procedure, and skills become stale prompt snippets if they cannot observe environmental change, attach evidence, and update themselves. A unified memory-skill harness makes repeated work inspectable, revisable, and queryable.

## Related Concepts
- [[agent-knowledge-loop.md]]
- [[navigable-agent-skills.md]]
- [[context-file-system.md]]
- [[context-graph.md]]
- [[rule-update-loop.md]]
- [[harness-engineering.md]]

## Supporting Sources
- [[../sources/tricalt-memory-skills-same-harness-x.md]]
- [[../sources/knowledgesense-corp

### Multi-Agent Orchestration

KB note: `wiki/concepts/multi-agent-orchestration.md`

---
aliases:
  - Multi-Agent Orchestration
---

# Multi-Agent Orchestration

## Definition
The deliberate assignment of different roles or subtasks to multiple cooperating agents within a larger workflow.

## Why It Matters
Some tasks benefit from separating planning, generation, evaluation, and execution rather than asking one agent to do everything.

## Related Concepts
- [[generator-evaluator-loop]]
- [[context-resets]]
- [[long-running-agents]]
- [[intelligent-delegation.md]]
- [[heavy-thinking.md]]
- [[managed-agents.md]]

## Supporting Sources
- [[../sources/anthropic-harness-design-long-running-apps.md]]
- [[../sources/claude-new-in-managed-agents-dreaming-outcomes-orchestration.md]]
- [[../sources/kevin-gu-autoagent-x-thread.md]]
- [[../sources/openai-codex-plugin-cc-github.md]]
- [[../sources/anthropic-claude-code-skills-docs.md]]
- [[../sources/cursor-3-x.md]]
- [[../sources/openai-gpt-5-4-mini-nano-blog.md]]
- [[../sources/codex-subagents-docs.md]]
- [[../sources/anthropic-m

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

### Rich Agent Output Artifact

KB note: `wiki/concepts/rich-agent-output-artifact.md`

---
aliases:
  - Rich agent output artifact
  - HTML artifact
  - Agent-generated interface
---

# Rich Agent Output Artifact

## Definition
An agent-produced deliverable that uses a richer medium than linear prose, such as HTML, SVG, charts, interactive controls, dashboards, slide decks, or custom editors, to help humans understand, review, steer, or reuse complex work.

## Why It Matters
Human-in-the-loop workflows often fail not because the agent lacks information, but because the output is too dense, flat, or hard to inspect. Rich artifacts can reduce review friction by making structure visible: diffs can become annotated layouts, plans can become option grids, reports can become timelines, and exploratory work can become a small browser-native tool.

## Relation to Harness Engineering
The output format is part of the harness. It determines how easily a human can:
- understand the agent's reasoning and evidence
- notice errors or missing cases
- compare alternatives
- manipulate pa

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

## NotebookLM Podcast用メモ

- まず今日の全体トレンドを話してから、重要ソースを3本に絞って深掘りする。
- ソース単体の紹介で終わらせず、既存KBの概念や地図がどう更新されたかを会話に含める。
- 最後に、明日以降の調査問いを2〜3個提示する。
