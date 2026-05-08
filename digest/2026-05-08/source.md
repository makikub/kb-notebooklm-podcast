<!-- generated: 2026-05-08T13:01:39.721671+00:00 -->
<!-- kb_daily_digest_date: 2026-05-08 -->
# KB Daily Digest Source — 2026-05-08

このページは、knowledge-base-llm の日次更新を NotebookLM に読み込ませるための公開向けソースページです。
Discord通知よりも文脈を厚めに残し、Podcast化しやすいように、今日追加・更新されたソース、概念、地図を文章中心で整理します。

## 今日の全体像

# KB Daily Digest — 2026-05-08

今日の `knowledge-base-llm` には、UTC 00時台のXブックマーク ingest と、UTC 12時台の安斎勇樹さん「冒険する組織のつくりかた」YouTubeソースが入りました。新規 raw は `raw/articles/` に7本、加えて `raw/x/bookmarks/20260508T000337Z-bookmarks.json`。新規 source note は `wiki/sources/` に7本で、`wiki/concepts/` では `exploratory-organization-lens` が追加され、`navigable-agent-skills`、`tool-accessibility`、`coding-agents`、`llm-inference-performance`、`model-psychology`、`organizational-intent-clarity` などが更新されています。

全体トレンドは、「AIエージェントを動かすための道具立て」がさらに広がったことです。OpenAI は Codex をChromeの中で動かし、OpenAI Realtime は音声会話の中で推論・中断・アクションを扱う方向に進み、AWS はMCPサーバー、skills、pluginsを束ねた公式ツールキットを提示しています。一方でGoogleの flash-lite は、高価な大モデルだけでなく、安価で大量に回せる軽量モデルをエージェントの部品として使う流れを補強しました。

重要ソース1本目は、AWS Agent Toolkit for AWS です。これは単なるSDK紹介というより、クラウドAPI群をエージェントが使える「技能パック」としてどう包装するかのシグナルです。KB上では `navigable-agent-skills` と `tool-accessibility` に接続され、ハーネス設計が「ツールを渡す」段階から、「巨大な操作面を、探索可能で安全なスキル集合として編成する」段階へ移っていることを示しています。

重要ソース2本目は、OpenAI の Codex Chrome plugin です。Codex がWebアプリをテストし、複数タブから文脈を集め、DevToolsを並行利用し、ブラウザを占有せずバックグラウンドで作業するという方向が記録されました。これは `coding-agents` と `tool-accessibility` にとって重要で、ブラウザが単なる人間用UIではなく、コーディングエージェントの実行・観察・検証面になるという変化を表しています。

重要ソース3本目は、安斎勇樹さんの「冒険する組織のつくりかた」です。技術ソースではありませんが、今日の更新の中ではKBの射程を大きく広げています。`exploratory-organization-lens` が新設され、AI導入を「命令と統制で高速化する」話だけでなく、問い、対話、学習、自己実現、組織を可能性の土壌として扱う視点から捉えるルートができました。これは `organizational-intent-clarity` や `sustainable-ai-work` と相性がよく、AI導入のJカーブや現場疲労の議論にもつながります。

その他のソースでは、Anthropic の Natural Language Autoencoders が `model-psychology` に、Claude内部状態を人間可読テキストへ翻訳する interpretability の方向を追加しました。OpenAI GPT-Realtime-2 はリアルタイム音声エージェントの操作面を、Anthropic Code with Claude workshop materials はモデル選択・技能分解・段階的検証の実践パターンを、Google AI Studio Gemini 3.1 flash-lite は低コスト・高スループットなサブタスク分担を補強しています。

今日のKB更新でいちばん面白いのは、ハーネスエンジニアリングの中心が「一つの強いモデルをどう使うか」から、「モデル、ブラウザ、音声、クラウドAPI、軽量モデル、スキル階層、組織学習をどう組み合わせるか」へ移っている点です。`harness-engineering-vendor-comparison` には May 2026 xurl bookmarks ingest として、OpenAI、Anthropic、Google、AWS、Anthropic workshops の位置づけが追記され、ベンダー比較の軸がより実装面に寄りました。

