<!-- generated: 2026-07-04T13:01:51.210653+00:00 -->
<!-- kb_daily_digest_date: 2026-07-04 -->
# KB Daily Digest Source — 2026-07-04

このページは、knowledge-base-llm の日次更新を NotebookLM に読み込ませるための公開向けソースページです。
Discord通知よりも文脈を厚めに残し、Podcast化しやすいように、今日追加・更新されたソース、概念、地図を文章中心で整理します。

## 今日の全体像

# KB Daily Digest — 2026-07-04

今日の knowledge-base-llm は、UTC 2026-07-04 00:12 の `KB ingest: daily X bookmarks 2026-07-04` により、Xブックマーク由来の新規 raw/source notes が4本追加されました。新規 raw は `raw/articles/cat-claude-tag-computer-use-setup-x-2026-07-03.md`、`raw/articles/openwiki-background-docs-agents-md-x-2026-07-02.md`、`raw/articles/shinyaa31-slackbot-mcp-client-spec-zenn-x-2026-07-02.md`、`raw/repos/ctxrs-ctx-search-coding-agent-history-github-2026-07-03.md`、および `raw/x/bookmarks/bookmarks-20260704T0000Z.json` です。wiki 側では対応する `wiki/sources/` が4本増え、`agent-harness-landscape`、`approval-policy-patterns-and-escalation`、`coding-agent-harness-patterns` の3つの map が更新されています。

全体トレンドは、「エージェントに作業させる」段階から、「エージェントの記憶、オンボーディング、権限境界、repo legibility をどう維持するか」へ寄っています。ctxrs/ctx は過去の coding-agent 履歴をローカル検索可能な SQLite substrate に変える話で、OpenWiki は repo docs と AGENTS.md を背景で保守する話です。Claude Tag の setup tip は docs と computer use をオンボーディング面として使う方向を示し、Slackbot MCP client spec は MCP 導入を connection/auth/rollout の設計問題として扱う必要を示しています。

重要ソース1本目は、`ctxrs/ctx - search the coding agent history on your machine` です。これは Codex、Claude Code、Cursor などの coding-agent 履歴をローカルに集め、SQLite に正規化し、検索できるようにする Rust CLI として取り込まれました。KB上では `agent-knowledge-loop`、`context-file-system`、`compiled-wiki`、`navigable-agent-skills` に接続されています。実務上の価値は、過去の agent session を「消えたチャットログ」ではなく、後から検索・再利用・要約できる作業記憶として扱える点です。

重要ソース2本目は、`Brace - OpenWiki background docs and AGENTS.md updates` です。OpenWiki は、repo のドキュメント生成と AGENTS.md 更新を背景で継続し、コードベースを読みやすい状態に保つ仕組みとして整理されました。KBでは `compiled-wiki`、`context-file-system`、`agent-knowledge-loop`、`workflow-compilation` に接続されています。ポイントは、ドキュメントを「作業後に人間が清掃するもの」ではなく、agent と repo の間に常駐する保守ループとして見ることです。

重要ソース3本目は、`しんや - Slackbot MCP client specification` です。今回の capture は記事本文までは取得していませんが、共有された Zenn 記事タイトルから、Slackbot MCP の導入では connection method、authentication、organization-level rollout が中心論点になると整理されています。KBでは `approval-policy`、`managed-agents`、`tool-accessibility`、`harness-engineering` に接続され、`approval-policy-patterns-and-escalation` map にも追記されました。MCPは単にツールをつなぐ規格ではなく、どのユーザー・組織権限で、どこまで動かすかを決める approval surface でもある、という読みです。

4本目の `cat - Claude Code computer use setup for Claude Tag` は、Claude Code with computer use を Claude Tag のセットアップ面として使う短い product tip です。docs を task specification として渡し、GitHub、data warehouse、Google Drive などの接続対象を bootstrap する、という実践的な示唆として取り込まれました。KBでは `managed-agents`、`context-engineering`、`tool-accessibility`、`agent-onboarding-kb-codebase` に接続されています。短い投稿なので実装境界の確度は限定的ですが、「docs が人間向け説明ではなく、computer-use agent が進める onboarding script になる」という方向性は重要です。

今日更新された地図では、`agent-harness-landscape` に「Agent history and doc maintenance」と「July 2026 xurl bookmarks ingest」が追加され、agent history search と background doc generation が single-session を越える repo legibility を作るものとして位置づけられました。`coding-agent-harness-patterns` には、Claude Tag setup、ctxrs/ctx、OpenWiki、Slackbot MCP の4本がまとめて追加され、harness の構成要素が runtime や tool API だけでなく、履歴検索、docs upkeep、auth rollout に広がっていることが明確になりました。

