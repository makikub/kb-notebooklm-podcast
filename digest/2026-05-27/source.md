<!-- generated: 2026-05-27T13:01:54.951780+00:00 -->
<!-- kb_daily_digest_date: 2026-05-27 -->
# KB Daily Digest Source — 2026-05-27

このページは、knowledge-base-llm の日次更新を NotebookLM に読み込ませるための公開向けソースページです。
Discord通知よりも文脈を厚めに残し、Podcast化しやすいように、今日追加・更新されたソース、概念、地図を文章中心で整理します。

## 今日の全体像

# KB Daily Digest 2026-05-27

今日の knowledge-base-llm は、X ブックマーク由来の5本を新規 ingest / compile した。全体としては、agent harness を「プロンプトや設定ファイル」より広い実行環境として捉え直す更新になっている。安全境界、セキュリティ助言、ツール配布、ブラウザ操作、静的HTML成果物が同じ束に入り、エージェントを実務に置く時の論点がかなり具体化した。

重要ソースの1本目は **Anthropic — How we contain Claude across products**。Anthropic は、エージェントに与える権限は能力に合わせて変わるべきで、破壊的な操作を制約する中心的な面として sandboxing を位置づけている。KB上では [[../../wiki/concepts/harness-engineering.md]]、[[../../wiki/concepts/harnessability.md]]、[[../../wiki/concepts/agent-management.md]] に接続され、harness engineering が単に便利な作業補助ではなく、能力上昇に合わせた権限設計と安全境界の問題でもあることを補強した。

2本目は **ClaudeDevs — security guidance plugin for Claude Code**。Claude Code の plugin marketplace に、コードを書いている最中に脆弱性の発見と修正を助ける security-guidance plugin が入った、というシグナルだ。ここで面白いのは、セキュリティが後段レビューだけではなく、コーディングループの内側にプラグインとして入り込んでいる点。KBでは、guardrail や remediation が core harness に入るべきなのか、plugin として追加されるべきなのか、という実装境界の問いが立った。

3本目は **riywo — nix-claude-code GitHub repo**。Claude Code CLI を Nix flake overlay として配布し、公式 Anthropic release の pre-built binary を再現可能に入れるための repo が紹介されている。これは地味だが実務上かなり大きい。エージェントの性能はモデルだけでなく、同じCLI、同じ環境、同じ導入手順で動かせるかに左右される。KBでは [[../../wiki/concepts/agent-recognizable-repository.md]] とも接続され、ツール配布・環境再現性が harness の一部として扱われるようになった。

残り2本は、harness の出力面と操作面を広げている。**super_bonochin — Webwright for coding agents** は、Playwright を置き換えるのではなく、Codex / Claude Code / OpenClaw / Hermes 向けの plugin / skill として包み直す発想を示す。つまり browser automation の価値は automation core だけではなく、複数の agent ecosystem に差し込める形で配布されることにもある。**Paras Chopra — static HTML outputs for Claude Code** は、report、exploration、code structure、mockup を static HTML として出し、ブラウザ上でコメントしながら Claude に更新させるワークフローを示している。KBでは [[../../wiki/concepts/structured-handoff-artifacts.md]] に入り、HTML成果物が最終納品だけでなく、レビューと再編集の作業面にもなりうることを補強した。

全体トレンドとしては、「エージェントに何を言うか」から「エージェントをどの環境で、どの権限で、どの成果物形式で、どの配布面から動かすか」へ焦点が移っている。Anthropic の sandbox は安全境界、ClaudeDevs の plugin はコーディング中のガードレール、nix-claude-code は再現可能な導入面、Webwright は browser automation の agent-native 化、static HTML は人間がレビューしやすい成果物面をそれぞれ担当している。別々の話に見えるが、KBの harness-engineering から見ると全部「agent が安定して仕事を進めるための周辺設計」だ。

KB内の更新としては、raw/articles 5件、raw/x/bookmarks 1件、wiki/sources 5件が追加され、既存の [[../../wiki/concepts/harness-engineering.md]] と [[../../wiki/concepts/structured-handoff-artifacts.md]] が更新された。新規 concept や map は作られていないが、harness-engineering の supporting sources に、セキュリティ、配布、sandbox、browser automation、HTML artifact という実務寄りの補助線が追加されたのが大きい。

