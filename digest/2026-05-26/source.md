<!-- generated: 2026-05-26T13:02:18.680899+00:00 -->
<!-- kb_daily_digest_date: 2026-05-26 -->
# KB Daily Digest Source — 2026-05-26

このページは、knowledge-base-llm の日次更新を NotebookLM に読み込ませるための公開向けソースページです。
Discord通知よりも文脈を厚めに残し、Podcast化しやすいように、今日追加・更新されたソース、概念、地図を文章中心で整理します。

## 今日の全体像

# KB Daily Digest 2026-05-26

今日の knowledge-base-llm は、X ブックマーク由来の4本と、arXiv 論文 SkillOpt の1本を新規 ingest / compile した。全体としては、エージェント活用の焦点が「単発プロンプト」から「再利用可能なワークフロー」「並列探索」「知識グラフによる継続運用」、さらに「スキル文書そのものを検証付きで最適化する」方向へ進んでいる。

重要ソースの1本目は arXiv の **SkillOpt: Executive Strategy for Self-Evolving Agent Skills**。これは、エージェントのスキル文書を、固定されたモデルとハーネスの外側にある「訓練可能な自然言語状態」として扱う研究だ。実行トレースを集め、成功・失敗パターンから optimizer model が add/delete/replace の小さな編集案を出し、held-out validation で改善した場合だけ採用する。KBでは新規概念 [[../../wiki/concepts/skill-optimization.md]] を作り、[[../../wiki/concepts/memory-skill-harness.md]]、[[../../wiki/concepts/rule-update-loop.md]]、[[../../wiki/concepts/trace-driven-improvement.md]]、[[../../wiki/maps/agent-harness-control-taxonomy.md]] に接続した。

SkillOpt が特に重要なのは、これまで KB で扱ってきた「スキルは手続き記憶」「メモリとスキルはエージェントハーネスの2つの見方」という議論に、かなり具体的な最適化ループを与える点だ。人間が気づいた改善を手で SKILL.md に書く段階から、実行ログ、スコア、失敗パターン、検証ゲートを通してスキルを更新する段階に進める。ただし、スコアが明確なベンチマークでは強い一方、文章作成・設計・リサーチのような開いた仕事では、どの検証ゲートを信頼するかがまだ大きな未解決問題として残る。

2本目は Daniel Miessler の Claude Code /workflows に関する投稿。ここでは、企業向けAIの重要単位が「プロンプト」ではなく「再利用可能な業務ワークフロー」になっていく、という見方が入った。KB上では [[../../wiki/concepts/harness-engineering.md]]、[[../../wiki/concepts/multi-agent-orchestration.md]]、[[../../wiki/concepts/managed-agents.md]] に接続され、Claude Code や類似ツールの価値が、単に賢いチャットではなく、組織内の反復作業を明示的な実行面に落とすところへ広がっていることを補強している。

3本目は Figma の design agent automation and parallel exploration。公式デモとして、反復的なデザイン作業の自動化と、複数案の並列探索が示されている。これは [[../../wiki/concepts/multi-agent-orchestration.md]] と [[../../wiki/concepts/rich-agent-output-artifact.md]] に効いていて、並列化の対象がコード実装だけでなく、デザイン案・視覚成果物・レビュー可能なブランチにも広がっていることを示す材料になった。

残る2本も同じトレンドを別角度から支えている。leopardracer の knowledge graph / Claude workflow は、モデル利用上限に達したあとも、周辺のノートやグラフが読み込み・接続・ブリーフ生成・次の問い出しを続けるという知識ループの例として入った。スナガクの Claude Design / Remotion 事例は、スタイル探索、選択、実装、動画生成までを一連の創作ワークフローとして扱っており、リッチな出力成果物をエージェントがどう作り、どのレビュー面で人間が選ぶかという論点を強めた。

