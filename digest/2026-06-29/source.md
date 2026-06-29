<!-- generated: 2026-06-29T13:01:36.129445+00:00 -->
<!-- kb_daily_digest_date: 2026-06-29 -->
# KB Daily Digest Source — 2026-06-29

このページは、knowledge-base-llm の日次更新を NotebookLM に読み込ませるための公開向けソースページです。
Discord通知よりも文脈を厚めに残し、Podcast化しやすいように、今日追加・更新されたソース、概念、地図を文章中心で整理します。

## 今日の全体像

# KB Daily Digest 2026-06-29

2026-06-29 UTC の knowledge-base-llm は、X bookmarks の日次取り込みを起点に、3本の raw article と3本の wiki source note を追加した。新規 raw は `raw/x/bookmarks/bookmarks-20260629T0000Z.json`、まかねこ氏の Codex + GPT-5.5 Pro advisor skill 記事共有、Yusuke Wada 氏の AI agent framework Flue 記事共有、Google Sheets の canvas 作成機能共有の3本。wiki 側では、それぞれ `makaneko-codex-gpt-55-pro-advisor-skill-x-2026-06-28.md`、`yusuke-wada-ai-agent-framework-flue-x-2026-06-28.md`、`lin-create-a-sheets-canvas-x-2026-06-26.md` が追加され、`wiki/INDEX.md` と4つの概念ノートも更新された。

全体トレンドは、AI agent の価値が「モデル単体の能力」から、「外側の harness、skill、artifact surface をどう組み合わせるか」へさらに寄っていること。Flue は agent を tools / skills / subagents / workflows / chat integration まで含む harness として扱い、まかねこ氏の記事は Codex の実装・検証ループにブラウザ側の上位 advisor model を差し込む運用パターンを示す。Google Sheets canvas は、AI生成結果をただのテキスト回答ではなく、チームで扱える構造化された可視 artifact に落とす方向を補強している。

重要ソースの1本目は、Yusuke Wada 氏による Flue の記事共有。source note では、Flue を TypeScript の AI agent framework としてだけでなく、prompt wrapper ではない harness-driven architecture として位置付けている。具体的には、runbook を skills として扱うこと、subagent delegation、structured workflows、Slack などの chat integration、SRE agent の例が取り上げられている。KB では `harness-engineering`、`coding-agents`、`workflow-compilation`、`multi-agent-orchestration` に接続され、agent framework を「モデルを呼ぶ薄い層」ではなく、実務に耐える運用外骨格として比較する材料になった。

重要ソースの2本目は、まかねこ氏の Codex GPT-5.5 Pro advisor skill。これは Codex がローカルで実装や検証を担い、重要な計画、設計、アーキテクチャ比較、調査の局面ではブラウザ上の ChatGPT Pro / GPT-5.5 Pro を外部 advisor として使い、その結果を Codex に戻すという loop を扱っている。source note の evidence quality は practitioner recipe として medium-high だが、実務上の問いははっきりしている。つまり、どの判断だけを高コストな advisor pass に回すべきか、advisor と implementer の分業をどう監査するか、これを一時的な workaround ではなく reusable skill や policy rule にすべきか、という問いである。

重要ソースの3本目は、Google Sheets の Create a canvas 機能共有。Google Docs help page を一次的な裏付けとして、Sheets から canvas を作り、Gemini によって Kanban board や gallery view のような interactive visualization を生成できる点が取り込まれた。KB 上では `rich-agent-output-artifact`、`structured-handoff-artifacts`、`tool-accessibility` に接続されている。これは agent UI の話であると同時に、日常的な productivity surface の中に AI-generated structured artifact が入ってくる話でもある。

今回の概念更新は小さいが、方向性は明確だった。`harness-engineering` には Flue が追加され、agent harness を構成する tools、skills、delegation、workflow、chat surface を比較する足場が増えた。`navigable-agent-skills` と `skill-optimization` には advisor skill が追加され、skill が単なる手順書ではなく、必要に応じて外部 reasoning resource に移動する navigation layer にもなり得ることが示された。`structured-handoff-artifacts` には Sheets canvas が入り、handoff artifact が Markdown や issue だけでなく、スプレッドシート内の interactive visualization に広がる可能性が補強された。