次に掘るなら、(1) sandbox / plugin / package manager / browser wrapper / HTML artifact を harness taxonomy 上でどう分けるか、(2) security guidance plugin のような助言型ガードレールをいつ実行型 remediation に進めるべきか、(3) static HTML を durable handoff artifact として運用する時に、Markdown や wiki note とどう役割分担するか、がよさそう。

## Important sources

- Anthropic — How we contain Claude across products: https://www.anthropic.com/engineering/how-we-contain-claude
- ClaudeDevs — security guidance plugin for Claude Code: https://x.com/ClaudeDevs/status/2059385239781384341
- riywo — nix-claude-code GitHub repo: https://github.com/ryoppippi/nix-claude-code
- super_bonochin — Webwright for coding agents: https://x.com/super_bonochin/status/2059284808988344370
- Paras Chopra — static HTML outputs for Claude Code: https://x.com/paraschopra/status/2059167147516199152

## Changed KB files

- raw/articles/anthropic-how-we-contain-claude-across-products-x-2026-05-26.md
- raw/articles/claudedevs-security-guidance-plugin-claude-code-x-2026-05-26.md
- raw/articles/paraschopra-static-html-claude-code-x-2026-05-26.md
- raw/articles/riywo-nix-claude-code-github-x-2026-05-26.md
- raw/articles/super-bonochin-webwright-coding-agents-x-2026-05-26.md
- raw/x/bookmarks/bookmarks-20260527T0004Z.json
- wiki/sources/anthropic-how-we-contain-claude-across-products-x-2026-05-26.md
- wiki/sources/claudedevs-security-guidance-plugin-claude-code-x-2026-05-26.md
- wiki/sources/paraschopra-static-html-claude-code-x-2026-05-26.md
- wiki/sources/riywo-nix-claude-code-github-x-2026-05-26.md
- wiki/sources/super-bonochin-webwright-coding-agents-x-2026-05-26.md
- wiki/concepts/harness-engineering.md
- wiki/concepts/structured-handoff-artifacts.md


## 重要ソース

### Anthropic — How we contain Claude across products

Source note: `wiki/sources/anthropic-how-we-contain-claude-across-products-x-2026-05-26.md`

# Anthropic — How we contain Claude across products

## Source Metadata
- Raw path: raw/articles/anthropic-how-we-contain-claude-across-products-x-2026-05-26.md
- Original URL: https://x.com/AnthropicAI/status/2059351260243919269
- Primary URL: https://www.anthropic.com/engineering/how-we-contain-claude
- Author: Anthropic
- Date: 2026-05-26
- Type: X post linking to engineering blog
- Evidence strength: direct xurl bookmarks capture

## Summary
Anthropic says the permissions granted to agents should evolve with their capabilities, and that sandboxing is how they constrain potentially destructive actions in their own products.

## Key Claims
- Access policy should be capability-adaptive.
- Sandboxing is a core control surface for destructive actions.
- Product guardrails should evolve as agents become more capable.

## Evidence / Examples
- The X post points to Anthropic's engineering blog as the stronger primary source.
- The post frames sandboxing as the concrete mechanism for limiting scope.

## Evidence Quality
- Source type: X post linking to blog
- Confidence: high for the post's framing, moderate for any details not visible in the bookmark text.

## Related Concepts
- [[harness-engineering]]
- [[harnessability]]
- [[agent-management]]

## Open Questions
- Which permission changes should be automatic, and which should require explicit human review?
- What sandbox boundaries are most effective for long-running agent products?

## Backlinks
- [[../concepts/harness-engineering.md]]
- [[../concepts/harnessability.md]]
- [[../concepts/agent-management.md]]

### ClaudeDevs — security guidance plugin for Claude Code

Source note: `wiki/sources/claudedevs-security-guidance-plugin-claude-code-x-2026-05-26.md`

# ClaudeDevs — security guidance plugin for Claude Code