全体トレンドはかなり明確で、今日の更新は「AIが何かを生成する」よりも、「生成を支える作業面をどう設計し、継続運用し、改善するか」に寄っている。/workflows は手順を製品面に固定し、Figma は探索を並列ブランチ化し、knowledge graph 事例は継続的な知識更新をハーネスに任せ、SkillOpt はスキル文書自体を検証付きの更新対象にする。つまり、エージェント活用はモデル呼び出しの工夫から、周辺のハーネス、メモリ、ワークフロー、検証ゲートの設計へ重心を移している。

KB内の更新としては、新規 raw 8件相当、wiki/sources 5件、wiki/concepts 1件が追加され、既存の harness-engineering、multi-agent-orchestration、agent-knowledge-loop、rich-agent-output-artifact、memory-skill-harness、rule-update-loop、trace-driven-improvement、agent-harness-landscape、agent-harness-control-taxonomy などが更新された。特に agent-harness-control-taxonomy には、自己更新するスキルを trusted context に入れる前にどう評価するか、という追跡課題が追加されている。

次に掘るなら、(1) SkillOpt 型の validation-gated skill update を、実務の Clawd / Codex / Claude Code スキル更新にどう安全に適用するか、(2) /workflows や Figma design agent のような製品面ワークフローを KB の harness taxonomy にどう分類するか、(3) knowledge graph / Obsidian / compiled wiki の継続ループで、何をモデルに任せ、何を構造化ファイル側に残すべきか、がよさそう。

## Important sources

- SkillOpt: Executive Strategy for Self-Evolving Agent Skills: https://arxiv.org/abs/2605.23904
- Daniel Miessler — Claude Code /workflows for Enterprise AI: https://x.com/DanielMiessler/status/2058699741140222055
- Figma — design agent automation and parallel exploration: https://x.com/figma/status/2057164914331128060
- leopardracer — Claude keeps running on a knowledge graph: https://x.com/leopardracer/status/2054178069653418477
- スナガク — Claude Design helps generate a video workflow end to end: https://x.com/suna_gaku/status/2058518930503930144

## Changed KB files

- raw/articles/arxiv-skillopt-executive-strategy-self-evolving-agent-skills-2605-23904.md
- raw/pdfs/arxiv-2605.23904-skillopt.pdf
- raw/arxiv-source/arxiv-2605.23904-skillopt-source.tar.gz
- raw/articles/danielmiessler-claude-code-workflows-enterprise-ai-x-2026-05-25.md
- raw/articles/figma-design-agent-parallel-exploration-automation-x-2026-05-20.md
- raw/articles/leopardracer-knowledge-graph-claude-limit-x-2026-05-12.md
- raw/articles/suna-gaku-claude-design-remotion-video-generation-x-2026-05-24.md
- raw/x/bookmarks/bookmarks-20260526T0005Z.json
- wiki/sources/arxiv-skillopt-executive-strategy-self-evolving-agent-skills.md
- wiki/sources/danielmiessler-claude-code-workflows-enterprise-ai-x-2026-05-25.md
- wiki/sources/figma-design-agent-parallel-exploration-automation-x-2026-05-20.md
- wiki/sources/leopardracer-knowledge-graph-claude-limit-x-2026-05-12.md
- wiki/sources/suna-gaku-claude-design-remotion-video-generation-x-2026-05-24.md
- wiki/concepts/skill-optimization.md
- wiki/concepts/memory-skill-harness.md
- wiki/concepts/rule-update-loop.md
- wiki/concepts/trace-driven-improvement.md
- wiki/concepts/harness-engineering.md
- wiki/concepts/multi-agent-orchestration.md
- wiki/concepts/agent-knowledge-loop.md
- wiki/concepts/rich-agent-output-artifact.md
- wiki/maps/agent-harness-control-taxonomy.md
- wiki/maps/agent-harness-landscape.md
- wiki/navigation/harness.md
- wiki/navigation/memory.md
- wiki/glossary.md
- wiki/INDEX.md



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

### arXiv — SkillOpt: Executive Strategy for Self-Evolving Agent Skills

Source note: `wiki/sources/arxiv-skillopt-executive-strategy-self-evolving-agent-skills.md`

