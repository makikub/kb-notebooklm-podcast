<!-- generated: 2026-07-31T13:02:20.129389+00:00 -->
<!-- kb_daily_digest_date: 2026-07-31 -->
# KB Daily Digest Source — 2026-07-31

このページは、knowledge-base-llm の日次更新を NotebookLM に読み込ませるための公開向けソースページです。
Discord通知よりも文脈を厚めに残し、Podcast化しやすいように、今日追加・更新されたソース、概念、地図を文章中心で整理します。

## 今日の全体像

# KB Daily Digest 2026-07-31

2026-07-31 UTC の knowledge-base-llm 更新は、`raw/x/bookmarks/bookmarks-20260731T0000Z.json` を入口に、Cognition / Devin と GitHub stacked pull requests を中心にした4本の source note が追加された日でした。追加された raw / wiki source は、Devin Cloud Agents の macOS/Xcode/iOS simulator 対応、Devin の GitHub stacked PR 対応、GitHub 自体の stacked pull requests public preview、Namespace と Cognition の devbox 連携です。X post 由来が多いため evidence strength は medium が中心ですが、GitHub Changelog への primary URL を持つ stacked PR preview は、機能公開の存在確認としては強めの根拠です。

今日の全体トレンドは、「coding agent の価値がエディタ内のコード生成から、実行環境、レビュー単位、ブランチ構造、クラウド devbox まで広がっている」ことです。Devin が macOS を持つ、Xcode と iOS simulator を動かす、 signing setup まで含める、という話は、モバイル開発のような環境依存の強い作業を agent harness の内側へ入れる動きです。一方、stacked PR は、大きな変更を小さな差分列に分解し、順序・依存・ downstream rebase を扱う review topology の話です。つまり今日の更新は、実行面とレビュー面の両方で「agent が動く土台そのもの」が製品化されているシグナルとして読めます。

重要ソース1本目は Cognition / Devin の macOS 対応デモです。投稿は「iOS apps cannot be built without a Mac」という制約を起点に、Devin Cloud Agents が real macOS environment 上で Xcode、iOS simulator、signing setup、full computer use を扱えるようになったと説明しています。KB上では、これは単なるリモート実行ではなく、artifact-native mobile development loop の証拠として扱えます。コードを書く agent が、ビルド対象の実機に近い環境、シミュレータ、署名設定、実行結果の観察まで同じ環境に持つと、テストとレビューの粒度が変わります。

重要ソース2本目は GitHub Changelog の stacked pull requests public preview です。stacked PR は、大きな変更を互いに積み重なる小さな PR に分解し、個別にもまとめても review / merge できるという変更管理の機能です。これは agentic coding にとってかなり重要です。agent は大きな変更を一気に出すほどレビュー負荷を上げがちですが、stack を work unit にできるなら、分解、依存、コメント修正、downstream rebase、merge order を明示的に扱えるようになります。KBの `eval-review-reliability` と `coding-agent-harness-patterns` にとって、review surface が単一PRから stack へ拡張する意味は大きいです。

重要ソース3本目は Devin の GitHub stacked PR native support です。Cognition の投稿は、Devin が large changes を smaller, reviewable diffs に分解し、stack across comments を直し、downstream changes を自動 rebase できると述べています。GitHub 側が stacked PR を public preview として出し、同日に Devin 側が native support を出しているため、これは人間の review workflow と agent の execution workflow が同じ構造へ寄っていく例です。stacked PR は人間レビューの便利機能に見えますが、agent harness の観点では、変更分解とレビュー応答を機械が扱いやすい単位へ変える interface でもあります。

Namespace の devbox update は、Cognition との連携により Devin が Apple Silicon の macOS Devboxes と Linux にアクセスできるというインフラ側の補助線です。これにより、Devin の macOS 対応は単独機能というより、cloud devbox vendor と agent product の境界が結びつく流れとして見えてきます。agent が「どこで実行されるか」は、権限、監査、再現性、warm pool、snapshot、ビルド性能、OS固有ツールの可用性を左右します。KBの `harness-engineering-vendor-comparison` では、Cognition / Devin の軸に macOS/Xcode execution、stacked PR support、devbox-environment partnerships が加わりました。

KB地図の更新としては、`agent-harness-landscape` に Cognition / Devin と GitHub stacked PR の項目が明示的に足され、cloud-agent runtime が generic ではなく environment-specific になっている点が整理されました。`coding-agent-harness-patterns` では、risk-routed AI review の近くに stacked PR が review unit として追加され、さらに embedded runtime review surface として iOS simulator panel 的な読み方が補強されています。`eval-review-reliability` では、single-diff inspection だけではなく、artifact-native、stack-aware workflow へ review reliability が移動しているという見方が入りました。