## Source Metadata
- Raw path: raw/articles/claudedevs-security-guidance-plugin-claude-code-x-2026-05-26.md
- Original URL: https://x.com/ClaudeDevs/status/2059385239781384341
- Author: ClaudeDevs
- Date: 2026-05-26
- Type: X post
- Evidence strength: direct xurl bookmarks capture

## Summary
ClaudeDevs says Claude Code now has a security-guidance plugin that helps identify and fix vulnerabilities while code is being written. It is available to all Claude Code users through the plugin marketplace.

## Key Claims
- Security guidance is moving into the coding loop instead of staying a separate review step.
- Plugin surfaces are becoming a first-class place for guardrails and remediation help.
- Claude Code users can install the plugin from the marketplace.

## Evidence / Examples
- The captured post text is the only evidence in this note.
- The post announces availability for all users and points to /plugins.

## Evidence Quality
- Source type: X post
- Confidence: moderate for the feature framing, lower for implementation details not present in the post.
- Main limitation: no stronger primary source was captured in this bookmark.

## Related Concepts
- [[harness-engineering]]
- [[harnessability]]
- [[agent-management]]

## Open Questions
- How much security guidance belongs in a plugin versus in the core agent harness?
- Which remediation actions should be advisory only versus directly executable?

## Backlinks
- [[../concepts/harness-engineering.md]]
- [[../concepts/harnessability.md]]
- [[../concepts/agent-management.md]]

### Paras Chopra — static HTML outputs for Claude Code

Source note: `wiki/sources/paraschopra-static-html-claude-code-x-2026-05-26.md`

# Paras Chopra — static HTML outputs for Claude Code

## Source Metadata
- Raw path: raw/articles/paraschopra-static-html-claude-code-x-2026-05-26.md
- Original URL: https://x.com/paraschopra/status/2059167147516199152
- Author: Paras Chopra
- Date: 2026-05-26
- Type: X post
- Evidence strength: direct xurl bookmarks capture

## Summary
Paras Chopra says his favorite way to use Claude Code is to have it generate static HTML outputs like reports, explorations, code structure, and mockups. He then iterates on the file in the browser by commenting and having Claude update the output live.

## Key Claims
- Static HTML is a strong artifact format for agent output.
- Browser commenting creates a tight review-and-revise loop.
- Output artifacts can be treated as editable workspaces rather than final deliverables.

## Evidence / Examples
- The bookmark text itself is the core evidence.
- The post references a live HTML artifact workflow, but no stronger source was captured here.

## Evidence Quality
- Source type: X post
- Confidence: moderate for the workflow pattern, lower for any claimed broader best practice.

## Related Concepts
- [[structured-handoff-artifacts]]
- [[harness-engineering]]
- [[workflow-compilation]]

## Open Questions
- Which kinds of outputs are best served by static HTML instead of markdown or plain text?
- When does an output artifact become a durable handoff artifact rather than a one-off result?

## Backlinks
- [[../concepts/structured-handoff-artifacts.md]]
- [[../concepts/harness-engineering.md]]
- [[../concepts/workflow-compilation.md]]

### riywo — nix-claude-code GitHub repo

Source note: `wiki/sources/riywo-nix-claude-code-github-x-2026-05-26.md`

# riywo — nix-claude-code GitHub repo

## Source Metadata
- Raw path: raw/articles/riywo-nix-claude-code-github-x-2026-05-26.md
- Original URL: https://x.com/riywo/status/2059348291058586092
- Primary URL: https://github.com/ryoppippi/nix-claude-code
- Author: Ryosuke Iwanaga
- Date: 2026-05-26
- Type: X post linking to GitHub repo
- Evidence strength: direct xurl bookmarks capture

## Summary
Ryosuke Iwanaga highlights ryoppippi's nix-claude-code repo as very useful and says he uses it across all of his environments. The linked repo provides a Nix flake overlay that ships pre-built Claude Code CLI binaries from official Anthropic releases.

## Key Claims
- Packaging Claude Code through Nix makes the toolchain easier to reproduce across machines.
- Pre-built official binaries reduce setup friction.
- A reusable installer layer can become part of an agent harness.