# arXiv — SkillOpt: Executive Strategy for Self-Evolving Agent Skills

## Source Metadata
- Raw path: `raw/articles/arxiv-skillopt-executive-strategy-self-evolving-agent-skills-2605-23904.md`
- Local PDF: `raw/pdfs/arxiv-2605.23904-skillopt.pdf`
- Local source tarball: `raw/arxiv-source/arxiv-2605.23904-skillopt-source.tar.gz`
- Original URL: https://arxiv.org/abs/2605.23904
- PDF URL: https://arxiv.org/pdf/2605.23904
- Project page: https://microsoft.github.io/SkillOpt/
- Code link: https://github.com/microsoft/SkillOpt
- arXiv ID: 2605.23904v2
- Authors: Yifan Yang, Ziyang Gong, Weiquan Huang, Qihao Yang, Ziwei Zhou, Zisu Huang, Yan Li, Xuemei Gao, Qi Dai, Bei Liu, Kai Qiu, Yuqing Yang, Dongdong Chen, Xue Yang, Chong Luo
- Date: 2026-05-22; updated 2026-05-25
- Type: arXiv paper / agent-skill optimization method

## Summary
SkillOpt proposes treating an agent skill document as the external trainable state of a frozen agent. Instead of relying on human-written skills, one-shot LLM-generated skills, or loosely controlled self-revision, the method uses a separate optimizer model to convert scored execution rollouts into bounded add/delete/replace edits. Each candidate skill is accepted only if it improves a held-out validation score, and the deployed output is a compact `best_skill.md` artifact that adds no extra inference-time model calls.

The paper is especially relevant to the KB because it turns the memory/skill harness idea into an optimizer design. Traces are not just reviewed by humans; they become structured evidence for modifying procedural memory under a validation gate.

## Key Claims
- Agent skills can be treated as trainable natural-language state for adapting frozen models and fixed execution harnesses.
- Bounded text updates are a practical analogue of le

### mizchi — Empirical prompt tuning with SKILL.md

Source note: `wiki/sources/mizchi-skill-md-empirical-prompt-tuning-x.md`

# mizchi — Empirical prompt tuning with SKILL.md

## Source Metadata
- Raw path: `raw/articles/mizchi-skill-md-empirical-prompt-tuning-x-2026-04-18.md`
- Original URL: https://x.com/mizchi/status/2045501078574350450
- Author: mizchi
- Date: 2026-04-18
- Type: X post
- Evidence strength: xAI-extracted post summary

## Summary
mizchi shares a SKILL.md that auto-optimizes skills by reflecting on task outcomes and rewriting instructions when the skill seems weak.

## Key Claims
- The workflow turns prompt tuning into an empirical loop
- the system self-evaluates after tasks
- reproducibility improves when tacit instructions are externalized.

## Evidence / Examples
- xAI summary of the post and any cited primary link.
- Engagement and thread context were used only as supporting signals.

## Evidence Quality
- Source type: X post
- Confidence: moderate to high for the post’s main framing; lower for any implied follow-up context.
- Supports: localized source note and concept connections.
- Main limitations: xAI summaries can compress or paraphrase the original post.
- Best use: a durable pointer into the related harness / agent / research cluster.

## Related Concepts
- [[agent-knowledge-loop]]
- [[trace-driven-improvement]]
- [[skill-optimization]]
- [[harness-engineering]]
- [[self-evaluation-bias]]

## Open Questions
- Which part of this pattern seems durable versus just a current product rollout?
- What stronger primary source should be attached next if this note proves important?

## Backlinks
- [[../concepts/agent-knowledge-loop.md]]
- [[../concepts/trace-driven-improvement.md]]
- [[../concepts/skill-optimization.md]]
- [[../concepts/harness-engineering.md]]
- [[../concepts/self-evaluation-bias.md]]

### Vasilije / tricalt — Memory and skills as the same harness

Source note: `wiki/sources/tricalt-memory-skills-same-harness-x.md`

# Vasilije / tricalt — Memory and skills as the same harness