実務上の読みどころは、agent 導入のボトルネックが「モデルに何を指示するか」だけではなくなっていることです。iOS のような環境依存タスクでは、agent が正しい shell command を知っていても、macOS、Xcode、simulator、signing、UI inspection が揃わなければ閉じたループになりません。大きな変更のレビューでは、agent がコードを書けても、差分が大きすぎたり、レビューコメント修正が downstream branch に波及したりすると、人間の負荷が跳ね上がります。今日の4本は、その2つの詰まりをそれぞれ runtime substrate と review topology で解こうとしているように見えます。

Podcastで掘るなら、第一に「cloud coding agent はもはやリモートCLIではなく、OS・デバイス・シミュレータ・署名・レビューUIを含む実行面そのものになっている」という話が中心になります。第二に「stacked PR は人間のための整理術であると同時に、agent が大きな変更を扱うための制御構造でもある」という論点があります。第三に「GitHub のレビュー構造と Devin の agent workflow が同じ日に同じ方向へ動いたことは、プラットフォームと agent vendor の境界が近づいている兆候かもしれない」という読み方もできます。

次に追うべき問いは3つあります。まず、Devin の macOS/Xcode 環境で、署名情報、Apple Developer account、秘密情報、監査ログがどのように扱われるのか。次に、GitHub stacked PR preview が一般化したとき、AI review、auto-merge、risk routing、downstream rebase の失敗検知はどのレイヤーで設計されるのか。最後に、Namespace のような devbox provider と agent vendor の組み合わせが進むと、企業は coding agent を「ツール」として買うのか、それとも「管理された実行環境」として買うのか、という調達・ガバナンス上の問いです。

## Important Sources

- `https://x.com/i/status/2082868506576519560`
- `https://github.blog/changelog/2026-07-30-stacked-pull-requests-are-now-in-public-preview`
- `https://x.com/i/status/2082870779775959249`
- `https://x.com/i/status/2082890935617171677`

## New / Changed Files

- `raw/x/bookmarks/bookmarks-20260731T0000Z.json`
- `raw/articles/cognition-devin-cloud-agents-macos-xcode-ios-simulator-x-2026-07-30.md`
- `raw/articles/cognition-devin-github-stacked-prs-x-2026-07-30.md`
- `raw/articles/ghchangelog-stacked-pull-requests-public-preview-github-x-2026-07-30.md`
- `raw/articles/namespacelabs-devboxes-cognition-macos-linux-x-2026-07-30.md`
- `wiki/sources/cognition-devin-cloud-agents-macos-xcode-ios-simulator-x-2026-07-30.md`
- `wiki/sources/cognition-devin-github-stacked-prs-x-2026-07-30.md`
- `wiki/sources/ghchangelog-stacked-pull-requests-public-preview-github-x-2026-07-30.md`
- `wiki/sources/namespacelabs-devboxes-cognition-macos-linux-x-2026-07-30.md`
- `wiki/INDEX.md`
- `wiki/maps/agent-harness-landscape.md`
- `wiki/maps/coding-agent-harness-patterns.md`
- `wiki/maps/eval-review-reliability.md`
- `wiki/maps/harness-engineering-vendor-comparison.md`


## 重要ソース

### Cognition - Devin Cloud Agents on macOS

Source note: `wiki/sources/cognition-devin-cloud-agents-macos-xcode-ios-simulator-x-2026-07-30.md`

# Cognition - Devin Cloud Agents on macOS

## Source Metadata
- Raw path: `../../raw/articles/cognition-devin-cloud-agents-macos-xcode-ios-simulator-x-2026-07-30.md`
- Raw bookmark capture: `../../raw/x/bookmarks/bookmarks-20260731T0000Z.json`
- Original URL: https://x.com/i/status/2082868506576519560
- Author: nader dabit (@dabit3)
- Posted: 2026-07-30T16:38:44.000Z
- Captured: 2026-07-31T00:00:18.198Z via xurl bookmarks capture
- Type: X post / video card
- Evidence strength: medium; the post is a demo clip rather than a full spec or docs page
- Public metrics at capture: 509 likes, 31 reposts, 54 replies, 16 quotes, 254 bookmarks, 104506 impressions

## Summary
The post claims Devin Cloud Agents can now run macOS with Xcode, the iOS simulator, and signing setup available in the same environment, and that a demo used this to build and test a native iOS game. The main KB signal is that mobile app work is becoming executable inside a remote agent environment with the relevant platform tools already in place.

