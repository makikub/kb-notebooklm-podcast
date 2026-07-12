<!-- generated: 2026-07-12T13:01:45.793478+00:00 -->
<!-- kb_daily_digest_date: 2026-07-12 -->
# KB Daily Digest Source — 2026-07-12

このページは、knowledge-base-llm の日次更新を NotebookLM に読み込ませるための公開向けソースページです。
Discord通知よりも文脈を厚めに残し、Podcast化しやすいように、今日追加・更新されたソース、概念、地図を文章中心で整理します。

## 今日の全体像

# KB Daily Digest 2026-07-12

今日の knowledge-base-llm は、UTC 2026-07-12 00:00 頃の xurl bookmarks ingest によって、raw 3本、wiki source 3本、map更新 3本が追加・更新された。新規ソースは、Takanori Suzuki さんの「AI agents use five graph types」、Emil Kowalski さんの design engineers 向け skills repo、そして t-wada さんの「code How, tests What, commits Why, comments Why not」という短い実践知である。全体としては、エージェントの知識基盤を「Markdownだけで足りるか、グラフが必要か」と問う流れと、skills / comments / commits のような小さな運用アーティファクトを再利用可能なハーネス部品として扱う流れが合流している。

重要ソースの1本目は、Takanori Suzuki さんの「AI agents use five graph types」。KB上では `context-graph`、`company-brain`、`compiled-wiki`、`agent-knowledge-loop` に接続された。ポイントは、AI agent の記憶や知識を単一の knowledge graph として雑に語るのではなく、用途に応じた複数の graph 型として分解する必要がある、という方向づけである。bookmark時点のノートでは、Markdown file approach の弱さにも触れており、今のKBが採っている「inspectable Markdown as compiled wiki」と、runtimeで使う「typed graph / context graph」の役割分担を考える材料になっている。

2本目は、Emil Kowalski さんの `skills` repo。特に `/apple-design` skill が、WWDC videos から抽出した design / motion principles を operational artifact にしている点が取り込まれた。これは coding agent の skill だけでなく、design engineer の判断、レビュー、motion guidance も、再利用可能で versionable な skill としてパッケージできることを示す例である。KBでは `navigable-agent-skills`、`skill-optimization`、`harness-engineering`、`tool-accessibility` に接続され、`agent-harness-landscape` と `coding-agent-harness-patterns` の「design harnesses beyond coding」側を補強している。

3本目は、t-wada さんの「code How, tests What, commits Why, comments Why not」。これは短い mnemonic だが、今日の更新の中ではかなり実務的な芯になっている。コードは実装方法、テストは振る舞い、コミットログは理由、コメントは「なぜそうしないのか」を担う、という分担は、agent handoff や long-running work で説明責任をどこに置くかの設計指針になる。KBでは `structured-handoff-artifacts`、`workflow-compilation`、`context-first-development`、`knowledge-base-linting` と結びついた。

map更新では、`context-graph-and-company-brain.md` が今日の中心に近い。ここでは Markdown wiki と typed graph の比較が整理され、Markdownは inspect / edit / diff / commit に強く、typed graph は relationship traversal、validity windows、permissions、structured invalidation に強い、という分担が明示された。Takanori Suzuki さんの five-graph 記事は、この「knowledge graph だけではない」という注意書きを足す source anchor として効いている。

`agent-harness-landscape.md` と `coding-agent-harness-patterns.md` も更新された。前者には design-engineering skills の例として Emil Kowalski repo が追加され、後者には t-wada mnemonic が「artifact separation rule」として入った。つまり今日のトレンドは、巨大な agent platform の話だけではなく、skill repo、commit message、commenting rule のような小さな作法も、agent harness の品質を左右する部品として扱う方向にある。

全体トレンドとしては、「エージェントの経験をどこに残すか」という問いが一段具体化した日だった。経験を Markdown wiki に残すだけなら人間が読みやすいが、権限・時系列・関係探索・無効化を扱うには graph layer が欲しくなる。一方で、すべてを graph に寄せると、レビュー可能性や編集しやすさを失う可能性がある。今日のKB更新は、Markdownを audit / editorial layer、graphを runtime memory layer、skillsやcommitsを procedural / rationale layer と見る合成案に近づいている。