今後の追跡ポイントは3つです。第一に、AWSのような巨大API面をどこまで狭く型付きにし、どこから探索可能なスキルとして開くべきか。第二に、ブラウザや音声のような人間に近い操作面で、承認・ロールバック・監査ログをどう設計するか。第三に、AI導入を探索として扱う場合、曖昧な実験で終わらせず、仮説、評価、対話、意思決定記録へどう接続するかです。


## 重要ソース

### 安斎勇樹 — 冒険する組織のつくりかた by 安斎 勇樹

Source note: `wiki/sources/anzai-adventurous-organization-emconf-youtube.md`

# 安斎勇樹 — 冒険する組織のつくりかた by 安斎 勇樹

## Source Metadata
- Raw path: `raw/articles/anzai-adventurous-organization-emconf-youtube-2026-05-08.md`
- Original URL: https://youtu.be/64vD8W5mwwI?si=K47qFZv--ggG1twd
- Canonical URL: https://www.youtube.com/watch?v=64vD8W5mwwI
- Author / speaker: 安斎勇樹
- Channel: EMConf JP
- Published: 2026-03-17
- Type: YouTube talk / conference presentation
- Language: Japanese

## Short Summary
This source captures a YouTube talk titled `冒険する組織のつくりかた by 安斎 勇樹`. The transcript was visible as a YouTube panel but could not be retrieved in this environment, so this note treats the source as metadata plus official book-context rather than a full talk transcript.

The relevant idea for this KB is the contrast between a `軍事的世界観` and an `冒険的世界観` for organization building. In the official framing, manager exhaustion, executive loneliness, frontline suffocation, and hiring difficulty are symptoms of a worldview mismatch. The proposed shift is from command/control and people-as-tools toward inquiry, exploration, individual self-realization, and organization as a soil for possibility.

## Key Claims / Frames
- Organizations can inherit a military worldview: hierarchy, command, control, competition, and treating people as means.
- A more adaptive worldview treats teams as exploratory parties: diverse members, shared inquiry, curiosity, dialogue, and mutual growth.
- Organizational weakness can be diagnosed through lenses such as goals, teams, meetings/dialogue, growth, and organization.
- For AI adoption, this source is useful as a socio-technical frame: exploratory adoption requires learning-oriented goals and rituals, not only better tools or stricter execution.

## Evidence / Examples
- YouTube metadata confirms title, channel, provider, thumbnail, and publi

### AnthropicAI — Natural Language Autoencoders

Source note: `wiki/sources/anthropicai-natural-language-autoencoders-x.md`

# AnthropicAI — Natural Language Autoencoders

## Source Metadata
- Raw path: `raw/articles/anthropicai-natural-language-autoencoders-x-2026-05-07.md`
- Original URL: https://x.com/i/status/2052435436157452769
- Bookmark post id: 2052435436157452769
- Author: Anthropic / bookmark by AnthropicAI
- Date: 2026-05-07
- Type: X post
- Evidence strength: high for the post itself; medium if the note leans on a linked video/repo without full source capture
- Capture source: xurl bookmarks capture
- Primary URL: https://x.com/AnthropicAI/status/2052435436157452769/video/1

## Summary
Anthropic shares research showing that Claude activations can be translated into human-readable text. The post frames activations as numeric internal state that encodes thoughts even when the model speaks in words.

## Key Claims
- Claude-like models operate on activations that are not directly human-readable.
- Natural language autoencoders can translate those activations back into text.
- Interpretability can be treated as a learnable interface rather than only an analysis technique.

## Evidence / Examples
- The post itself is the durable provenance pointer from the bookmarks feed.

## Related Concepts
- [[../concepts/model-psychology.md]]
- [[../concepts/evidence-quality.md]]
- [[../concepts/behavioral-stability.md]]

## Related Maps
- [[../maps/evidence-quality-and-source-trust.md]]

## Open Questions
- Could activation-to-text translators become a practical audit surface for agent systems?
- How much of this transfers from research framing to production debugging?