## Source Metadata
- Raw path: raw/articles/tricalt-memory-skills-same-harness-x-2026-05-17.md
- Original URL: https://x.com/tricalt/status/2055876832797581406
- Article URL: https://x.com/i/article/2053986800050524160
- Author: Vasilije / @tricalt
- Date: 2026-05-17
- Type: X post linking to X Article
- Capture method: X API metadata plus xAI-extracted article summary

## Summary
This source argues that memory and skills are two views of the same agent harness. Memory is the broad world model an agent uses to act, while skills are compressed procedures and traces of what has worked before. The article's central claim is that separating them into static product primitives misses the important loop: observe the environment, inspect whether the current skill/memory still fits, amend it, and evaluate the next run.

## Key Claims
- Agent memory is not only saved facts; it includes the codebase, tools, filesystem, conversation history, preferences, and observations that shape action.
- Skills are not merely static Markdown prompts; they are reusable, task-specific memory about how to act.
- Skills degrade when the environment changes, so skill maintenance needs an active improvement loop.
- A useful memory system should route, inspect, and revise skills as part of the same world model.
- Cognee is presented as an example where skills are ingested as first-class memory nodes and skill changes become memory events.

## Evidence / Examples
- The X API exposes the linked article title and post metadata.
- xAI extraction summarizes the article's Cognee example: cognee.remember("skills/") treats skill files as memory nodes shared by retrieval and self-improvement runtime.
- The source points to a broader convergence aro

### Daniel Miessler — Claude Code /workflows for Enterprise AI

Source note: `wiki/sources/danielmiessler-claude-code-workflows-enterprise-ai-x-2026-05-25.md`

# Daniel Miessler — Claude Code /workflows for Enterprise AI

## Source Metadata
- Raw path: ../../raw/articles/danielmiessler-claude-code-workflows-enterprise-ai-x-2026-05-25.md
- Original URL: https://x.com/DanielMiessler/status/2058699741140222055
- Author: Daniel Miessler (@DanielMiessler)
- Posted: 2026-05-25T00:00:41.000Z
- Captured: 2026-05-26 via xurl bookmarks capture
- Type: X post
- Evidence strength: bookmark snapshot metadata only; the post is visually anchored by an attached image card

## What it says
Miessler frames Claude Code's upcoming /workflows feature as a significant step, especially for enterprise AI. The key idea is that work should be encoded as reusable workflows rather than handled as a loose stream of prompts.

## Key Claims
- Workflow-level controls are becoming a first-class product surface.
- Enterprise AI benefits when repeatable procedures are encoded explicitly.
- The important unit is not just a prompt, but a reusable operational workflow.

## Evidence / Examples
- The tweet text explicitly calls /workflows significant.
- The attached image card suggests the point is product-level workflow orchestration, not merely a single prompt trick.

## Related Concepts
- [[../concepts/harness-engineering.md]]
- [[../concepts/multi-agent-orchestration.md]]
- [[../concepts/managed-agents.md]]

## Open Questions
- Which classes of enterprise work belong in a reusable workflow surface?
- How much workflow logic should stay user-authored versus product-managed?
- What review and safety gates should wrap reusable workflows by default?

## Backlinks
- [[../concepts/harness-engineering.md]]
- [[../concepts/multi-agent-orchestration.md]]
- [[../concepts/managed-agents.md]]

### Figma — design agent automation and parallel exploration

Source note: `wiki/sources/figma-design-agent-parallel-exploration-automation-x-2026-05-20.md`

# Figma — design agent automation and parallel exploration

## Source Metadata
- Raw path: ../../raw/articles/figma-design-agent-parallel-exploration-automation-x-2026-05-20.md
- Original URL: https://x.com/figma/status/2057164914331128060
- Author: Figma (@figma)
- Posted: 2026-05-20T18:21:50.000Z
- Captured: 2026-05-26 via xurl bookmarks capture
- Type: X post / official product demo
- Evidence strength: bookmark snapshot metadata plus official Figma video preview