実務上の読みどころは、今日の4本がどれも「モデルを強くする」話ではなく、「作業の周辺構造を長持ちさせる」話である点です。ctxrs/ctx は過去作業の recall を支え、OpenWiki は repo の説明可能性を支え、Claude Tag setup は導入手順を agent に渡しやすくし、Slackbot MCP spec は組織導入時の権限設計を前面に出します。エージェント運用の成熟は、派手な autonomous demo よりも、履歴、docs、権限、接続設定のような地味な surface がどれだけ整うかに依存していきそうです。

次に追う問いは、agent history index をどの粒度で保存・要約・redact するべきか、AGENTS.md の自動更新にどの review gate を置くべきか、computer-use onboarding で人間が確認すべき境界はどこか、そして Slackbot MCP のような組織導入で approval policy をユーザー単位・workspace単位・ツール単位のどこに置くべきか、の四つです。Podcastでは、「エージェントの能力拡張より、エージェントが働く環境の記憶化・文書化・権限化が進んでいる」という切り口で話すと、今日の更新を一本の流れとして説明しやすいはずです。


## 重要ソース

### cat - Claude Code computer use setup for Claude Tag

Source note: `wiki/sources/cat-claude-tag-computer-use-setup-x-2026-07-03.md`

# cat - Claude Code computer use setup for Claude Tag

## Source Metadata
- Raw path: [[../../raw/articles/cat-claude-tag-computer-use-setup-x-2026-07-03.md]]
- Raw bookmark capture: [[../../raw/x/bookmarks/bookmarks-20260704T0000Z.json]]
- Original URL: https://x.com/i/status/2073149354412822738
- Author: cat (@_catwu)
- Posted: 2026-07-03T20:58:18.000Z
- Captured: 2026-07-04 via xurl bookmarks capture
- Type: X post / product tip
- Evidence strength: bookmark snapshot metadata plus plaintext setup advice

## Summary
The post suggests using Claude Code with computer use as the setup surface for Claude Tag. Instead of hand-wiring each source one by one, the docs become a task specification that can connect GitHub, a warehouse, Drive, and similar systems.

## Key Claims
- Claude Code with computer use can be used to bootstrap Claude Tag.
- The setup path is docs-driven and therefore automatable.
- Team data sources can be connected during that bootstrap flow.

## Evidence / Examples
- The tweet explicitly says to point Claude Code at the Claude Tag docs.
- It names GitHub, a data warehouse, Google Drive, and other sources as connection targets.
- The post is intentionally short, so the details should be read as practical advice rather than a full implementation spec.

## Evidence Quality
- Source type: X post / product tip
- Confidence: medium for the onboarding pattern, lower for the exact automation boundaries
- Supports: managed-agents, context-engineering, harness-engineering, tool-accessibility
- Main limitations: no API or implementation details beyond the one-line tip
- Best use: show that docs and computer use can function as an onboarding surface for agent setup

