<!-- generated: 2026-05-28T13:01:34.001785+00:00 -->
<!-- kb_daily_digest_date: 2026-05-28 -->
# KB Daily Digest Source — 2026-05-28

このページは、knowledge-base-llm の日次更新を NotebookLM に読み込ませるための公開向けソースページです。
Discord通知よりも文脈を厚めに残し、Podcast化しやすいように、今日追加・更新されたソース、概念、地図を文章中心で整理します。

## 今日の全体像

# KB Daily Digest 2026-05-28

今日の knowledge-base-llm は、X ブックマーク由来の5本を新規 ingest / compile した。中心にあるのは、AI coding agent のレビュー能力をどう維持するか、そしてそのレビューを単発の人間チェックではなく、hook、browser automation、test clock、wiki linkage、autoreview skill といった周辺構造へどう分散するか、という話だ。

重要ソースの1本目は **mizchi — review visibility and black-box testing**。AI生成コードの量が増えると、レビューの失敗は「読めばわかる」ではなく「読み切れない」ことから起きる。mizchi の指摘は、レビュー能力そのものがボトルネックになり、line-by-line の目視だけでは追いつかないというもの。KB上では [[../../wiki/maps/coding-agent-review-rubric.md]] に接続され、レビュー観点として correctness や safety だけでなく、comprehension / reviewability を明示的に扱う理由が強くなった。

2本目は **Oikon — security guidance hooks for Claude Code**。Claude Code の security-guidance plugin hook が、裏側で Claude Agent SDK を呼び、メインの agent 作業と並行して脆弱性レビューを走らせるというパターンを示している。特に asyncRewake は、レビューを同期的な gate に閉じ込めず、background agent として後から戻す設計の手がかりになる。KBでは [[../../wiki/concepts/harness-engineering.md]]、[[../../wiki/concepts/multi-agent-orchestration.md]]、[[../../wiki/concepts/background-agents.md]] に接続され、hook が単なる通知機構ではなく、review harness の実行面にもなりうることを補強した。

3本目は **steipete — autoreview skill and Codex review loop**。autoreview skill を PR 前に走らせ、何時間もかけて edge case を拾うという話で、レビューが lint の延長ではなく、長時間走る検証プロセスとして扱われ始めていることがわかる。重要なのは「自動レビューは速いから便利」ではなく、「レビュー yield が高いなら latency を払う価値がある」という実務判断だ。KBでは [[../../wiki/maps/coding-agent-review-rubric.md]] と [[../../wiki/maps/coding-agent-harness-patterns.md]] に入り、レビューのコスト、深さ、エスカレーション条件を考える材料になった。

残り2本も、同じトレンドを別角度から支えている。**catnose99 — Stripe test clock plus Codex browser checklist** は、支払い系 SaaS の QA で、Stripe test clock と事前チェックリスト、Codex browser action を組み合わせる実務パターンを示す。subscription renewal、cancellation、expired card のような edge case を、都度の勘ではなく再現可能な checklist / sandbox に落とし込む発想だ。**Haruhiko Okumura — LLM Wiki and knowledge linking** は、Karpathy-style LLM wiki の価値を、単なる保存ではなく知識同士の接続に置く。これは今日の digest 自体とも直結していて、review hook や test checklist のような一回限りの運用知を、KBの concept / map に戻して再利用可能にする意味を支えている。

全体トレンドとしては、AI coding の課題が「コードを生成できるか」から「生成された変更を、誰が、どの視点で、どの環境で、どのくらい深く確認するか」へ移っている。review visibility は人間側の認知限界、security hook は非同期の専門レビュー、autoreview skill は長時間検証、Stripe test clock は再現可能な外部状態、LLM wiki は学習した運用知の蓄積をそれぞれ担当している。別々の小ネタに見えて、全部 review capacity と harness engineering の話としてつながる。

KB内の更新としては、raw/articles 5件、raw/x/bookmarks 1件、wiki/sources 5件が追加された。既存の [[../../wiki/concepts/harness-engineering.md]]、[[../../wiki/concepts/coding-agents.md]]、[[../../wiki/concepts/agent-knowledge-loop.md]]、[[../../wiki/concepts/compiled-wiki.md]] が更新され、[[../../wiki/maps/coding-agent-review-rubric.md]] には新しい supporting sources が追加された。特に review rubric は、AI生成コードの増加に対して「正しさ」だけでなく「レビュー可能性」そのものを評価軸として持つ必要がある、という方向に少し強くなった。

実務上の含意はかなりはっきりしている。agent による実装が増えるほど、レビューは人間の最後の気合いでは回らない。重要な workflow では、チェックリスト、browser automation、sandbox/test clock、非同期 hook、長時間 autoreview、そして結果をKBへ戻す知識ループを組み合わせる必要がある。逆に言うと、まだ人間が毎回ゼロからレビュー観点を考えている箇所は、harness 化できる余地がある。

