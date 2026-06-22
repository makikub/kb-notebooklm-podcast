<!-- generated: 2026-06-22T13:02:12.958713+00:00 -->
<!-- kb_daily_digest_date: 2026-06-22 -->
# KB Daily Digest Source — 2026-06-22

このページは、knowledge-base-llm の日次更新を NotebookLM に読み込ませるための公開向けソースページです。
Discord通知よりも文脈を厚めに残し、Podcast化しやすいように、今日追加・更新されたソース、概念、地図を文章中心で整理します。

## 今日の全体像

# KB Daily Digest 2026-06-22

UTC 2026-06-22 の knowledge-base-llm 更新は、X bookmark ingest 由来の新規ソース4本と、それに伴う concept note / compiled wiki の更新だった。新規 raw は `raw/articles/ktknd-atlassian-ai-design-system-design-md-x-2026-06-20.md`、`raw/articles/oikon48-claude-code-catchup-zennfes-slides-x-2026-06-20.md`、`raw/articles/oikon48-claude-code-customization-seven-methods-x-2026-06-19.md`、`raw/articles/yusuke-wada-zennfes-2026-clear-communication-slides-x-2026-06-20.md`。対応する wiki source も4本追加され、`compiled-wiki`、`context-file-system`、`context-first-development`、`harness-engineering`、`navigable-agent-skills`、`rich-agent-output-artifact` が更新された。

全体トレンドは、agent / AI product development を「その場の会話」ではなく、持ち運び可能な文脈、再利用できる設定、レビュー可能な発信物として扱う方向に寄っている。Claude Code 関連の2本は、学習やカスタマイズを個人の勘に閉じず、harness maintenance や onboarding artifact として整理するための材料になる。Atlassian / DESIGN.md の bookmark は、design-system context を Markdown として運べるという点で `context-file-system` と強くつながる。Zennfes の「伝わる発信のつくりかた」は、説明そのものを artifact 化するという観点で `rich-agent-output-artifact` と `context-first-development` に接続された。

重要ソースの1本目は、Oikon 氏の Zennfes 登壇資料「Claude Codeをどのようにキャッチアップしているか」。X bookmark からは deck title card と Speaker Deck URL が確認でき、KBでは evidence strength を medium-high とした。中身の全文は ingest していないため、詳細な手法の断定は避けるべきだが、「速く変わる agent tool をどう追い続けるか」を talk artifact として残している点が重要だ。これは単なる学習メモではなく、チームで共有できる onboarding / workflow capture の入口になる。

重要ソースの2本目は、Oikon 氏による Claude Code カスタマイズ記事への bookmark。捕捉できた本文は短いが、Claude Code の振る舞いを変える手段が7つあり、少なくとも「いつ context に読み込まれるか」「長い session でどう振る舞うか」「どれくらい指示に従いやすいか」という観点が含まれる。KB上では、これは prompt writing の話だけではなく、configuration-driven behavior shaping と harness tuning の話として扱われた。特に long-session behavior は、単発回答よりも継続作業を前提にする Codex / Claude Code 的な使い方では重要な制御面になる。

重要ソースの3本目は、かつき氏の Atlassian AI and design systems / DESIGN.md に関する bookmark。DESIGN.md は design-system context を Markdown で持ち運ぶ形式だという短い signal だが、KBにとっては大きい。design system を Figma や実装コードだけのものとしてではなく、agent や別ツールへ渡せる portable textual context として扱えるからだ。これは `compiled-wiki` や `context-file-system` の「文脈をファイルとして運用する」発想と同じ方向を向いており、将来的には repo 内の `DESIGN.md` schema、component guideline、token、interaction rule をどう束ねるかという問いにつながる。

もう1本の重要な補助ソースは、Yusuke Wada 氏が紹介した Zennfes 2026 の slide deck「伝わる発信のつくりかた」。bookmark 上では title card レベルの情報に限られるため、deck の内容を細かく要約する段階ではない。ただし、この source は「発信の質」を個人の文章術としてではなく、構造化された reviewable artifact として扱う材料になる。agent が作る report、digest、slide、rich output は、あとから人間が読み返し、別の文脈に再利用できて初めて knowledge artifact になる、という KB の方向性を補強している。