## Related Concepts
- [[../concepts/managed-agents.md]]
- [[../concepts/context-engineering.md]]
- [

### ctxrs/ctx - search the coding agent history on your machine

Source note: `wiki/sources/ctxrs-ctx-search-coding-agent-history-github-2026-07-03.md`

# ctxrs/ctx - search the coding agent history on your machine

## Source Metadata
- Raw path: [[../../raw/repos/ctxrs-ctx-search-coding-agent-history-github-2026-07-03.md]]
- Raw bookmark capture: [[../../raw/x/bookmarks/bookmarks-20260704T0000Z.json]]
- Original URL: https://x.com/i/status/2072836592868438486
- Primary URL: https://github.com/ctxrs/ctx
- Author: hiroppy (@about_hiroppy)
- Posted: 2026-07-03T00:15:29.000Z
- Captured: 2026-07-04 via xurl bookmarks capture
- Type: GitHub repository
- Evidence strength: bookmark snapshot metadata plus linked GitHub repo

## Summary
ctxrs/ctx is a local Rust CLI for searching coding-agent history already on the machine. The repo description and bookmark text suggest a durable index over Codex, Claude Code, and Cursor histories, which makes past agent work queryable instead of trapped in scattered transcripts.

## Key Claims
- The tool normalizes coding-agent history into SQLite.
- The search surface stays local to the machine.
- The history span includes Codex, Claude Code, and Cursor.
- The CLI is intended for search and indexing rather than just export.

## Evidence / Examples
- The GitHub repo title calls it a fast, local CLI for searching agent history.
- The bookmark text says it normalizes older coding-agent history into SQLite.
- The post explicitly names Codex, Claude Code, and Cursor as input sources.

## Evidence Quality
- Source type: GitHub repository captured from an X bookmark
- Confidence: high for the local search/indexing framing
- Supports: agent-knowledge-loop, context-file-system, compiled-wiki, navigable-agent-skills
- Main limitations: the bookmark snapshot does not show the full schema or retention policy
- Best use: treat coding-agent history as a searchable local substrate rather than disposable cha

### Brace - OpenWiki background docs and AGENTS.md updates

Source note: `wiki/sources/openwiki-background-docs-agents-md-x-2026-07-02.md`

# Brace - OpenWiki background docs and AGENTS.md updates

## Source Metadata
- Raw path: [[../../raw/articles/openwiki-background-docs-agents-md-x-2026-07-02.md]]
- Raw bookmark capture: [[../../raw/x/bookmarks/bookmarks-20260704T0000Z.json]]
- Original URL: https://x.com/i/status/2072744824470724887
- Primary URL: https://x.com/BraceSproul/status/2072744824470724887/photo/1
- Author: Brace (@BraceSproul)
- Posted: 2026-07-02T18:10:50.000Z
- Captured: 2026-07-04 via xurl bookmarks capture
- Type: X post / photo card
- Evidence strength: bookmark snapshot metadata plus attached photo card

## Summary
OpenWiki is presented as a background docs engine: it generates documentation, keeps AGENTS.md updated, and self-updates so the repo stays readable without manual cleanup after every change. The useful angle here is less "wiki app" and more "continuous repo documentation maintenance."

## Key Claims
- Background generation can keep docs current without a dedicated cleanup pass.
- AGENTS.md can act as a durable onboarding/control file for agents.
- Self-update behavior makes the docs surface part of the maintenance loop.

## Evidence / Examples
- The post text explicitly says OpenWiki runs in the background and updates AGENTS.md.
- The screenshot/card makes it feel like an automation product, not a one-off note generator.
- The claim that it can update itself should be treated as product intent unless the repo docs confirm implementation details.

## Evidence Quality
- Source type: X post / photo card
- Confidence: medium for the docs-maintenance framing
- Supports: compiled-wiki, context-file-system, agent-knowledge-loop, workflow-compilation
- Main limitations: the bookmark text is promotional and does not show the implementation
- Best use: compare doc-maintenance tooling 

### しんや - Slackbot MCP client specification

Source note: `wiki/sources/shinyaa31-slackbot-mcp-client-spec-zenn-x-2026-07-02.md`

# しんや - Slackbot MCP client specification

## Source Metadata
- Raw path: [[../../raw/articles/shinyaa31-slackbot-mcp-client-spec-zenn-x-2026-07-02.md]]
- Raw bookmark capture: [[../../raw/x/bookmarks/bookmarks-20260704T0000Z.json]]
- Original URL: https://x.com/i/status/2072650961374638530
- Primary URL: https://zenn.dev/truestar/articles/6a5843fa881d72
- Author: しんや (@shinyaa31)
- Posted: 2026-07-02T11:57:51.000Z
- Captured: 2026-07-04 via xurl bookmarks capture
- Type: X post / article share
- Evidence strength: bookmark snapshot metadata plus linked Zenn article title

## Summary
The bookmark points at a Zenn article about Slackbot's MCP client spec. Based on the title, the piece appears to organize the implementation around connection methods, authentication, and organization-level rollout caveats.

## Key Claims
- Slackbot MCP needs a client-side spec, not just a platform announcement.
- Connection method and authentication are central implementation concerns.
- Organization-wide adoption has rollout and governance implications.

## Evidence / Examples
- The tweet shares an article explicitly titled around connection methods, auth, and organizational deployment concerns.
- The bookmark's linked URL points to a Zenn article rather than an X-only teaser.
- The post itself is short, so the note should be read as an inference from the title and share text.

## Evidence Quality
- Source type: X post / article share
- Confidence: medium; the article title is informative, but the full article was not fetched in this pass
- Supports: approval-policy, managed-agents, tool-accessibility, harness-engineering
- Main limitations: the current capture only exposes the share text and title, not the article body
- Best use: treat MCP adoption as an auth and rollout problem as much

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

### Approval Policy Patterns and Escalation

KB note: `wiki/maps/approval-policy-patterns-and-escalation.md`

# Approval Policy Patterns and Escalation

## Purpose
Connect approval policy from a vague safety setting into a concrete design space: what gets auto-approved, what gets reviewed, what gets blocked, and how escalation changes throughput.

## Core idea
Approval policy is not one binary switch between autonomy and safety. In practice it is a stack of gates across action type, environment, review path, and failure handling.

## Source anchors
- [[../sources/anthropic-claude-code-auto-mode.md]]
- [[../sources/codex-subagents-docs.md]]
- [[../sources/openai-codex-plugin-cc-github.md]]
- [[../sources/anthropic-claude-code-web-scheduled-tasks-docs.md]]
- [[../sources/zaid-mercury-agent-security-cost-identity-x.md]]
- [[../sources/akshay-pachaar-opus-4-7-prompting-session-management-x.md]]
- [[../sources/claudedevs-enterprise-managed-auth-extension-to-mcp-x-2026-06-18.md]]
- [[../sources/shinyaa31-slackbot-mcp-client-spec-zenn-x-2026-07-02.md]]

## Common escalation ladder

### 1. Auto-allowe

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