同時に、`outputs/audit/kb-static-audit-seed-2026-06-29.md` も生成されている。現時点の wiki markdown は620件、source note は505件、concept note は86件、map note は18件。broken wiki/markdown links は3件で、いずれも `openclaw-gogcli-release-v0.16` に関するリンクの表記揺れらしい。source note without concept links は0件なので、新規 source note の接続漏れは起きていない。一方で `infrastructure-from-code`、`intention-debt`、`kv-cache` は source backlink が1件の弱い概念として残っており、月次 audit ではこのあたりの補強や整理が候補になる。

実務上の示唆は、agent 導入を「どのモデルを使うか」だけで見ないこと。Flue のような framework は、runbook、tool schema、subagent、workflow、chat invocation をどう束ねるかを問う。advisor skill は、全てを同じ agent に任せるのではなく、判断の重い局面だけを別の reasoning surface に渡す設計を示す。Sheets canvas は、agent の出力が次の人間やチームに渡るとき、どの artifact ならそのまま作業面になるかを問う。3本を合わせると、今日のKBは「agent の能力」よりも「agent が働く面、移動する面、成果を残す面」を厚くした更新だった。

Podcast では、「Flue の harness-driven な見方は既存の coding agent harness pattern と何が違うのか」「advisor model を挟む skill は、品質改善なのか、責任分界の明確化なのか」「Sheets canvas のような structured artifact は、agent output の終点なのか、それとも次の workflow の入口なのか」を掘るとよい。次に追う問いは、1) Flue の実装と Pi foundation の境界、2) advisor skill をどの判断にだけ適用すると費用対効果が出るか、3) AI-generated canvas がチームの handoff artifact として再利用できる条件、4) static audit で出た broken links と weak concepts の整理、の4つ。


## 重要ソース

### LIN - Create a Sheets canvas

Source note: `wiki/sources/lin-create-a-sheets-canvas-x-2026-06-26.md`

# LIN - Create a Sheets canvas

## Source Metadata
- Raw path: [[../../raw/articles/lin-create-a-sheets-canvas-x-2026-06-26.md]]
- Raw bookmark capture: [[../../raw/x/bookmarks/bookmarks-20260629T0000Z.json]]
- Original URL: https://x.com/i/status/2070430015439974597
- Primary URL: https://support.google.com/docs/answer/17035851?hl=en
- Author: LIN / @ai_lin_creation
- Posted: 2026-06-26T08:52:37.000Z
- Captured: 2026-06-29 via xurl bookmarks capture
- Type: X post / feature screenshot share

## Summary
This bookmark highlights Google Sheets' new canvas workflow. The feature matters because it turns a spreadsheet into a lightweight AI-assisted workspace where Gemini can generate interactive task boards and other structured visualizations.

## Key Claims
- Google Sheets now has a canvas creation flow accessible from the UI.
- Gemini can be prompted to generate interactive visualizations inside the canvas.
- Kanban boards and gallery views are explicitly listed as supported examples.

## Evidence / Examples
- The bookmark text explicitly calls out "Create a Canvas".
- The Google Docs help page describes the UI entry points and example canvas types.
- The screenshot share makes the feature feel like a practical product capability rather than a conceptual roadmap item.

## Evidence Quality
- Source type: X post backed by an official Google Docs help page
- Confidence: high for the documented UI behavior
- Supports: rich agent output artifact, structured handoff artifacts, tool accessibility
- Main limitations: this is a product feature note, not an agent framework or eval result
- Best use: connect everyday productivity surfaces to AI-assisted artifact generation