概念更新では、`context-file-system` が DESIGN.md と Claude Code customization の両方を吸収し、文脈を「会話中に思い出すもの」ではなく「適切な時点で読み込まれ、長い session を支えるファイル群」として扱う見方が強まった。`harness-engineering` と `navigable-agent-skills` は、Claude Code のキャッチアップ資料とカスタマイズ面を受けて、agent harness を継続的に調整・学習・説明する対象として見る方向に更新された。`rich-agent-output-artifact` は Zennfes slide deck 群を、単発の共有リンクではなく、知識の受け渡し形式として読む足場を得た。

実務上の示唆は、AI開発や agent 運用の品質は、モデル選定や一回の prompt だけでは決まらないということだ。チームが使う design system を Markdown 化して渡せるか、Claude Code のカスタマイズ面をどこまで明示できるか、長い session の振る舞いをどう安定させるか、学習資料や発信物をあとから再利用できる artifact として残せるか。今日の4本は派手な新製品ニュースではないが、agent を日常業務に組み込むための地味で重要な基盤を示している。

Podcastで掘るなら、今日は「文脈はどこに置くべきか」という一本の問いにまとめるとよい。前半で DESIGN.md を使い、design system の暗黙知を Markdown として持ち運ぶ意味を話す。中盤で Claude Code customization と catch-up deck を使い、agent の振る舞いを設定・学習・共有する harness engineering として捉える。後半で「伝わる発信のつくりかた」を使い、知識を人間にも agent にも再利用しやすい artifact にするには、説明そのものの構造が必要だという話につなげる。

次に追う問いは、DESIGN.md の実際の schema や Atlassian 記事本文、Oikon 氏の2つの Claude Code 資料の具体的な checklist / workflow、そして Zennfes slide deck の中身をどこまで KB の durable note に落とし込めるかの4つ。今日の ingest は bookmark snapshot が多く、証拠強度は medium 止まりのものもある。次の compile では、primary source の本文や deck 本体を読んで、現在の source note をより強い evidence に育てるのが自然だ。

公開HTML: https://makikub.github.io/kb-notebooklm-podcast/digest/2026-06-22/

NotebookLM用 source.md: https://makikub.github.io/kb-notebooklm-podcast/digest/2026-06-22/source.md


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

### ktknd - Atlassian AI and design systems note on DESIGN.md

Source note: `wiki/sources/ktknd-atlassian-ai-design-system-design-md-x-2026-06-20.md`

# ktknd - Atlassian AI and design systems note on DESIGN.md

## Source Metadata
- Raw path: [[../../raw/articles/ktknd-atlassian-ai-design-system-design-md-x-2026-06-20.md]]
- Original URL: https://x.com/i/status/2068156556513050971
- Author: かつき🌏AI時代のプロダクト開発と事業創出 / @ktknd
- Posted: 2026-06-20T02:18:42.000Z
- Captured: 2026-06-22 via xurl bookmarks capture
- Type: X post / bookmark snapshot
- Evidence strength: bookmark snapshot text only; no primary article URL or title card was exposed

## Summary
This bookmark highlights an Atlassian article about AI and design systems and calls out DESIGN.md as a portable Markdown format for carrying design-system context. The useful implication for this KB is that design-system knowledge can be treated as structured, transferable context rather than only as visual assets or scattered docs.

## Key Claims
- DESIGN.md is a format for carrying design-system context in Markdown.
- AI and design-system practice can be discussed together as a workflow, not only as separate disciplines.
- Portable textual context is valuable when design systems need to move across tools or teams.

## Evidence / Examples
- The bookmark text explicitly says the article was good and that DESIGN.md is a Markdown format for transporting design-system context.
- No URL, article title, or body text was captured, so the claim should be read as a bookmark-level signal rather than a full article summary.

## Evidence Quality
- Source type: practitioner X post
- Confidence: medium
- Supports: compiled-wiki practices, context-file-system framing, and design-context portability
- Main limitations: no primary article link exposed; the note is based on a short bookmark excerpt
- Best use: a compact pointer for discussions about design systems as portable machine-readabl