## What it says
Figma's design agent can automate repetitive tasks and run explorations in parallel. The demo treats design as a workflow with branches, not a single linear edit session.

## Key Claims
- Repetitive design actions can be automated.
- Exploration can happen in parallel instead of serially.
- The design agent is framed as a production workflow surface, not just a chat UI.

## Evidence / Examples
- The tweet explicitly names automating repetitive tasks and running explorations in parallel.
- The official Figma video preview anchors the claim as a product demo.

## Related Concepts
- [[../concepts/harness-engineering.md]]
- [[../concepts/multi-agent-orchestration.md]]
- [[../concepts/rich-agent-output-artifact.md]]

## Open Questions
- Which design tasks are best treated as parallel branches?
- How does a design-agent workflow preserve authorial intent while automating routine edits?
- What artifact format best exposes the parallel branches for review?

## Backlinks
- [[../concepts/harness-engineering.md]]
- [[../concepts/multi-agent-orchestration.md]]
- [[../concepts/rich-agent-output-artifact.md]]

### leopardracer — Claude keeps running on a knowledge graph

Source note: `wiki/sources/leopardracer-knowledge-graph-claude-limit-x-2026-05-12.md`

# leopardracer — Claude keeps running on a knowledge graph

## Source Metadata
- Raw path: ../../raw/articles/leopardracer-knowledge-graph-claude-limit-x-2026-05-12.md
- Original URL: https://x.com/leopardracer/status/2054178069653418477
- Author: leopardracer (@leopardracer)
- Posted: 2026-05-12T12:33:11.000Z
- Captured: 2026-05-26 via xurl bookmarks capture
- Type: X post / video demo
- Evidence strength: bookmark snapshot metadata plus video-card preview

## What it says
The post describes a knowledge-graph workflow where Claude keeps operating even after the author hits a daily usage limit. The system reads new material, creates fresh connections, writes a brief, and surfaces a question worth thinking about.

## Key Claims
- A knowledge-graph workflow can keep going beyond a single session.
- The surrounding notes and graph matter as much as the model call.
- The output is not only content generation but also synthesis and promptable next questions.

## Evidence / Examples
- The tweet explicitly says the author hit the daily Claude limit while the system kept running.
- The text references Obsidian, new connections, a brief, and one question for the day.

## Related Concepts
- [[../concepts/agent-knowledge-loop.md]]
- [[../concepts/harness-engineering.md]]
- [[../concepts/long-running-agents.md]]

## Open Questions
- What minimum note structure keeps a self-running knowledge loop legible?
- How much of the loop should live in the graph versus in the model?
- Which checks are needed to keep this kind of autonomous compounding trustworthy?

## Backlinks
- [[../concepts/agent-knowledge-loop.md]]
- [[../concepts/harness-engineering.md]]
- [[../concepts/long-running-agents.md]]

### スナガク — Claude Design helps generate a video workflow end to end

Source note: `wiki/sources/suna-gaku-claude-design-remotion-video-generation-x-2026-05-24.md`

# スナガク — Claude Design helps generate a video workflow end to end

## Source Metadata
- Raw path: ../../raw/articles/suna-gaku-claude-design-remotion-video-generation-x-2026-05-24.md
- Original URL: https://x.com/suna_gaku/status/2058518930503930144
- Author: スナガク (@suna_gaku)
- Posted: 2026-05-24T12:02:13.000Z
- Captured: 2026-05-26 via xurl bookmarks capture
- Type: X post / workflow report
- Evidence strength: bookmark snapshot metadata plus tweet text; media preview not fully transcribed

## What it says
The author says Claude Design is valuable enough to keep paying for even if Claude Code usage drops. In the concrete example, the agent proposes multiple video styles, the author selects one, and the system carries the work through to video generation.

## Key Claims
- Claude Design can be worth paying for on its own.
- The tool can explore multiple output styles quickly.
- A creative workflow can move from idea to implemented video in one loop.

## Evidence / Examples
- The tweet explicitly describes using Claude Design to produce a YouTube-style video from an existing app.
- The workflow includes style exploration, selection, implementation, and final generation.