次に追うべき問いは3つある。第一に、five graph types の具体的な分類をKB内の `context-graph` mapへどう落とすか。第二に、design engineer向けの skill package を、coding skill と同じレビュー・versioning・evaluation の枠で扱えるか。第三に、Why / Why not を commit / comment / wiki / skill のどこへ残すと、将来のagentが最も安全に再利用できるか。今日の追加分は小粒に見えるが、KBの「compiled wiki と context graph を併用する」設計思想を補強する更新だった。

## Important Sources

- Takanori Suzuki - AI agents use five graph types: `wiki/sources/takanorisuzuki-ai-agent-five-graph-types-zenn-x-2026-07-11.md`
- Emil Kowalski - skills for design engineers: `wiki/sources/emilkowalski-skills-design-engineers-github-2026-07-09.md`
- Takuto Wada - code How, tests What, commits Why, comments Why not: `wiki/sources/t_wada-code-how-tests-what-commit-why-comments-why-not-x-2026-07-10.md`

## Changed Maps

- `wiki/maps/context-graph-and-company-brain.md`
- `wiki/maps/agent-harness-landscape.md`
- `wiki/maps/coding-agent-harness-patterns.md`


## 重要ソース

### Emil Kowalski - skills for design engineers

Source note: `wiki/sources/emilkowalski-skills-design-engineers-github-2026-07-09.md`

# Emil Kowalski - skills for design engineers

## Source Metadata
- Raw path: `raw/repos/emilkowalski-skills-github-2026-07-09.md`
- Raw bookmark capture: `raw/x/bookmarks/bookmarks-20260712T0000Z.json`
- Original URL: https://x.com/i/status/2075188252877672732
- Primary URL: https://github.com/emilkowalski/skills
- Author: Emil Kowalski / @emilkowalski
- Posted: 2026-07-09T12:00:09.000Z
- Captured: 2026-07-12 via xurl bookmarks capture
- Type: X post / GitHub repository share
- Evidence strength: bookmark snapshot metadata plus repo title
- Public metrics at capture: 12282 likes, 823 reposts, 110 replies, 79 quotes, 21475 bookmarks, 1677434 impressions

## Summary
The repository is framed as a skill pack for design engineers, with the bookmark specifically highlighting an `/apple-design` skill distilled from WWDC videos into 17 design and motion principles. As a KB source, it is a concrete example of skill packaging for a non-coding specialty instead of a generic prompt library.

## Key Claims
- reusable skills can encode design-engineering judgment
- domain-specific skills can be derived from a curated source set such as WWDC videos
- motion and design review can be operationalized as a skill rather than a one-off checklist

## Evidence / Examples
- The repository title says it is for "Skills for Design Engineers."
- The tweet says the author created a new `/apple-design` skill.
- The tweet says the skill is based on 17 design and motion principles extracted from favorite WWDC videos.

## Evidence Quality
- Source type: X post / repo share
- Confidence: high for the existence of the repo and the skill framing, medium for any broader claim about adoption
- Supports: navigable-agent-skills, skill-optimization, harness-engineering, tool-accessibility
- Main limitations: 

### Takuto Wada - code How, tests What, commits Why, comments Why not

Source note: `wiki/sources/t_wada-code-how-tests-what-commit-why-comments-why-not-x-2026-07-10.md`

# Takuto Wada - code How, tests What, commits Why, comments Why not

## Source Metadata
- Raw path: `raw/articles/t_wada-code-comments-why-not-x-2026-07-10.md`
- Raw bookmark capture: `raw/x/bookmarks/bookmarks-20260712T0000Z.json`
- Original URL: https://x.com/i/status/904916106153828352
- Author: Takuto Wada / @t_wada
- Posted: 2017-09-05T03:56:26.000Z
- Captured: 2026-07-12 via xurl bookmarks capture
- Type: X post
- Evidence strength: bookmark snapshot metadata and the post text itself
- Public metrics at capture: 11045 likes, 3326 reposts, 11 replies, 277 quotes, 5022 bookmarks, 0 impressions