### Oikon - Claude Code catch-up Zennfes slides

Source note: `wiki/sources/oikon48-claude-code-catchup-zennfes-slides-x-2026-06-20.md`

# Oikon - Claude Code catch-up Zennfes slides

## Source Metadata
- Raw path: [[../../raw/articles/oikon48-claude-code-catchup-zennfes-slides-x-2026-06-20.md]]
- Original URL: https://x.com/i/status/2068237495381418113
- Primary URL: https://speakerdeck.com/oikon48/claude-codewodonoyouni-kiyatutiatupusiteiruka
- Author: Oikon / @oikon48
- Posted: 2026-06-20T07:40:19.000Z
- Captured: 2026-06-22 via xurl bookmarks capture
- Type: X post / slide deck
- Evidence strength: bookmark snapshot metadata plus title card and linked slides

## Summary
This bookmark points to a Zennfes slide deck about how the author keeps up with Claude Code. It is valuable as a practitioner artifact because it likely packages habits, workflow choices, and learning loops into a shareable deck rather than a loose thread.

## Key Claims
- The deck is a concrete Zennfes talk artifact on Claude Code adoption and learning.
- A slide deck can serve as a compact reusable explanation of a workflow.
- Practitioner notes about staying current on tooling are part of harness maintenance, not just personal study.

## Evidence / Examples
- The bookmark text explicitly identifies the deck as the author's talk materials.
- The linked deck title is directly visible in the X card.

## Evidence Quality
- Source type: slide-deck bookmark
- Confidence: medium-high
- Supports: navigable-agent-skills, harness engineering, and onboarding / workflow capture
- Main limitations: the deck content itself was not read in this ingest
- Best use: a practical pointer for Claude Code onboarding and workflow-sharing discussions

## Related Concepts
- [[../concepts/navigable-agent-skills.md]]
- [[../concepts/harness-engineering.md]]
- [[../concepts/rich-agent-output-artifact.md]]
- [[../concepts/context-file-system.md]]

## Related M

### Oikon - Claude Code customization article for beginners

Source note: `wiki/sources/oikon48-claude-code-customization-seven-methods-x-2026-06-19.md`

# Oikon - Claude Code customization article for beginners

## Source Metadata
- Raw path: [[../../raw/articles/oikon48-claude-code-customization-seven-methods-x-2026-06-19.md]]
- Original URL: https://x.com/i/status/2067986260803645898
- Author: Oikon / @oikon48
- Posted: 2026-06-19T15:02:00.000Z
- Captured: 2026-06-22 via xurl bookmarks capture
- Type: X post / bookmark snapshot
- Evidence strength: bookmark snapshot summary text only; no primary article URL or title card was exposed

## Summary
This bookmark points to a beginner-friendly article about customizing Claude Code. The summarized hook is that there are seven separate ways to shape behavior, spanning context-loading, long-session behavior, and how willing the agent is to follow instructions. That makes it a useful source for thinking about Claude Code as a configurable operating environment rather than a fixed product.

## Key Claims
- Claude Code behavior can be customized through multiple distinct control surfaces.
- At least some of those surfaces relate to when context is loaded, how the agent behaves over long sessions, and how strictly it follows instructions.
- Practical Claude Code usage should consider harness tuning, not only prompt writing.

## Evidence / Examples
- The bookmark explicitly summarizes the article as describing seven ways to customize Claude Code behavior.
- The captured excerpt names three of the categories, which is enough to place the source in the harness and context-management cluster.

## Evidence Quality
- Source type: practitioner X post
- Confidence: medium
- Supports: harness engineering, context management, and configuration-driven behavior shaping
- Main limitations: no article title or URL exposed in the capture
- Best use: a compact pointer for Claude Code configuratio

### Yusuke Wada - Zennfes talk slides on clear communication

Source note: `wiki/sources/yusuke-wada-zennfes-2026-clear-communication-slides-x-2026-06-20.md`

# Yusuke Wada - Zennfes talk slides on clear communication