## Key Claims
- Devin Cloud Agents can run on macOS.
- Xcode and the iOS simulator are available inside that environment.
- Signing setup is part of the surfaced workflow.
- The environment is usable for both building and testing a native iOS app.

## Evidence / Examples
- The post explicitly names macOS, Xcode, the iOS simulator, and signing setup.
- It says the demo builds a native iOS game and then plays/tests it.
- The clip therefore combines compile, run, and verification in one agent workspace.

## Evidence Quality
- Source type: X post / demo video
- Confidence: medium-high for the feature direction, medium for implementation details
- Supports: managed-agents, long-running-agents, human-in-the-loop, self-verification
- Main limitations: no docs page or repr

### Cognition - Devin now supports GitHub stacked PRs

Source note: `wiki/sources/cognition-devin-github-stacked-prs-x-2026-07-30.md`

# Cognition - Devin now supports GitHub stacked PRs

## Source Metadata
- Raw path: `../../raw/articles/cognition-devin-github-stacked-prs-x-2026-07-30.md`
- Raw bookmark capture: `../../raw/x/bookmarks/bookmarks-20260731T0000Z.json`
- Original URL: https://x.com/i/status/2082870779775959249
- Author: Cognition (@cognition)
- Posted: 2026-07-30T16:47:46.000Z
- Captured: 2026-07-31T00:00:18.198Z via xurl bookmarks capture
- Type: X post / video card
- Evidence strength: medium; the post is a demo signal without a linked primary source
- Public metrics at capture: 333 likes, 34 reposts, 28 replies, 39 quotes, 54 bookmarks, 67191 impressions

## Summary
Cognition says Devin natively supports GitHub stacked PRs, including breaking work into smaller diffs, fixing comments across the stack, and automatically rebasing downstream changes. This is a useful KB signal because it connects agent workflows to a more explicit review topology.

## Key Claims
- Devin can work with GitHub stacked PRs natively.
- Stacked PRs let the agent break work into smaller, reviewable diffs.
- Devin can address comments across the stack and rebase downstream changes automatically.

## Evidence / Examples
- The post explicitly lists the three capabilities.
- It sits alongside GitHub's own public-preview announcement for stacked pull requests.

## Evidence Quality
- Source type: X post / demo video
- Confidence: medium
- Supports: self-verification, human-in-the-loop, feedback-controls, task-decomposition
- Main limitations: no docs page or reproducible implementation notes were captured
- Best use: evidence that agent products are adapting to stacked-review workflows