次に掘るなら、(1) review hook / autoreview / browser checklist / black-box test を review taxonomy 上でどう分けるか、(2) async review の結果をいつ main agent に割り込ませ、いつ後段の注意として扱うべきか、(3) payment や auth のような状態依存ワークフローを agent-readable checklist としてどう標準化するか、がよさそう。

## Important sources

- mizchi — review visibility and black-box testing: https://x.com/mizchi/status/2059567539878068246
- Oikon — security guidance hooks for Claude Code: https://x.com/oikon48/status/2059758293414023464
- Peter Steinberger — autoreview skill and Codex review loop: https://x.com/steipete/status/2059453909819654554
- catnose — Stripe test clock plus Codex browser checklist: https://x.com/catnose99/status/2059635758731026533
- Haruhiko Okumura — LLM Wiki and knowledge linking: https://x.com/h_okumura/status/2059504313744199932

## Changed KB files

- raw/articles/catnose99-stripe-test-clock-codex-browser-checklist-x-2026-05-27.md
- raw/articles/h-okumura-llm-wiki-connecting-knowledge-x-2026-05-27.md
- raw/articles/mizchi-review-visibility-black-box-testing-x-2026-05-27.md
- raw/articles/oikon48-security-guidance-hooks-claude-code-x-2026-05-27.md
- raw/articles/steipete-autoreview-skill-codex-review-loop-x-2026-05-27.md
- raw/x/bookmarks/bookmarks-20260528T0004Z.json
- wiki/sources/catnose99-stripe-test-clock-codex-browser-checklist-x-2026-05-27.md
- wiki/sources/h-okumura-llm-wiki-connecting-knowledge-x-2026-05-27.md
- wiki/sources/mizchi-review-visibility-black-box-testing-x-2026-05-27.md
- wiki/sources/oikon48-security-guidance-hooks-claude-code-x-2026-05-27.md
- wiki/sources/steipete-autoreview-skill-codex-review-loop-x-2026-05-27.md
- wiki/concepts/agent-knowledge-loop.md
- wiki/concepts/coding-agents.md
- wiki/concepts/compiled-wiki.md
- wiki/concepts/harness-engineering.md
- wiki/maps/coding-agent-review-rubric.md


## 重要ソース

### catnose99 — Stripe test clock plus Codex browser checklist

Source note: `wiki/sources/catnose99-stripe-test-clock-codex-browser-checklist-x-2026-05-27.md`

# catnose99 — Stripe test clock plus Codex browser checklist

## Source Metadata
- Raw path: raw/articles/catnose99-stripe-test-clock-codex-browser-checklist-x-2026-05-27.md
- Original URL: https://x.com/catnose99/status/2059635758731026533
- Author: catnose
- Date: 2026-05-27
- Type: X post
- Evidence strength: direct xurl bookmarks capture

## Summary
catnose recommends a practical workflow for paid web services: prepare a checklist for payment-related checks, then use Codex browser actions to run through the checklist. The post specifically calls out Stripe test clocks as a way to reproduce subscription renewals, cancellations, and expired cards inside a sandbox.

## Key Claims
- Payment flows are easier to validate when the checks are prewritten as a checklist.
- Browser automation turns the checklist into a repeatable QA loop.
- Stripe test clocks make subscription edge cases reproducible instead of ad hoc.

## Evidence / Examples
- The post text is the only evidence in this capture.
- The bookmark is image-only, so there is no richer article metadata here.

## Evidence Quality
- Source type: X post
- Confidence: moderate for the operational pattern, lower for any generalization beyond the author’s own workflow.

## Related Concepts
- [[../concepts/coding-agents.md]]
- [[../concepts/harness-engineering.md]]
- [[../concepts/tool-accessibility.md]]
- [[../concepts/spec-code-test-loop.md]]

## Open Questions
- Which recurring QA flows should become checklists by default?
- Where should the browser runner end and a dedicated test harness begin?
- How much of payment-edge-case testing can be standardized across SaaS products?

