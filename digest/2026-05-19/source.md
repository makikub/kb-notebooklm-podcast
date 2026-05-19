<!-- generated: 2026-05-19T13:01:20.616654+00:00 -->
<!-- kb_daily_digest_date: 2026-05-19 -->
# KB Daily Digest Source — 2026-05-19

このページは、knowledge-base-llm の日次更新を NotebookLM に読み込ませるための公開向けソースページです。
Discord通知よりも文脈を厚めに残し、Podcast化しやすいように、今日追加・更新されたソース、概念、地図を文章中心で整理します。

## 今日の全体像

# KB Daily Digest - 2026-05-19

2026-05-19 UTC の knowledge-base-llm は、前日の「長期運用・記憶・レビュー面」寄りの流れを受けて、よりプロダクト機能としての coding-agent harness に寄った更新だった。新規 raw/wiki/source としては X bookmarks ingest 由来の4件が入り、Cursor Composer 2.5、Claude Design の token limit 拡張、Devin Auto-Triage、implementation-notes.html という4つの材料が追加された。全体としては、モデル単体の賢さよりも、長く働ける agent、豊かな artifact、運用ループ、実装中の判断ログをどう組み合わせるかに焦点が移っている。

いちばん大きいソースは Cursor の Composer 2.5 告知。Cursor は Composer 2.5 を「これまでで最も有能なモデル」として位置づけ、長時間タスクや instruction following の信頼性を強調している。KB上では、この材料は `coding-agents`、`long-running-agents`、`context-engineering`、`harness-engineering` に接続された。ここで重要なのは、単にベンチマーク上の性能が上がったという話ではなく、実務で崩れやすい「長い作業を継続して、指示を保持し続ける」部分がプロダクト価値の中心として語られている点。

2本目の重要ソースは Claude Design の token limits doubled。Claude Design は、全プランで token limit が倍増し、より大きな creation を扱えるようになったと説明されている。KBでは `rich-agent-output-artifact`、`structured-handoff-artifacts`、`harness-engineering` に接続された。これは coding agent だけの話ではなく、設計・UI・資料・複合 artifact を一回の文脈で扱える範囲が広がるという capacity signal で、分割や再説明のコストを下げる方向の更新として読める。

3本目は Cognition の Devin Auto-Triage。Devin が bug、alert、incident を監視し、調査し、文脈・次の手・場合によっては PR まで返す「AI first-responder」として紹介されている。KBでは `long-running-agents`、`multi-agent-orchestration`、`memory-skill-harness`、`harness-engineering` に接続された。これはエディタ内支援ではなく、運用面の triage loop を agent が担う例で、長期記憶、サブタスク分解、調査、実装提案が同じワークフローに入ってくる。

補助的だが実務上かなり効くのが、Thariq の `implementation-notes.html` prompt pattern。spec 実装中に、仕様からの解釈・逸脱・拡張を browser-readable な HTML artifact に残し続けるというもの。KBでは `rich-agent-output-artifact`、`structured-handoff-artifacts`、`context-engineering`、`verification-tax` に接続された。これは、モデルに「覚えておいて」と頼む代わりに、判断理由をレビュー可能な成果物として残す小さな harness で、レビュー負荷や引き継ぎコストを下げるパターンとして強い。

更新された地図としては `coding-agent-harness-patterns` が中心。新しく「Manager-subagent fleet with durable memory」というパターンが追加され、Devin Auto-Triage を、open-ended だが運用範囲が明確な triage / delegation 形態として整理している。既存の plan files、verifier split、deterministic checks、rule-update loop、durable operating threads、artifact-native review surface に、継続監視と incident response の具体例が加わった形だ。

今日の全体トレンドは、「長く動く agent」と「大きな artifact」と「判断ログ」が同じ方向に伸びていること。Cursor は長時間タスクの信頼性、Claude は大きな creation の文脈容量、Devin は運用ループの自律化、Thariq は実装中判断の外部化を示している。つまり、KBの視点では、agent 活用の実務課題が「モデルにうまく依頼する」から「agent が働ける環境、記憶、成果物、監視範囲を設計する」へさらに寄った。