## Backlinks
- [[../../raw/articles/anthropicai-natural-language-autoencoders-x-2026-05-07.md]]

### AWS — Agent Toolkit for AWS

Source note: `wiki/sources/aws-agent-toolkit-for-aws-x.md`

# AWS — Agent Toolkit for AWS

## Source Metadata
- Raw path: `raw/articles/aws-agent-toolkit-for-aws-x-2026-05-06.md`
- Original URL: https://x.com/i/status/2052115538701394205
- Bookmark post id: 2052115538701394205
- Author: Clare Liguori / bookmark by clare_liguori
- Date: 2026-05-06
- Type: X post
- Evidence strength: high for the post itself; medium if the note leans on a linked video/repo without full source capture
- Capture source: xurl bookmarks capture ; xurl read
- Primary URL: https://github.com/aws/agent-toolkit-for-aws
- Secondary URL: https://docs.aws.amazon.com/agent-toolkit/latest/userguide/quick-start.html

## Summary
AWS introduces an official agent toolkit with MCP servers, skills, and plugins for building on AWS. The post highlights broad API coverage, scripts, docs, and skill retrieval, with quick-start docs and a GitHub repo as the main entrypoints.

## Key Claims
- AWS is packaging agent access as skills, plugins, and remote MCP servers.
- The toolkit is designed to expose a very large AWS API surface to agents.
- The GitHub repo and quick-start docs are the practical source of truth.

## Evidence / Examples
- The post itself is the durable provenance pointer from the bookmarks feed.
- The quick-start docs and repo are the stronger practical source for implementation details.

## Related Concepts
- [[../concepts/navigable-agent-skills.md]]
- [[../concepts/tool-accessibility.md]]
- [[../concepts/coding-agents.md]]

## Related Maps
- [[../maps/harness-engineering-vendor-comparison.md]]
- [[../maps/coding-agent-harness-patterns.md]]

## Open Questions
- What parts of AWS access should remain typed and narrow even if the toolkit exposes everything?
- How should agent repos represent provider-specific skill packs without fragmenting the skill graph?


### Google AI Studio — Gemini 3.1 flash-lite

Source note: `wiki/sources/googleaistudio-gemini-3-1-flash-lite-x.md`

# Google AI Studio — Gemini 3.1 flash-lite

## Source Metadata
- Raw path: `raw/articles/googleaistudio-gemini-3-1-flash-lite-x-2026-05-07.md`
- Original URL: https://x.com/i/status/2052453828272812310
- Bookmark post id: 2052453828272812310
- Author: Google AI Studio / bookmark by GoogleAIStudio
- Date: 2026-05-07
- Type: X post
- Evidence strength: high for the post itself; medium if the note leans on a linked video/repo without full source capture
- Capture source: xurl bookmarks capture
- Primary URL: https://x.com/GoogleAIStudio/status/2052453828272812310/video/1

## Summary
Google AI Studio announces Gemini 3.1 flash-lite as a cost-efficient model aimed at high-volume agentic tasks, translation, and simple data processing.

## Key Claims
- flash-lite is positioned as a low-cost, high-throughput model.
- The target workload is agentic but relatively simple or repetitive.
- Translation and data processing are highlighted as fit cases.

## Evidence / Examples
- The post itself is the durable provenance pointer from the bookmarks feed.

## Related Concepts
- [[../concepts/llm-inference-performance.md]]
- [[../concepts/ai-roi-model.md]]
- [[../concepts/coding-agents.md]]

## Related Maps
- [[../maps/ai-adoption-roi-and-capability-investment.md]]

## Open Questions
- Where is the cost/performance break-even for using a lighter model in agent loops?
- Which agent subtasks should be routed to small models by default?

## Backlinks
- [[../../raw/articles/googleaistudio-gemini-3-1-flash-lite-x-2026-05-07.md]]

### ぬこぬこ / NUKO — Code with Claude workshop materials

Source note: `wiki/sources/nukonuko-code-with-claude-workshops-x.md`

# ぬこぬこ / NUKO — Code with Claude workshop materials