## Source Metadata
- Raw path: [[../../raw/articles/yusuke-wada-zennfes-2026-clear-communication-slides-x-2026-06-20.md]]
- Original URL: https://x.com/i/status/2068362160468893784
- Primary URL: https://yoshiko-pg.github.io/talks/zennfes-2026/
- Author: Yusuke Wada / @yusukebe
- Posted: 2026-06-20T15:55:42.000Z
- Captured: 2026-06-22 via xurl bookmarks capture
- Type: X post / slide deck
- Evidence strength: bookmark snapshot metadata plus title card and linked slides

## Summary
This bookmark points to a slide deck titled 「伝わる発信のつくりかた」 from Zennfes 2026. Even without the full deck body in capture, the source is useful as a reminder that effective communication often deserves the same artifact quality as code: a slide deck can externalize the structure of an explanation, not just the result.

## Key Claims
- The deck is a talk artifact about how to make communication land clearly.
- Slide decks can act as rich, reviewable handoff artifacts.
- Communication quality is itself a workflow problem, not only a writing-style problem.

## Evidence / Examples
- The X card exposes the slide title and notes that it is the Zennfes 2026 slide deck.
- The bookmark text is short, so the title card is the main directly visible evidence.

## Evidence Quality
- Source type: slide-deck bookmark
- Confidence: medium
- Supports: rich output artifacts, context-first development, and explanation design
- Main limitations: no deck body was captured here; title-level interpretation only
- Best use: a reference for turning explanations and talks into durable reviewable artifacts

## Related Concepts
- [[../concepts/rich-agent-output-artifact.md]]
- [[../concepts/context-first-development.md]]
- [[../concepts/compiled-wiki.md]]

## Rela

## 更新された概念・地図

### Compiled Wiki

KB note: `wiki/concepts/compiled-wiki.md`

---
aliases:
  - Compiled Wiki
---

# Compiled Wiki

## Definition
A compiled wiki is a curated layer of linked Markdown notes derived from raw sources, rather than a direct dump of source material.

## Why It Matters
It lets an LLM work over a cleaner, more connected representation of knowledge while preserving traceability back to raw evidence.

## Related Concepts
- [[agent knowledge loop]]
- [[obsidian as interface]]
- [[knowledge base linting]]
- [[open-knowledge-format]]

## Supporting Sources
- [[../sources/karpathy-personal-llm-kb.md]]
- [[../sources/coreyganim-karpathy-second-brain-clearly-explained-x.md]]
- [[../sources/coreyganim-second-brain-monthly-audit-x.md]]
- [[../sources/shannholmberg-llm-wikid-x.md]]
- [[../sources/farza-farzapedia-x.md]]
- [[../sources/fieldtheory-cli-github.md]]
- [[../sources/obsidian-mind-github.md]]
- [[../sources/contextconor-enterprise-understanding-context-graph-x.md]]
- [[../sources/artemxtech-llm-wiki-vs-notebooklm-x.md]]
- [[../sources/aks

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

### Context-First Development

KB note: `wiki/concepts/context-first-development.md`

---
aliases:
  - Context-First Development
  - Context Checking
  - 30-Minute Waterfall
---

# Context-First Development

## Definition
Context-first development is an AI-assisted software workflow where the main engineering control is not only tests or code-writing, but actively shaping, checking, and refreshing the context that the agent uses to plan and act.

## Why It Matters
When implementation becomes fast, missing or stale context can dominate failure. The engineer's leverage shifts toward deciding what the agent should know, what constraints matter, how the work is sliced, and when the produced artifact should be checked or redirected.

## Workflow Pattern
- Define a small outcome and context pack.
- Let the agent implement or draft quickly.
- Check the result and, crucially, check whether the context was sufficient.
- Update context, constraints, or work item state.
- Repeat in short cycles, sometimes framed as "30-minute waterfall" rather than multi-week sprint cadence.

## R

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

## NotebookLM Podcast用メモ

- まず今日の全体トレンドを話してから、重要ソースを3本に絞って深掘りする。
- ソース単体の紹介で終わらせず、既存KBの概念や地図がどう更新されたかを会話に含める。
- 最後に、明日以降の調査問いを2〜3個提示する。