実務上の示唆は、導入順序を間違えないこと。強いモデルや大きな token limit は便利だが、それだけではレビュー可能性や運用責任は生まれない。小さく始めるなら、長いタスクを渡す前に、進捗ログ、判断ログ、テストや lint、レビュー用 artifact、どこまで自動実行してよいかの境界を用意するのが筋がいい。今日の更新は、個別プロダクトのニュースを、coding-agent harness の部品表として読めるようにしている。

次に追うべき問いは3つある。第一に、Composer 2.5 のような長時間タスク強化は、どの種類の作業で本当にレビュー負荷を下げるのか。第二に、Claude Design のような大きな artifact 文脈は、structured handoff とどう組み合わせると再利用可能になるのか。第三に、Devin Auto-Triage 型の first-responder agent は、どの incident / support 領域なら人間の承認前提で安全に回せるのか。この3点を追うと、agent harness の実務地図がさらに具体化しそう。

## Important Sources

- Cursor - Composer 2.5: `wiki/sources/cursor-ai-composer-2-5-x.md`
- Claude - Claude Design token limits doubled across every plan: `wiki/sources/claudeai-claude-design-token-limits-doubled-x.md`
- Cognition - Devin Auto-Triage: `wiki/sources/cognition-devin-auto-triage-long-term-memory-x.md`

## Supporting Source

- Thariq - implementation-notes.html prompt: `wiki/sources/trq212-implementation-notes-html-prompt-x.md`

## Verification Notes

- New/changed material was detected from git log and mtime under `raw/`, `wiki/`, and `outputs/` for 2026-05-19 UTC.
- Key commit: `a19dd2d Add daily x bookmarks ingest`.
- New raw/source material: 4 X bookmark-derived article/source notes plus `raw/x/bookmarks/bookmarks-20260519T0005Z.json`.
- Evidence limits: all four source notes are X post/card captures with moderate evidence strength; the report avoids claims beyond captured metadata and KB note summaries.


## 重要ソース

### Claude - Claude Design token limits doubled across every plan

Source note: `wiki/sources/claudeai-claude-design-token-limits-doubled-x.md`

# Claude - Claude Design token limits doubled across every plan

## Source metadata
- Raw path: raw/articles/claudeai-claude-design-token-limits-doubled-x-2026-05-18.md
- Original URL: https://x.com/claudeai/status/2056460045756309820
- Bookmark post id: 2056460045756309820
- Author: Claude (@claudeai)
- Date: 2026-05-18
- Type: X post / image card
- Evidence strength: moderate; bookmark text only
- Capture source: xurl bookmarks capture
- Public metrics at capture: 567 reposts, 505 replies, 10130 likes, 260 quotes, 1796 bookmarks, 551799 impressions

## Summary
Claude says Claude Design can now handle larger creations because token limits were doubled across every plan.

## Why It Matters
This is a capacity signal for rich artifact workflows. Bigger token budgets make it easier to keep more structure, layout, and design context in a single pass instead of fragmenting the output.

## Related concepts
- [[../concepts/rich-agent-output-artifact.md]]
- [[../concepts/structured-handoff-artifacts.md]]
- [[../concepts/harness-engineering.md]]

## Backlinks
- [[../../raw/articles/claudeai-claude-design-token-limits-doubled-x-2026-05-18.md]]

### Cognition - Devin Auto-Triage

Source note: `wiki/sources/cognition-devin-auto-triage-long-term-memory-x.md`

# Cognition - Devin Auto-Triage

## Source metadata
- Raw path: raw/articles/cognition-devin-auto-triage-long-term-memory-x-2026-05-18.md
- Original URL: https://x.com/cognition/status/2056396941181727210
- Bookmark post id: 2056396941181727210
- Author: Cognition (@cognition)
- Date: 2026-05-18
- Type: X post / video card
- Evidence strength: moderate; bookmark text only
- Capture source: xurl bookmarks capture
- Public metrics at capture: 43 reposts, 21 replies, 353 likes, 27 quotes, 185 bookmarks, 104214 impressions