## Backlinks
- [[../concepts/coding-agents.md]]
- [[../concepts/harness-engineering.md]]
- [[../concepts/tool-accessibility.md]]
- [[../concepts/

### Haruhiko Okumura — LLM Wiki and knowledge linking

Source note: `wiki/sources/h-okumura-llm-wiki-connecting-knowledge-x-2026-05-27.md`

# Haruhiko Okumura — LLM Wiki and knowledge linking

## Source Metadata
- Raw path: raw/articles/h-okumura-llm-wiki-connecting-knowledge-x-2026-05-27.md
- Original URL: https://x.com/h_okumura/status/2059504313744199932
- Author: Haruhiko Okumura
- Date: 2026-05-27
- Type: X post
- Evidence strength: direct xurl bookmarks capture
- Primary URLs:
  - https://zenn.dev/tsurubee/articles/llm-wiki-connecting-knowledge
  - https://zenn.dev/nori_handa/articles/llm-knowledge-base-karpathy-wiki

## Summary
Haruhiko Okumura bookmarks two Japanese articles about operating a Karpathy-style LLM wiki. One article focuses on how an LLM wiki helps connect knowledge over time; the other frames the same idea as a design for letting AI reliably collect internal know-how without leakage or fragmentation.

## Key Claims
- A well-run LLM wiki is valuable because it helps connect related knowledge, not just store notes.
- Karpathy-style personal wikis are now being adapted into practical internal knowledge workflows.
- The core value is curation and linkage, not raw accumulation.

## Evidence / Examples
- The X post is a two-link curation post.
- The Zenn article titles provide the strongest provenance in this capture.

## Evidence Quality
- Source type: X post linking to secondary articles.
- Confidence: moderate for the theme of connected knowledge; lower for any claims that depend on the full article bodies, which were not fetched here.

## Related Concepts
- [[../concepts/compiled-wiki.md]]
- [[../concepts/agent-knowledge-loop.md]]
- [[../concepts/context-graph.md]]
- [[../concepts/structured-handoff-artifacts.md]]

## Open Questions
- Which linking practices most improve retrieval in a personal wiki?
- When does a linked note graph become a true context graph?
- What is the smallest dura

### mizchi — review visibility and black-box testing

Source note: `wiki/sources/mizchi-review-visibility-black-box-testing-x-2026-05-27.md`

# mizchi — review visibility and black-box testing

## Source Metadata
- Raw path: raw/articles/mizchi-review-visibility-black-box-testing-x-2026-05-27.md
- Original URL: https://x.com/mizchi/status/2059567539878068246
- Author: mizchi
- Date: 2026-05-27
- Type: X post
- Evidence strength: direct xurl bookmarks capture

## Summary
mizchi argues that the current failure mode in AI-generated code review is a visibility problem: teams are producing too much code to inspect line by line, so they need review methods beyond plain text reading. The post also says black-box testing is becoming more valuable because it checks behavior without requiring the reviewer to understand every implementation detail.

## Key Claims
- Review capacity is now a bottleneck when AI generates large code volumes.
- New visualization and inspection methods are needed for review to keep up.
- Black-box testing gains value when internal inspection becomes too expensive.

## Evidence / Examples
- The post text is the only evidence in the capture.
- No linked primary source was included in the bookmark.

## Evidence Quality
- Source type: X post
- Confidence: moderate for the diagnosis, lower for the implied remedies.

## Related Concepts
- [[../concepts/coding-agents.md]]
- [[../concepts/harness-engineering.md]]
- [[../concepts/evidence-quality.md]]
- [[../concepts/verification-tax.md]]
- [[../maps/coding-agent-review-rubric.md]]

## Open Questions
- Which review views are better than line-by-line text for generated code?
- How should a harness balance black-box tests against internal reasoning checks?
- When does review capacity become the limiting factor rather than code generation?

## Backlinks
- [[../concepts/coding-agents.md]]
- [[../concepts/harness-engineering.md]]
- [[../concepts/evidence-q

### Oikon — security guidance hooks for Claude Code

Source note: `wiki/sources/oikon48-security-guidance-hooks-claude-code-x-2026-05-27.md`

# Oikon — security guidance hooks for Claude Code

## Source Metadata
- Raw path: raw/articles/oikon48-security-guidance-hooks-claude-code-x-2026-05-27.md
- Original URL: https://x.com/oikon48/status/2059758293414023464
- Author: Oikon
- Date: 2026-05-27
- Type: X post
- Evidence strength: direct xurl bookmarks capture
- Primary URL: https://github.com/anthropics/claude-code/blob/b7339920b69f4a395c28727a1e2305dc5b122cb2/plugins/security-guidance/hooks/hooks.json#L63

## Summary
Oikon highlights the Claude Code security-guidance plugin hook design. The post says Claude Code hooks can call Claude Agent SDK in the background so a model can review vulnerabilities while the main agent continues, then report back asynchronously. Oikon calls out the asyncRewake pattern as worth studying.

## Key Claims
- Security review is being pushed into hooks rather than bolted on after the fact.
- A background review agent can run while the main agent keeps working.
- asyncRewake: true is an example of a useful async hook pattern.

## Evidence / Examples
- The post text itself is the main evidence.
- The captured URL points at the Claude Code security-guidance hook file in the Anthropic repo.

## Evidence Quality
- Source type: X post with a linked GitHub file.
- Confidence: moderate for the architectural pattern, lower for any implementation detail not visible in the captured hook file excerpt.

## Related Concepts
- [[../concepts/harness-engineering.md]]
- [[../concepts/tool-accessibility.md]]
- [[../concepts/multi-agent-orchestration.md]]
- [[../concepts/background-agents.md]]

## Open Questions
- Which review work belongs in hooks versus in the main agent loop?
- How should hook output be surfaced so it helps without becoming noisy?
- Which asynchronous review patterns are safe to sta

### steipete — autoreview skill and Codex review loop

Source note: `wiki/sources/steipete-autoreview-skill-codex-review-loop-x-2026-05-27.md`

# steipete — autoreview skill and Codex review loop

## Source Metadata
- Raw path: raw/articles/steipete-autoreview-skill-codex-review-loop-x-2026-05-27.md
- Original URL: https://x.com/steipete/status/2059453909819654554
- Author: Peter Steinberger
- Date: 2026-05-27
- Type: X post
- Evidence strength: direct xurl bookmarks capture
- Primary URLs:
  - http://crabbox.sh
  - https://github.com/openclaw/agent-skills/blob/main/skills/autoreview/SKILL.md

## Summary
Peter Steinberger says autoreview is one of the most impactful skills in his stack because it automatically reviews code before a PR lands and catches many edge cases. He adds that the loop can run for hours, which implies the skill is used as a serious review harness rather than a quick lint pass.

## Key Claims
- Automated review before merge can catch edge cases that humans miss.
- Long-running review loops are acceptable when the review yield is high enough.
- Review skills are becoming a meaningful part of the coding stack, not just a convenience.

## Evidence / Examples
- The post text is the main evidence.
- The bookmark also points to a docs page and an agent skill file for autoreview.

## Evidence Quality
- Source type: X post with primary links.
- Confidence: moderate for the workflow pattern, lower for any performance claims about the underlying skill.

## Related Concepts
- [[../concepts/coding-agents.md]]
- [[../concepts/harness-engineering.md]]
- [[../maps/coding-agent-review-rubric.md]]
- [[../maps/coding-agent-harness-patterns.md]]
- [[../concepts/evidence-quality.md]]

## Open Questions
- When is a long-running automated review loop worth the latency cost?
- What cases still require a human reviewer even after autoreview passes?
- Which review findings should trigger immediate autofix versus es

## 更新された概念・地図

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

### Coding Agents

KB note: `wiki/concepts/coding-agents.md`

---
aliases:
  - Coding Agents
---

# Coding Agents

## Definition
Agents that operate in software development environments using code editing, terminal commands, tests, and repository context as part of their task execution.

## Why It Matters
Coding agents are one of the most concrete and operationally demanding forms of LLM agents, making them useful for studying autonomy and oversight in practice.

## Related Concepts
- [[agent-autonomy]]
- [[approval-policy]]
- [[human-in-the-loop]]
- [[spec-code-test-loop.md]]

## Supporting Sources
- [[../sources/anthropic-claude-code-auto-mode.md]]
- [[../sources/anthropic-claude-code-on-the-web-docs.md]]
- [[../sources/openai-codex-plugin-cc-github.md]]
- [[../sources/openai-codex-chrome-plugin-x.md]]
- [[../sources/aws-agent-toolkit-for-aws-x.md]]
- [[../sources/nukonuko-code-with-claude-workshops-x.md]]
- [[../sources/anthropic-claude-code-init-interview-x.md]]
- [[../sources/cursor-3-blog.md]]
- [[../sources/storybook-mcp-react-blog.md]]
- 

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
- [[../sources/akshay-pachaar-wiki-plus-graph-

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

### Coding-Agent Review Rubric

KB note: `wiki/maps/coding-agent-review-rubric.md`

# Coding-Agent Review Rubric

## Purpose
Provide a lightweight reusable review rubric for coding-agent workflows so reviewer agents, human reviewers, and automated review routines use the same judgment axes.

## Why this note exists
The current KB has strong vocabulary for harness controls, but it does not yet turn that vocabulary into a compact operational review standard. This note bridges that gap.

## Recommended core rubric
### 1. Correctness
- Does the change satisfy the intended requirement?
- Does it avoid regressions in existing behavior?
- Are edge cases or failure paths obviously mishandled?

### 2. Safety / Blast Radius
- Is the scope of change proportionate to the task?
- Could it create dangerous side effects, permission mistakes, data corruption, or risky automation behavior?
- Are rollback and containment concerns reasonable?

### 3. Maintainability / Simplicity
- Is the change understandable and locally coherent?
- Are responsibilities separated cleanly?
- Did the impl

## NotebookLM Podcast用メモ

- まず今日の全体トレンドを話してから、重要ソースを3本に絞って深掘りする。
- ソース単体の紹介で終わらせず、既存KBの概念や地図がどう更新されたかを会話に含める。
- 最後に、明日以降の調査問いを2〜3個提示する。