## Related Concepts
- [[../concepts/rich-agent-output-artifact.md]]
- [[../concepts/structured-handoff-artifact

### makaneko - Codex GPT-5.5 Pro advisor skill

Source note: `wiki/sources/makaneko-codex-gpt-55-pro-advisor-skill-x-2026-06-28.md`

# makaneko - Codex GPT-5.5 Pro advisor skill

## Source Metadata
- Raw path: [[../../raw/articles/makaneko-codex-gpt-55-pro-advisor-skill-x-2026-06-28.md]]
- Raw bookmark capture: [[../../raw/x/bookmarks/bookmarks-20260629T0000Z.json]]
- Original URL: https://x.com/i/status/2071136501937872956
- Primary URL: https://note.com/makaneko_ai/n/n179a9876911b
- Author: まかねこ / @makaneko_AI
- Posted: 2026-06-28T07:39:56.000Z
- Captured: 2026-06-29 via xurl bookmarks capture
- Type: X bookmark share of note.com article

## Summary
This bookmark points to a note article describing a Codex skill that uses GPT-5.5 Pro as an external advisor. The pattern is interesting because it combines coding-agent execution with a higher-end reasoning pass in the browser, then feeds the result back into Codex for verification.

## Key Claims
- Codex can be paired with GPT-5.5 Pro as a consultation step.
- The skill is intended for important planning, design, architecture, comparisons, and research.
- The Pro model is used as an advisor because it can spend more effort on ambiguous decisions.
- Codex still performs the local verification and implementation step.

## Evidence / Examples
- The article description explicitly lays out the Codex -> browser ChatGPT Pro -> Codex loop.
- The writeup says Pro is being used for advisory work because Codex cannot directly use the Pro model in the same way.
- The suggested use cases are planning-heavy, which makes the source relevant to decision-support workflows rather than ordinary code generation.

## Evidence Quality
- Source type: X bookmark share of a note.com article
- Confidence: medium-high for the workflow pattern
- Supports: navigable agent skills, coding agents, skill optimization, human-in-the-loop
- Main limitations: this is a practitioner recip

### Yusuke Wada - AI Agent Framework Flue

Source note: `wiki/sources/yusuke-wada-ai-agent-framework-flue-x-2026-06-28.md`

# Yusuke Wada - AI Agent Framework Flue

## Source Metadata
- Raw path: [[../../raw/articles/yusuke-wada-ai-agent-framework-flue-x-2026-06-28.md]]
- Raw bookmark capture: [[../../raw/x/bookmarks/bookmarks-20260629T0000Z.json]]
- Original URL: https://x.com/i/status/2071254229633946041
- Primary URL: https://azukiazusa.dev/blog/ai-agent-framework-flue/
- Author: Yusuke Wada / @yusukebe
- Posted: 2026-06-28T15:27:45.000Z
- Captured: 2026-06-29 via xurl bookmarks capture
- Type: X bookmark share of technical blog post

## Summary
This bookmark points to a detailed blog post about Flue, a TypeScript framework for building AI agents. The article is useful because it treats agent construction as a harness problem: the framework provides the surrounding pieces for tools, skills, subagents, workflows, and chat integration, not just a prompt wrapper.

## Key Claims
- Flue is a TypeScript framework for building AI agents.
- The article frames Flue as harness-driven rather than prompt-driven.
- The framework covers practical building blocks such as runbooks as skills, subagent delegation, workflows, and chat integration.
- The post uses an SRE agent example, which grounds the framework in operational work.

## Evidence / Examples
- The bookmark description explicitly says Flue is a TypeScript framework for AI agents.
- The linked article describes harness-driven architecture and points to Pi as a minimal terminal coding harness foundation.
- The article outline includes SRE agent setup, runbooks as skills, subagent delegation, structured workflows, and Slack invocation.

## Evidence Quality
- Source type: X bookmark share of a technical blog post
- Confidence: high for the framework and architecture framing
- Supports: harness engineering, coding agents, workflow compilation, mult

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

## NotebookLM Podcast用メモ

- まず今日の全体トレンドを話してから、重要ソースを3本に絞って深掘りする。
- ソース単体の紹介で終わらせず、既存KBの概念や地図がどう更新されたかを会話に含める。
- 最後に、明日以降の調査問いを2〜3個提示する。