## Summary
Devin Auto-Triage is framed as an AI first-responder with long-term memory that can monitor incoming bugs, alerts, and incidents, investigate them, and return with context, next steps, or a PR.

## Why It Matters
This is a strong harness signal: the agent is not just generating code, it is taking ownership of a triage loop with memory, subtasking, and actionable incident response.

## Related concepts
- [[../concepts/long-running-agents.md]]
- [[../concepts/multi-agent-orchestration.md]]
- [[../concepts/memory-skill-harness.md]]
- [[../concepts/harness-engineering.md]]

## Backlinks
- [[../../raw/articles/cognition-devin-auto-triage-long-term-memory-x-2026-05-18.md]]

### Cursor - Composer 2.5

Source note: `wiki/sources/cursor-ai-composer-2-5-x.md`

# Cursor - Composer 2.5

## Source metadata
- Raw path: raw/articles/cursor-ai-composer-2-5-x-2026-05-18.md
- Original URL: https://x.com/cursor_ai/status/2056415413077233983
- Bookmark post id: 2056415413077233983
- Author: Cursor (@cursor_ai)
- Date: 2026-05-18
- Type: X post / image card
- Evidence strength: moderate; bookmark text only
- Capture source: xurl bookmarks capture
- Public metrics at capture: 822 reposts, 604 replies, 8746 likes, 572 quotes, 1552 bookmarks, 10383345 impressions

## Summary
Cursor positions Composer 2.5 as its most capable model yet, especially for sustained work on long-running tasks and instruction-following reliability.

## Why It Matters
This is directly relevant to agent loops. The claim is not just raw benchmark strength; it is that sustained, multi-turn work is getting more dependable, which is the part that usually breaks in practice.

## Related concepts
- [[../concepts/coding-agents.md]]
- [[../concepts/long-running-agents.md]]
- [[../concepts/context-engineering.md]]
- [[../concepts/harness-engineering.md]]

## Backlinks
- [[../../raw/articles/cursor-ai-composer-2-5-x-2026-05-18.md]]

### Thariq - implementation-notes.html prompt

Source note: `wiki/sources/trq212-implementation-notes-html-prompt-x.md`

# Thariq - implementation-notes.html prompt

## Source metadata
- Raw path: raw/articles/trq212-implementation-notes-html-prompt-x-2026-05-18.md
- Original URL: https://twitter.com/trq212/status/2056415973125796184
- Bookmark post id: 2056419378154139656
- Author: Thariq (@trq212)
- Date: 2026-05-18
- Type: X post / text card
- Evidence strength: moderate; bookmark text only
- Capture source: xurl bookmarks capture
- Public metrics at capture: 21 reposts, 0 replies, 324 likes, 6 quotes, 531 bookmarks, 34741 impressions

## Summary
The prompt pattern asks an agent to maintain an implementation-notes.html file while implementing a spec, capturing every place where the implementation diverges from, interprets, or extends the spec.

## Why It Matters
This is a concrete handoff artifact pattern. Instead of hoping the model will remember why it made decisions, the workflow makes the deviations visible in a browser-readable artifact while work is in flight.

## Related concepts
- [[../concepts/rich-agent-output-artifact.md]]
- [[../concepts/structured-handoff-artifacts.md]]
- [[../concepts/context-engineering.md]]
- [[../concepts/verification-tax.md]]

## Backlinks
- [[../../raw/articles/trq212-implementation-notes-html-prompt-x-2026-05-18.md]]

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



## NotebookLM Podcast用メモ

- まず今日の全体トレンドを話してから、重要ソースを3本に絞って深掘りする。
- ソース単体の紹介で終わらせず、既存KBの概念や地図がどう更新されたかを会話に含める。
- 最後に、明日以降の調査問いを2〜3個提示する。