## Source Metadata
- Raw path: `raw/articles/nukonuko-code-with-claude-workshops-x-2026-05-06.md`
- Original URL: https://x.com/i/status/2052078242358841432
- Bookmark post id: 2052078242358841432
- Author: ぬこぬこ / NUKO 🇯🇵 / bookmark by nukonuko
- Date: 2026-05-06
- Type: X post
- Evidence strength: high for the post itself; medium if the note leans on a linked video/repo without full source capture
- Capture source: xurl bookmarks capture ; xurl read
- Primary URL: https://github.com/anthropics/cwc-workshops

## Summary
A workshop-repo share for Anthropic’s Code with Claude materials. The post calls out rightmodel-style model sweep selection and agent-decomposition into skills plus code execution with stepwise validation.

## Key Claims
- Workshop materials expose practical agent workflow design patterns.
- One pattern is searching model/prompt settings for the best cost/latency mix.
- Another is decomposing a prompt inventory into skill and execution steps with validation.

## Evidence / Examples
- The post itself is the durable provenance pointer from the bookmarks feed.
- The linked repository is the practical primary source.

## Related Concepts
- [[../concepts/coding-agents.md]]
- [[../concepts/tool-accessibility.md]]
- [[../concepts/navigable-agent-skills.md]]

## Related Maps
- [[../maps/coding-agent-harness-patterns.md]]

## Open Questions
- How much of workshop guidance should become repo-level defaults versus optional playbooks?
- Can these patterns be turned into reusable harness primitives rather than slideware?

## Backlinks
- [[../../raw/articles/nukonuko-code-with-claude-workshops-x-2026-05-06.md]]

### OpenAI — Codex browser work in Chrome

Source note: `wiki/sources/openai-codex-chrome-plugin-x.md`

# OpenAI — Codex browser work in Chrome

## Source Metadata
- Raw path: `raw/articles/openai-codex-chrome-plugin-x-2026-05-07.md`
- Original URL: https://x.com/i/status/2052480800004956323
- Bookmark post id: 2052480800004956323
- Author: OpenAI / bookmark by OpenAI
- Date: 2026-05-07
- Type: X post
- Evidence strength: high for the post itself; medium if the note leans on a linked video/repo without full source capture
- Capture source: xurl bookmarks capture
- Primary URL: https://x.com/OpenAI/status/2052480800004956323/video/1

## Summary
OpenAI says Codex can now work directly in Chrome, testing web apps, gathering context across tabs, using DevTools in parallel, and staying in the background instead of taking over the browser.

## Key Claims
- Codex now has a browser-native workflow in Chrome.
- Parallel tab-level work and DevTools access are part of the workflow.
- The browser plugin keeps the agent in the background rather than foregrounding the whole session.

## Evidence / Examples
- The post itself is the durable provenance pointer from the bookmarks feed.

## Related Concepts
- [[../concepts/coding-agents.md]]
- [[../concepts/tool-accessibility.md]]
- [[../concepts/background-agents.md]]

## Related Maps
- [[../maps/coding-agent-harness-patterns.md]]

## Open Questions
- How much browser automation should live inside the coding agent versus a separate harness?
- What review and rollback surfaces are needed when the browser becomes part of the coding loop?

## Backlinks
- [[../../raw/articles/openai-codex-chrome-plugin-x-2026-05-07.md]]

### OpenAI — GPT-Realtime-2 in the API

Source note: `wiki/sources/openai-gpt-realtime-2-api-x.md`

# OpenAI — GPT-Realtime-2 in the API

## Source Metadata
- Raw path: `raw/articles/openai-gpt-realtime-2-api-x-2026-05-07.md`
- Original URL: https://x.com/i/status/2052438194625593804
- Bookmark post id: 2052438194625593804
- Author: OpenAI / bookmark by OpenAI
- Date: 2026-05-07
- Type: X post
- Evidence strength: high for the post itself; medium if the note leans on a linked video/repo without full source capture
- Capture source: xurl bookmarks capture
- Primary URL: https://x.com/OpenAI/status/2052438194625593804/video/1

