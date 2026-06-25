<!-- generated: 2026-06-25T13:01:47.409737+00:00 -->
<!-- kb_daily_digest_date: 2026-06-25 -->
# KB Daily Digest Source — 2026-06-25

このページは、knowledge-base-llm の日次更新を NotebookLM に読み込ませるための公開向けソースページです。
Discord通知よりも文脈を厚めに残し、Podcast化しやすいように、今日追加・更新されたソース、概念、地図を文章中心で整理します。

## 今日の全体像

# KB Daily Digest 2026-06-25

2026-06-25 UTC の knowledge-base-llm は、X bookmarks の新規取り込みを起点に、coding agent / design agent / secrets management の3本を source note として追加した更新だった。新規 raw は `raw/x/bookmarks/bookmarks-20260625T0000Z.json` と、そこから切り出された記事メモ3本。wiki 側では Devin Desktop/CLI のモデル提供、Figma Config 2026 の generative plugins、1Password Environments による `.env` 管理が sources に追加され、`harness-engineering`、`coding-agents`、`workflow-compilation`、`context-engineering`、`environment-bootstrapping`、`tool-accessibility` などの既存概念に接続された。

全体トレンドは、「AI機能を単体ツールとして足す」段階から、「日常の作業面にモデル・スキル・秘密情報の扱いを埋め込む」段階への移行として読める。Devin は Kimi K2.7 Code と GLM 5.2 を Desktop/CLI の選択肢として出し、Figma は generative plugin と design agent の custom tools / context / skills を前面に出し、1Password Environments は `.env` を平文ファイルやチャット共有ではなく、権限付きの実行時注入として扱う。いずれも、モデルやプロンプトだけではなく、作業環境そのものが agent-ready に整備されていく流れを補強している。

重要ソースの1本目は Devin Desktop / CLI のモデル提供に関する投稿。KB内では `coding-agents`、`llm-inference-performance`、`tool-accessibility`、`agentic-jevons-paradox` に接続されている。ポイントは、Kimi K2.7 Code と GLM 5.2 のようなモデルが、単なるリリース情報ではなく、Desktop と CLI という実作業面に組み込まれていること。FrontierCode Extended のスコアも提示されているが、KB上の扱いとしてはベンチマーク値そのものより、「どのモデルをどの作業面で使えるようにするか」が product UX の判断になっている点が重要になる。

2本目は Figma Config 2026 の generative plugins と design-agent tools。ここでは、Figma が受動的なキャンバスから、生成・拡張・文脈理解を備えた作業面へ寄っていることが読みどころになる。source note は `navigable-agent-skills`、`workflow-compilation`、`rich-agent-output-artifact`、`context-engineering` に接続されており、デザイン作業を「一回限りの生成」ではなく、再利用できる tool / skill / plugin として編成する方向を示す。特に「custom tools」「real context」「skills」という語彙は、KBが追っている agent skill substrate の設計論と相性がよい。

3本目は Takahiro Ikeuchi 氏の 1Password Environments 記事。これは `.env` を Slack DM などで共有する運用を避け、1Password 側で環境変数を管理し、`op environment read` や `op run --environment` で必要時に注入する実務パターンとして追加された。KBでは `environment-bootstrapping`、`context-file-system`、`approval-policy`、`sustainable-ai-work` に効いている。agent がリポジトリや開発環境を扱うほど、秘密情報をどこに置くか、いつ読み込むか、どの承認境界で使うかが品質と安全性の一部になる。

今日の概念地図としては、3本すべてが `tool-accessibility` に接続されている点が目立つ。Devin のモデル選択、Figma の生成プラグイン、1Password のCLI注入は、表面上は別ジャンルだが、どれも「正しい能力を、作業者やagentが使える場所に置く」話である。KB全体の harness engineering 観点では、ツールを増やすこと自体ではなく、選択・権限・文脈・出力物の扱いまで含めて、作業ループにどう編み込むかが焦点になる。

実務上の読みどころは、agent時代のチーム環境を「モデル」「作業キャンバス」「秘密情報」の3層で点検できることだと思う。まず、coding agent で使えるモデルは誰が選び、どう比較し、いつ切り替えるのか。次に、デザインやドキュメントの作業面は、単なるチャット応答ではなく、再実行可能なスキルやプラグインとして残せるのか。最後に、そうした agent が開発環境へ入るとき、`.env` やトークンを生のファイルとして置かず、安全に注入できるのか。この3つが揃うと、agent導入はデモから日常運用に近づく。

公開ページとPodcastでは、「モデル可用性はベンダー発表ではなくUX設計である」「design agent の skill 化は workflow compilation の別表現である」「秘密情報管理はagent harnessの土台である」という3点を掘るとよい。次に追う問いは、1) coding agent が複数モデルを自律的に選ぶときの評価基準、2) Figmaのgenerative pluginがどこまで再利用可能なskillとして扱えるか、3) 1Password Environments のような実行時注入が unattended automation にどこまで向くか、4) tool accessibility と approval boundary を同じ設計図で扱えるか、の4つ。


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

### Cognition - Devin Desktop and CLI model availability

Source note: `wiki/sources/cognition-devin-model-availability-kimi-glm-x-2026-06-24.md`

# Cognition - Devin Desktop and CLI model availability