## Summary
This post compresses a useful documentation-separation rule into one line: code should explain How, tests What, commit logs Why, and comments Why not. It is a durable writing heuristic because it assigns each artifact a different job instead of making every layer carry every kind of explanation.

## Key Claims
- source code is the place for implementation details
- tests are the place for behavioral intent
- commit logs should preserve rationale
- comments should explain negative space and rejected alternatives

## Evidence / Examples
- The entire bookmark text is the mnemonic itself.
- The phrasing maps cleanly to versioned engineering artifacts rather than abstract documentation theory.
- The distinction fits repo practices where repeated rationale should move into durable artifacts instead of being re-explained in chat.

## Evidence Quality
- Source type: X post
- Confidence: high for the mnemonic and its utility as a documentation heuristic
- Supports: structured-handoff-artifacts, workflow-compilation, context-first-development, knowledge-base-linting
- Main limitations: this is a short practitioner aphorism, not a formal methodology
- Best use: a compact rule

### Takanori Suzuki - AI agents use five graph types

Source note: `wiki/sources/takanorisuzuki-ai-agent-five-graph-types-zenn-x-2026-07-11.md`

# Takanori Suzuki - AI agents use five graph types

## Source Metadata
- Raw path: `raw/articles/takanorisuzuki-ai-agent-five-graph-types-zenn-x-2026-07-11.md`
- Raw bookmark capture: `raw/x/bookmarks/bookmarks-20260712T0000Z.json`
- Original URL: https://x.com/i/status/2075905048073445758
- Primary URL: https://zenn.dev/knowledge_graph/articles/ai-agent-five-graph-types
- Author: Takanori Suzuki / @takanorisuzuki
- Posted: 2026-07-11T11:28:26.000Z
- Captured: 2026-07-12 via xurl bookmarks capture
- Type: X post / article share
- Evidence strength: bookmark snapshot metadata plus linked Zenn title
- Public metrics at capture: 57 likes, 7 reposts, 0 replies, 0 quotes, 50 bookmarks, 2626 impressions

## Summary
The article argues that AI-agent systems use more than a single knowledge graph. The bookmark description says it covers five graph usage patterns and also explains why the same idea is weaker when implemented only with Markdown files.

## Key Claims
- AI agents use multiple graph types, not just knowledge graphs
- graph choice matters for enterprise AI workflows
- Markdown can work as an interface, but it may be weaker than a graph-backed representation for some tasks

## Evidence / Examples
- The article title explicitly says it is about "five graph types" for AI agents.
- The bookmark description says the author wrote about caveats in using graphs for enterprise AI.
- The bookmark text says the article also explains why a Markdown-file approach is weaker for the same purpose.

## Evidence Quality
- Source type: X post / technical article share
- Confidence: high for the article's framing, medium for any generalized graph taxonomy beyond what is visible in the bookmark
- Supports: context-graph, company-brain, compiled-wiki, agent-knowledge-loop
- Main limitation

## 更新された概念・地図

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



### Context Graph and Company Brain

KB note: `wiki/maps/context-graph-and-company-brain.md`

# Context Graph and Company Brain

## Purpose
This map connects the emerging vocabulary around company-scale agent memory: compiled wiki, context graph, Company Brain, and context farming.

## Core Pattern
1. Raw organizational signals enter the system: docs, chat, logs, emails, tickets, meetings, and decisions.
2. A context layer extracts entities, relationships, rules, provenance, and validity windows.
3. Agents query the layer before acting, ideally receiving only context that is relevant, permitted, and still valid.
4. Humans maintain the layer through review, invalidation, conflict resolution, and context farming.
5. Dreaming-style background review can propose memory cleanup and cross-session pattern promotion, but should preserve provenance and review boundaries.

In an agent-first company, this context layer also becomes an operating surface: named agents read and update role docs, taskboards, status files, decision records, handoffs, and feedback-strength notes so the organiza

## NotebookLM Podcast用メモ

- まず今日の全体トレンドを話してから、重要ソースを3本に絞って深掘りする。
- ソース単体の紹介で終わらせず、既存KBの概念や地図がどう更新されたかを会話に含める。
- 最後に、明日以降の調査問いを2〜3個提示する。