## Summary
OpenAI announces GPT-Realtime-2 for voice agents, positioning it as a production-ready API model that can listen, reason, take action, and handle interruptions in real time.

## Key Claims
- The API now supports a stronger realtime voice model for voice agents.
- The model is pitched as capable of reasoning while conversations unfold.
- Interruptions and action-taking are part of the intended interaction model.

## Evidence / Examples
- The post itself is the durable provenance pointer from the bookmarks feed.

## Related Concepts
- [[../concepts/tool-accessibility.md]]
- [[../concepts/agent-management.md]]
- [[../concepts/long-running-agents.md]]

## Related Maps
- [[../maps/agent-deployment-gates-and-operational-risk.md]]

## Open Questions
- What approval and fallback design does realtime voice need before it is safe for high-stakes use?
- How much of the agent loop moves into the speech layer when voice becomes the primary interface?

## Backlinks
- [[../../raw/articles/openai-gpt-realtime-2-api-x-2026-05-07.md]]

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
- [Instability Tax](instability-tax.md)
- [LLM In

### Exploratory Organization Lens

KB note: `wiki/concepts/exploratory-organization-lens.md`

---
aliases:
  - Exploratory organization lens
  - 冒険的世界観
  - Adventurous organization lens
---

# Exploratory Organization Lens

## Definition
A way to view organization design as exploration rather than command execution: goals become inquiry prompts, teams become diverse parties, meetings become dialogue spaces, growth becomes identity exploration, and the organization becomes soil for people and capabilities to develop.

## Why It Matters
AI adoption often fails when organizations expect new tools to simply execute pre-existing commands faster. In uncertain workflows, teams are still discovering what good looks like, which constraints matter, and how humans and agents should divide work. An exploratory organization lens makes learning, dialogue, and evolving intent first-class parts of adoption.

## Relation to Agent / AI Work
- Complements [[organizational-intent-clarity.md]]: clear intent does not always mean fixed orders; sometimes the clearer artifact is a shared question, hypo

### Organizational Intent Clarity

KB note: `wiki/concepts/organizational-intent-clarity.md`

---
aliases:
  - Organizational intent clarity
  - Goal clarity for AI adoption
---

# Organizational Intent Clarity

## Definition
The degree to which a team can state stable goals, desired outcomes, constraints, and evaluation criteria clearly enough for humans and agents to act on them.

## Why It Matters
When intent is vague or constantly shifting, AI systems look unreliable even when the underlying model is capable. The practical bottleneck moves from “can the model do it?” to “has the organization expressed what should be done, why, and how success will be judged?”

## Related Concepts
- [[context-engineering.md]]
- [[exploratory-organization-lens.md]]
- [[company-brain.md]]
- [[product-responsibility-distribution.md]]
- [[agent-management.md]]
- [[evidence-quality.md]]

## Supporting Sources
- [[../sources/iwashi86-organizational-ai-use-goal-clarity-x.md]]
- [[../sources/anzai-adventurous-organization-emconf-youtube.md]]
- [[../sources/recerqa-pdm-abolished-speakerdeck.md]]
- [[

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

### Model Psychology

KB note: `wiki/concepts/model-psychology.md`

---
aliases:
  - Model Psychology
---

# Model Psychology

## Definition
A framing that treats recurring internal states, styles, or behavioral tendencies in language models as psychologically relevant to how the system acts.

## Why It Matters
If agent behavior depends partly on latent internal dynamics, then external tool policy alone may not fully explain system behavior. This matters most in the current KB when trying to separate failures caused by weak harness design from failures caused by model tendencies that the harness must anticipate.

## Related Concepts
- [[behavioral stability]]
- [[agent safety]]
- [[failure modes]]

## Supporting Sources
- [[../sources/anthropic-emotion-concepts.md]]
- [[../sources/anthropic-harness-design-long-running-apps.md]]
- [[../sources/anthropicai-natural-language-autoencoders-x.md]]

## Tradeoffs / Tensions
- Psychological language can clarify behavior, but may also anthropomorphize too aggressively.
- Interpretability findings may not map clea

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
- [[../sources/nukonuko-code-with-claude-worksh

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