## Related Concepts
- [[../concepts/rich-agent-output-artifact.md]]
- [[../concepts/harness-engineering.md]]
- [[../concepts/tool-accessibility.md]]

## Open Questions
- Which media workflows are best served by agent-generated variants?
- What review surface is needed when the output is a video rather than text or code?
- How should pricing and usage limits be evaluated for creative-output workflows?

## Backlinks
- [[../concepts/rich-agent-output-artifact.md]]
- [[../concepts/harness-engineering.md]]
- [[../concepts/tool-accessibility.md]]

## 更新された概念・地図

### Concept Notes

KB note: `wiki/concepts/README.md`

# Concept Notes

Each note in this folder should represent a reusable concept that appears across multiple sources.

Recommended structure:
- definition
- why it matters
- related concepts
- supporting sources
- tensions / tradeoffs
- open questions

- [Evidence Quality](evidence-quality.md)
- [Field-Deployed Engineer](field-deployed-engineer.md)
- [Product Responsibility Distribution](product-responsibility-distribution.md)
- [Conversion Packaging](conversion-packaging.md)
- [Organizational Intent Clarity](organizational-intent-clarity.md)
- [Exploratory Organization Lens](exploratory-organization-lens.md)
- [Intelligent Delegation](intelligent-delegation.md)
- [Conversational Feedback Learning](conversational-feedback-learning.md)
- [Spec-Code-Test Loop](spec-code-test-loop.md)
- [Heavy Thinking](heavy-thinking.md)
- [Sustainable AI Work](sustainable-ai-work.md)
- [AI Adoption J-Curve](ai-adoption-j-curve.md)
- [AI ROI Model](ai-roi-model.md)
- [Verification Tax](verification-tax.md)

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
- [[skill-optimization.md]]