## Source Metadata
- Raw path: `raw/articles/cognition-devin-model-availability-kimi-glm-x-2026-06-24.md`
- Original URL: https://x.com/i/status/2069918091245699456
- Bookmark source: xurl bookmarks capture
- Canonical URL: https://x.com/i/status/2069918091245699456
- Primary URL: https://x.com/devindesktop/status/2069918091245699456/photo/1
- Author: Devin Desktop / @devindesktop
- Posted: 2026-06-24T22:58:24.000Z
- Captured: 2026-06-25 via xurl bookmarks capture
- Public metrics at capture: 10 reposts, 6 replies, 79 likes, 12 quotes, 15 bookmarks, 13254 impressions

## Summary
This bookmarked post is a small but useful product-distribution signal: Devin Desktop and CLI surfaced Kimi K2.7 Code and GLM 5.2 directly to users, along with benchmark numbers on FrontierCode Extended and a limited free-try window.

## Key Claims
- Devin Desktop and CLI are serving Kimi K2.7 Code and GLM 5.2 as selectable models.
- The post uses FrontierCode Extended scores to position the models for real-world engineering tasks.
- The rollout is temporarily free for Pro, Max, and Teams users until July 5.
- Model availability is becoming a product-surface decision, not just a model-release decision.

## Evidence / Examples
- The bookmark text explicitly names both models and both Devin surfaces.
- It reports FrontierCode Extended scores of 43.0% for GLM 5.2 and 39.5% for Kimi K2.7 Code.
- The post says users can try both models for free until July 5.

## Evidence Quality
- Source type: X post / image card
- Confidence: medium-high for the rollout claim, medium for benchmark interpretation because the benchmark details are only lightly surfaced
- Supports: model availability, product integration, and benchmark-driven model selection
- Mai

### Figma - Config 2026 generative plugins and design-agent tools

Source note: `wiki/sources/figma-config-2026-generative-plugins-x-2026-06-24.md`

# Figma - Config 2026 generative plugins and design-agent tools

## Source Metadata
- Raw path: `raw/articles/figma-config-2026-generative-plugins-x-2026-06-24.md`
- Original URL: https://www.figma.com/blog/config/
- Bookmark source: xurl bookmarks capture
- Canonical URL: https://x.com/i/status/2069824816279154840
- Primary URL: https://www.figma.com/blog/config/
- Related primary URL: https://www.figma.com/blog/the-figma-agent-is-here/
- Author: Figma / @figma
- Posted: 2026-06-24T16:47:46.000Z
- Captured: 2026-06-25 via xurl bookmarks capture
- Public metrics at capture: 100 reposts, 26 replies, 1073 likes, 47 quotes, 273 bookmarks, 58073 impressions

## Summary
This source packages Figma's Config 2026 announcements as an increasingly agent-shaped design surface. The bookmark text points at generative plugins, and Figma's own product pages add that the design agent now has custom tools, more context, and skills.

## Key Claims
- Figma is moving beyond passive design surfaces toward generative, programmable canvas tooling.
- Generative plugins are part of the Config 2026 launch set.
- The design agent is being extended with custom tools, real context, and skills.
- The result is a design workflow where users can describe a tool or behavior and get a more tailored canvas output.

## Evidence / Examples
- The bookmark text says, "Generative plugins, built by you and the Figma agent."
- The Config 2026 blog teaser explicitly lists generative plugins among the new materials/tools.
- The design-agent blog teaser says custom tools, real context, and skills take the design agent further.

## Evidence Quality
- Source type: X post / video card plus official product blog previews
- Confidence: medium-high for the product direction, medium for implementation details because the

### Takahiro Ikeuchi - 1Password Environments for secure .env handling

Source note: `wiki/sources/iktakahiro-1password-environments-secure-env-2026-06-23.md`

# Takahiro Ikeuchi - 1Password Environments for secure .env handling

## Source Metadata
- Raw path: `raw/articles/iktakahiro-1password-environments-secure-env-2026-06-23.md`
- Original URL: https://zenn.dev/iktakahiro/articles/cc0692b8673184
- Bookmark source: xurl bookmarks capture
- Canonical URL: https://x.com/i/status/2069418304960364774
- Primary URL: https://zenn.dev/iktakahiro/articles/cc0692b8673184
- Author: Takahiro Ikeuchi / @iktakahiro
- Posted: 2026-06-23T13:52:26.000Z
- Captured: 2026-06-25 via xurl bookmarks capture
- Public metrics at capture: 3 reposts, 0 replies, 38 likes, 0 quotes, 41 bookmarks, 3788 impressions

## Summary
This source argues that `.env` files are better treated as managed environment data than as ad hoc text blobs shared through chat. The article recommends 1Password Environments as a secure way to store project variables, then load them into commands with `op environment read` or `op run --environment`.

## Key Claims
- Sharing `.env` contents over Slack is a security risk and an operational smell.
- 1Password Environments gives teams a centralized way to manage project environment variables.
- The CLI workflow lets developers inject environment variables at runtime without placing a plaintext `.env` file on disk.
- The feature was still beta at the time of writing, so operational details may change.

## Evidence / Examples
- The article describes environment-variable import/export, environment scoping, and per-environment access control.
- It shows `op environment read <<Environment-ID>>` for inspection.
- It shows `op run --environment <<Environment-ID>> -- pnpm run dev` as the basic runtime pattern.
- It explicitly warns against sending `.env` contents in Slack DMs.

## Evidence Quality
- Source type: practitioner blog post prom

## 更新された概念・地図

## NotebookLM Podcast用メモ

- まず今日の全体トレンドを話してから、重要ソースを3本に絞って深掘りする。
- ソース単体の紹介で終わらせず、既存KBの概念や地図がどう更新されたかを会話に含める。
- 最後に、明日以降の調査問いを2〜3個提示する。