## Related Concepts
- [[../concepts/self-verification.md]]
- [[../concepts/human-in-the-loop.md]]
- [[../concepts/feedback-controls.md

### GitHub Changelog - Stacked pull requests public preview

Source note: `wiki/sources/ghchangelog-stacked-pull-requests-public-preview-github-x-2026-07-30.md`

# GitHub Changelog - Stacked pull requests public preview

## Source Metadata
- Raw path: `../../raw/articles/ghchangelog-stacked-pull-requests-public-preview-github-x-2026-07-30.md`
- Raw bookmark capture: `../../raw/x/bookmarks/bookmarks-20260731T0000Z.json`
- Original URL: https://x.com/i/status/2082870109912072588
- Primary URL: https://github.blog/changelog/2026-07-30-stacked-pull-requests-are-now-in-public-preview
- Author: GitHub Changelog (@GHchangelog)
- Posted: 2026-07-30T16:45:06.000Z
- Captured: 2026-07-31T00:00:18.198Z via xurl bookmarks capture
- Type: X post pointing to GitHub Changelog
- Evidence strength: high for the feature preview and primary announcement
- Public metrics at capture: 51 likes, 14 reposts, 0 replies, 4 quotes, 16 bookmarks, 3614 impressions

## Summary
GitHub's stacked pull request preview makes large changes easier to split into ordered, reviewable layers. That matters to the KB because it turns "review" from a single merge gate into a structured workflow for building, fixing, and merging change stacks.

## Key Claims
- Stacked pull requests let large work be split into smaller ordered diffs.
- Reviewers can work through the stack independently or merge the whole stack together.
- The feature is now in public preview.

## Evidence / Examples
- The bookmark text explicitly describes reviewable PRs that build on each other in order.
- The linked GitHub changelog entry is the primary source for the feature preview.

## Evidence Quality
- Source type: X bookmark plus GitHub changelog
- Confidence: high
- Supports: self-verification, human-in-the-loop, feedback-controls, task-decomposition
- Main limitations: public preview status means the UX and rollout details may still change
- Best use: a concrete review-structure example for coding-

### Namespace - Devbox update with Cognition

Source note: `wiki/sources/namespacelabs-devboxes-cognition-macos-linux-x-2026-07-30.md`

# Namespace - Devbox update with Cognition

## Source Metadata
- Raw path: `../../raw/articles/namespacelabs-devboxes-cognition-macos-linux-x-2026-07-30.md`
- Raw bookmark capture: `../../raw/x/bookmarks/bookmarks-20260731T0000Z.json`
- Original URL: https://x.com/i/status/2082890935617171677
- Author: Namespace (@namespacelabs)
- Posted: 2026-07-30T18:07:51.000Z
- Captured: 2026-07-31T00:00:18.198Z via xurl bookmarks capture
- Type: X post / product update
- Evidence strength: medium; the post is mostly a summary update with one visible media card
- Public metrics at capture: 6 likes, 0 reposts, 0 replies, 0 quotes, 4 bookmarks, 438 impressions

## Summary
Namespace says it has partnered with Cognition so Devin can use macOS Devboxes with Apple Silicon as well as Linux. The signal is less about the marketing copy and more about the deployment surface: cloud-agent workflows are now being packaged around specific devbox environments rather than only generic remote compute.

## Key Claims
- Namespace is shipping new devbox-related improvements.
- Cognition / Devin can access macOS Devboxes with Apple Silicon and Linux.
- The devbox is positioned as a usable surface for the agent, not just a general-purpose machine image.

## Evidence / Examples
- The post explicitly names a partnership with Cognition.
- It explicitly mentions macOS Devboxes with Apple Silicon and Linux.
- The visible card suggests the update is product-facing, not merely internal infrastructure.

## Evidence Quality
- Source type: X post / product update
- Confidence: medium for the surface claim, low for any deeper operational details
- Supports: managed-agents, agent-management, tool-accessibility, harness-engineering
- Main limitations: no engineering docs or benchmarks were captured
- Best use: eviden

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



### Eval and Review Reliability

KB note: `wiki/maps/eval-review-reliability.md`

# Eval and Review Reliability

## Purpose
Collect the KB's evaluation and review ideas into one map focused on practical reliability: how to know whether an agent-produced artifact is good enough, and how to keep review load from becoming the bottleneck.

## Core thesis
Agent output quality improves when evaluation is treated as a separate harness layer, not as an informal final glance by the same agent that produced the work.

## Reliability layers

### 1. Deterministic checks first
Use cheap checks before semantic review:
- lint and typecheck
- tests and smoke tests
- formatting and structural checks
- repository-specific machine-checkable invariants

Related concepts: [[../concepts/machine-checkable-invariants.md]], [[../concepts/feedback-controls.md]].

### 2. Task-fit review
Check whether the work actually satisfies the request:
- requirements coverage
- edge cases
- backward compatibility
- user-facing behavior
- maintainability

Related maps: [[coding-agent-review-rubric.md]], [

### Harness Engineering Vendor / Practitioner Comparison

KB note: `wiki/maps/harness-engineering-vendor-comparison.md`

# Harness Engineering Vendor / Practitioner Comparison

## Purpose
Compare how different sources frame harness engineering, what they optimize for, and what distinctive mechanisms they emphasize.

## Source anchors
- [[../sources/openai-harness-engineering.md]]
- [[../sources/openai-codex-plugin-cc-github.md]]
- [[../sources/codex-subagents-docs.md]]
- [[../sources/anthropic-effective-harnesses-long-running-agents.md]]
- [[../sources/anthropic-harness-design-long-running-apps.md]]
- [[../sources/anthropic-claude-code-on-the-web-docs.md]]
- [[../sources/anthropic-claude-code-skills-docs.md]]
- [[../sources/anthropic-claude-code-web-scheduled-tasks-docs.md]]
- [[../sources/cursor-3-blog.md]]
- [[../sources/anthropic-claude-code-large-codebases.md]]
- [[../sources/anthropic-2026-agentic-coding-trends-report.md]]
- [[../sources/gargetisha-openclaw-under-the-hood-x-article.md]]

## Comparison axes

### OpenAI
- Focus: repository design, machine-enforced invariants, agent-recognizable contex

## NotebookLM Podcast用メモ

- まず今日の全体トレンドを話してから、重要ソースを3本に絞って深掘りする。
- ソース単体の紹介で終わらせず、既存KBの概念や地図がどう更新されたかを会話に含める。
- 最後に、明日以降の調査問いを2〜3個提示する。