## Supporting Sources
- [[../sources/tricalt-memory-skills-same-harness-x.md]]
- [[..

### Rule-Update Loop

KB note: `wiki/concepts/rule-update-loop.md`

---
aliases:
  - Rule-Update Loop
  - Mistake-to-Rule Loop
---

# Rule-Update Loop

## Definition
A lightweight harness pattern where repeated prompts, recurring corrections, or observed agent mistakes are converted into durable rules in files such as `CLAUDE.md`, `AGENTS.md`, skills, templates, or team playbooks.

## Why It Matters
It lowers repeated review cost. Instead of correcting the agent one chat at a time, the human improves the operating environment so future sessions start with better guidance.

## Related Concepts
- [[harness-engineering]]
- [[context-file-system]]
- [[behavioral-stability]]
- [[agent-recognizable-repository]]
- [[approval-policy]]
- [[skill-optimization]]

## Supporting Sources
- [[../sources/claudecode-love-boris-30-claude-code-tips-x.md]]
- [[../sources/gota-purpose-first-harness-design-speakerdeck.md]]
- [[../sources/rkaga-what-harness-engineering-is-and-is-not-zenn.md]]
- [[../sources/masaki-claude-md-rules-for-non-engineers.md]]
- [[../sources/mnilax-

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

### Trace-Driven Improvement

KB note: `wiki/concepts/trace-driven-improvement.md`

---
aliases:
  - Trace-Driven Improvement
---

# Trace-Driven Improvement

## Definition
Improving an agent harness by analyzing execution traces to identify recurring errors, bottlenecks, and loop failures.

## Why It Matters
When model internals are opaque, traces become a practical substrate for systematic iteration.

## Related Concepts
- [[harness-engineering]]
- [[self-verification]]
- [[middleware-controls]]
- [[skill-optimization]]

## Supporting Sources
- [[../sources/langchain-deep-agents-harness-engineering.md]]
- [[../sources/kevin-gu-autoagent-x-thread.md]]
- [[../sources/neural-avb-agentic-memory-transfer-learning-x.md]]

- [[../sources/vmlops-openai-agents-sdk-clean-x.md]]
- [[../sources/mizchi-skill-md-empirical-prompt-tuning-x.md]]
- [[../sources/arxiv-skillopt-executive-strategy-self-evolving-agent-skills.md]]

## Tradeoffs / Tensions
- Trace analysis can overfit to specific benchmarks or workloads.
- Good trace capture requires strong observability discipline.
- Trac

### Agent Harness Control Taxonomy

KB note: `wiki/maps/agent-harness-control-taxonomy.md`

# Agent Harness Control Taxonomy

## Purpose
Normalize the control vocabulary used across the harness-engineering cluster so the KB can compare sources without collapsing distinct mechanisms into one vague idea of "guardrails."

## Core split
Harness controls fall along two practical axes:
1. **When they act** — before action, during action, or after action
2. **How they act** — deterministic/computational or semantic/inferential

This note treats those axes as complementary rather than mutually exclusive.

## Scope split: evaluation, runtime, context, safety
Use this split when a source says "harness" but means different machinery:
- **Evaluation harness**: infrastructure that scores models or task submissions, such as lm-evaluation-harness or SWE-bench-style graders.
- **Runtime harness**: the agent loop that alternates reasoning, tool use, observation, state, and retry behavior.
- **Context harness**: instructions, rule files, memory, retrieval, tools, hooks, skills, MCP servers, an

### Navigation: Harness

KB note: `wiki/navigation/harness.md`

# Navigation: Harness

## Use When
The question is about making agents more reliable through prompts, tools, permissions, repository structure, checks, or workflow design.

## Start Maps
- [[../maps/ai-adoption-roi-and-capability-investment.md]]
- [[../maps/agent-harness-landscape.md]]
- [[../maps/agent-harness-control-taxonomy.md]]
- [[../maps/coding-agent-harness-patterns.md]]
- [[../maps/coding-agent-cognitive-debt-and-review-capacity.md]]
- [[../maps/harness-engineering-vendor-comparison.md]]
- [[../maps/eval-review-reliability.md]]

## Core Concepts
- [[../concepts/ai-adoption-j-curve.md]]
- [[../concepts/verification-tax.md]]
- [[../concepts/harness-engineering.md]]
- [[../concepts/context-first-development.md]]
- [[../concepts/agent-recognizable-repository.md]]
- [[../concepts/context-engineering.md]]
- [[../concepts/environment-bootstrapping.md]]
- [[../concepts/tool-accessibility.md]]
- [[../concepts/gateway-control-plane.md]]
- [[../concepts/managed-agents.md]]
- [[../concept

### Navigation: Memory / Knowledge Substrate

KB note: `wiki/navigation/memory.md`

# Navigation: Memory / Knowledge Substrate

## Use When
The question is about agent memory, knowledge bases, compiled notes, context graphs, team/company brains, or retrieval architecture.

## Start Maps
- [[../maps/context-graph-and-company-brain.md]]
- [[../maps/research-os-query-paths.md]]
- [[../maps/agent-onboarding-kb-codebase.md]]

## Core Concepts
- [[../concepts/compiled-wiki.md]]
- [[../concepts/agent-knowledge-loop.md]]
- [[../concepts/continual-learning.md]]
- [[../concepts/agent-dreaming.md]]
- [[../concepts/context-file-system.md]]
- [[../concepts/context-engineering.md]]
- [[../concepts/llm-inference-performance.md]]
- [[../concepts/workflow-compilation.md]]
- [[../concepts/kv-cache.md]]
- [[../concepts/context-graph.md]]
- [[../concepts/company-brain.md]]
- [[../concepts/agent-first-organization.md]]
- [[../concepts/organizational-intent-clarity.md]]
- [[../concepts/navigable-agent-skills.md]]
- [[../concepts/memory-skill-harness.md]]
- [[../concepts/skill-optimization.

## NotebookLM Podcast用メモ

- まず今日の全体トレンドを話してから、重要ソースを3本に絞って深掘りする。
- ソース単体の紹介で終わらせず、既存KBの概念や地図がどう更新されたかを会話に含める。
- 最後に、明日以降の調査問いを2〜3個提示する。