## Evidence / Examples
- The X post gives the adoption signal.
- The GitHub repo is the stronger source for installation details and packaging behavior.

## Evidence Quality
- Source type: X post + linked GitHub repo
- Confidence: high for the existence of the repo and the user's endorsement; moderate for broader harness implications.

## Related Concepts
- [[harness-engineering]]
- [[harnessability]]
- [[agent-recognizable-repository]]

## Open Questions
- Which parts of agent-tool distribution are best solved by package managers like Nix?
- How much does tool reproducibility matter for agent reliability in daily use?

## Backlinks
- [[../concepts/harness-engineering.md]]
- [[../concepts/harnessability.md]]
- [[../concepts/agent-recognizable-repository.md]]

### super_bonochin — Webwright for coding agents

Source note: `wiki/sources/super-bonochin-webwright-coding-agents-x-2026-05-26.md`

# super_bonochin — Webwright for coding agents

## Source Metadata
- Raw path: raw/articles/super-bonochin-webwright-coding-agents-x-2026-05-26.md
- Original URL: https://x.com/super_bonochin/status/2059284808988344370
- Author: 炎鎮🔥 - ₿onochin -
- Date: 2026-05-26
- Type: X post
- Evidence strength: direct xurl bookmarks capture

## Summary
The post describes Webwright as Playwright tuned for coding agents. It says plugins and skills are available for Codex, Claude Code, OpenClaw, and Hermes, and that Webwright wraps Playwright rather than replacing it.

## Key Claims
- Browser automation is being repackaged as agent-specific tooling.
- Thin wrappers around Playwright can make browser control easier to slot into multiple agent ecosystems.
- Plugin and skill distribution matters as much as the automation core.

## Evidence / Examples
- The bookmark includes a preview image and a linked thread reference, but no stronger primary source was captured here.
- The post itself is enough to treat Webwright as an agent-tooling signal, not as a technical specification.

## Evidence Quality
- Source type: X post
- Confidence: moderate for the high-level pattern, lower for implementation specifics.

## Related Concepts
- [[harness-engineering]]
- [[harnessability]]
- [[navigable-agent-skills]]
- [[agent-recognizable-repository]]

## Open Questions
- How much value comes from the wrapper versus the underlying Playwright control model?
- What does a portable browser-automation skill need to expose to stay useful across agent frameworks?

## Backlinks
- [[../concepts/harness-engineering.md]]
- [[../concepts/harnessability.md]]
- [[../concepts/navigable-agent-skills.md]]
- [[../concepts/agent-recognizable-repository.md]]

## 更新された概念・地図

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

### Structured Handoff Artifacts

KB note: `wiki/concepts/structured-handoff-artifacts.md`

---
aliases:
  - Structured Handoff Artifacts
---

# Structured Handoff Artifacts

## Definition
Persistent artifacts such as progress logs, feature lists, plans, and commit history that allow one agent session to hand work off to another cleanly.

## Why It Matters
Without structured handoffs, long-running work across multiple context windows becomes brittle and repetitive.

## Related Concepts
- [[initializer-agent]]
- [[rich-agent-output-artifact.md]]
- [[context-resets]]
- [[incremental-progress]]
- [[long-running-agents]]

## Supporting Sources
- [[../sources/openai-harness-engineering.md]]
- [[../sources/anthropic-effective-harnesses-long-running-agents.md]]
- [[../sources/oikon48-team-onboarding-x.md]]
- [[../sources/oikon48-ultraplan-x.md]]
- [[../sources/anthropic-claude-code-ultraplan-docs.md]]
- [[../sources/cursor-pr-demos-x.md]]
- [[../sources/noahzweben-autofix-pr-x.md]]
- [[../sources/aparnadhinak-harness-vs-sandbox-trajectory-x.md]]
- [[../sources/nyk-builderz-4-agent-h

## NotebookLM Podcast用メモ

- まず今日の全体トレンドを話してから、重要ソースを3本に絞って深掘りする。
- ソース単体の紹介で終わらせず、既存KBの概念や地図がどう更新されたかを会話に含める。
- 最後に、明日以降の調査問いを2〜3個提示する。
