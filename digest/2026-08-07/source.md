<!-- generated: 2026-08-07T13:01:48.215365+00:00 -->
<!-- kb_daily_digest_date: 2026-08-07 -->
# KB Daily Digest Source — 2026-08-07

このページは、knowledge-base-llm の日次更新を NotebookLM に読み込ませるための公開向けソースページです。
Discord通知よりも文脈を厚めに残し、Podcast化しやすいように、今日追加・更新されたソース、概念、地図を文章中心で整理します。

## 今日の全体像

# KB Daily Digest — 2026-08-07

2026-08-07 UTC の knowledge-base-llm 更新では、OpenAI Developers の Agent Plugins 告知が新規 source note として追加され、`tool-accessibility` と `agent-harness-landscape` が更新されました。件数としては1本の取り込みですが、KB上の意味は大きめです。全体トレンドは、エージェントの能力拡張が「個別クライアントごとの便利機能」から、「スキル、MCP設定、配布、マーケットプレイスを含む共通パッケージ面」へ寄っていることです。

重要ソースの1本目は、OpenAI Developers の X 告知です。短い文面ではありますが、「一度プラグインを作れば、互換性のある agent client で使える」というメッセージが中心にあります。KBでは、この一文を単なる製品告知ではなく、agent tool surface のポータビリティに関するシグナルとして扱っています。つまり、エージェントに何を使わせるかという問題が、プロンプトやローカル設定だけでなく、配布可能なプラグイン単位へ移り始めているという読みです。

2本目の重要ソースは OpenAI の plugins ドキュメントです。source note では、Agent Plugins が Agent Skills と MCP server configurations をまとめる共有形式として整理されています。ここで重要なのは、スキルと外部サービス接続が同じ「プラグイン」という配布単位に入る点です。KBの `tool-accessibility` から見ると、これは人間用ツールをエージェントが発見し、権限つきで使えるようにするための中間層が、より明示的な標準形式へ寄っていることを示します。

3本目の重要ソースは Codex の changelog / build plugins ドキュメントです。Codex が Agent Plugins manifest、workspace plugin publishing、追加の plugin marketplace をサポートするという記述は、プラグインが単なるローカル拡張ではなく、ワークスペース単位・マーケットプレイス単位で流通するものとして扱われていることを示しています。これは、個人の作業環境だけでなく、チームや組織の agent harness にも関わる更新です。

概念ノートでは、`tool-accessibility` に今回の source note が supporting source として追加されました。この概念は「人間が頼っているツールが、エージェントにとって発見可能かつ効果的に使える形で露出している度合い」を扱っています。Agent Plugins はその定義にかなり直接的に当たります。特に、MCP server config と Agent Skills をまとめて共有できるなら、ツール接続・操作手順・利用文脈をバラバラに管理するより、エージェントが利用できる能力パッケージとして扱いやすくなります。

地図ノートでは、`agent-harness-landscape` の OpenAI セクションに Agent Plugins が追記されました。これにより、この地図の OpenAI 関連の流れは、Codex の実行環境、モデル階層やルーティング、音声やメモリのような continuity surface に加えて、プラグイン配布という harness infrastructure の層も含むようになりました。エージェントの性能はモデル単体ではなく、周辺のツール、権限、設定、配布、レビュー、継続性によって決まるという、このKBの中心命題に沿った更新です。

実務上の読みどころは、エージェント導入で作るべきものが「良いプロンプト」だけではなくなっている点です。チームが繰り返し使う操作、外部サービス連携、内部ツールへの接続、レビューや検証の手順は、今後はスキルやMCP設定を含むプラグインとして管理する方が自然になるかもしれません。その場合、重要になるのは機能の追加だけでなく、権限、監査、バージョン管理、公開範囲、マーケットプレイスでの発見性です。

次に追う問いは3つです。第一に、Agent Plugins の「互換性」は、実際にはどのメタデータ、権限モデル、実行環境まで共有されるのか。第二に、Agent Skills と MCP configs は、別クライアントへ持ち出されたときにどれだけ意味を保てるのか。第三に、プラグインの流通面は共通マーケットプレイスへ収束するのか、それとも各agent clientごとのマーケットプレイスが並立するのかです。今日は小さな取り込みですが、agent harness の標準化と配布の方向を示す更新として記録しておく価値があります。


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
- [[cloudflare-os-open-platform-agents-apps-work-x-2026-08-06.md]] — Cloudflare OS launch signal: browser-based agent workspace, curated org context and skills, persistent state, internal-system access, and deployable open-source runtime.
- [[cloudflare-workers-local-tracing-x-2026-08-06.md]] — Cloudflare's local tracing launch: `wrangler dev` emits structured traces for local requests and exposes agent-readable observability for Workers debugging.
- [[openaidevs-agent-plugins-open-standard-x-2026-08-06.md]] — OpenAI Developers' Agent Plugins signal: a shared plugin format plus marketplace publishing across compatible agent clients.
- [[google-research-nested-learning-continual-learning.md]] — Google Research on Nested Learning, continuum memory systems, and Hope as a model-internal continual-learning architecture.
- [[anthropic-claude-code-large-codebases.md]] — Anthropic on Claude Code at large-codebase scale: live-code navigation, harness extension points, layered context files, LSP/subagents, 

### OpenAI Developers - Agent Plugins

Source note: `wiki/sources/openaidevs-agent-plugins-open-standard-x-2026-08-06.md`

# OpenAI Developers - Agent Plugins

## Source Metadata
- Raw path: `../../raw/articles/openaidevs-agent-plugins-open-standard-x-2026-08-06.md`
- Raw bookmark capture: `../../raw/x/bookmarks/bookmarks-20260807T0000Z.json`
- Original URL: https://x.com/i/status/2085398373511918022
- Primary URLs:
  - https://developers.openai.com/codex/whats-new
  - https://developers.openai.com/plugins
  - https://developers.openai.com/codex/build-plugins
- Author: OpenAI Developers / @OpenAIDevs
- Posted: 2026-08-06T16:11:31.000Z
- Captured: 2026-08-07T00:00:48.104Z via xurl bookmarks capture
- Type: X post / official docs announcement
- Evidence strength: high; the X post and official OpenAI docs both describe Agent Plugins as a cross-client plugin surface with marketplace publishing
- Public metrics at capture: 5014 likes, 405 reposts, 227 replies, 242 quotes, 2891 bookmarks, 942068 impressions

## Summary
OpenAI Developers is positioning Agent Plugins as a shared plugin format that can be built once and used across compatible agent clients. The official docs reinforce that Codex now supports Agent Plugins manifests, workspace plugin publishing, and additional plugin marketplaces.

## Key Claims
- Agent Plugins aims to let one plugin work across compatible agent clients.
- The shared format packages Agent Skills and MCP server configurations.
- Codex now supports Agent Plugins manifests.
- OpenAI's plugin docs frame plugins as reusable skills and connections to external services.
- The docs also describe public and personal plugin distribution paths.

## Evidence / Examples
- The X post says to build a plugin once and use it across compatible agent clients.
- The OpenAI Codex changelog explicitly mentions support for Agent Plugins manifests, workspace plugin publishing, and additiona

## 更新された概念・地図

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

## NotebookLM Podcast用メモ

- まず今日の全体トレンドを話してから、重要ソースを3本に絞って深掘りする。
- ソース単体の紹介で終わらせず、既存KBの概念や地図がどう更新されたかを会話に含める。
- 最後に、明日以降の調査問いを2〜3個提示する。
