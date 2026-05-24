<!-- generated: 2026-05-24T13:00:48.143638+00:00 -->
<!-- kb_daily_digest_date: 2026-05-24 -->
# KB Daily Digest Source — 2026-05-24

このページは、knowledge-base-llm の日次更新を NotebookLM に読み込ませるための公開向けソースページです。
Discord通知よりも文脈を厚めに残し、Podcast化しやすいように、今日追加・更新されたソース、概念、地図を文章中心で整理します。

## 今日の全体像

今日の主なコミットは次の通りです: +0000 KB ingest: daily X bookmarks batch

## 重要ソース

### Cline SDK harness rebuild

Source note: `wiki/sources/cline-sdk-harness-rebuild-x-2026-05-13.md`

# Cline SDK harness rebuild

## Source Metadata
- Raw path: [[../../raw/articles/cline-sdk-harness-rebuild-x-2026-05-13.md]]
- Original URL: https://x.com/cline/status/2054580767779700775
- Primary URL: https://x.com/cline/status/2054580767779700775/video/1
- Author: Cline (@cline)
- Posted: 2026-05-13T15:13:21.000Z
- Captured: 2026-05-24 via xurl bookmarks capture
- Type: X video post
- Evidence strength: bookmark snapshot metadata plus video-card summary

## Linked URLs
- https://x.com/cline/status/2054580767779700775
- https://x.com/cline/status/2054580767779700775/video/1

## Bookmark text
> Introducing the Cline SDK. We rebuilt the Cline harness for our extension and CLI from scratch using all the lessons learned since creating one of the world's first coding agents in 2024, and are open sourcing it for others to build with today.

## What it says
Cline is packaging its agent harness as an SDK, which makes the runtime itself something other builders can extend rather than only consume.

## Why it matters
This is a compact example of harness engineering becoming a platform boundary. The product is no longer just the agent experience; it is the control surface and composition layer around it.

## Related concepts
- [[../concepts/harness-engineering.md]]
- [[../concepts/multi-agent-orchestration.md]]
- [[../concepts/managed-agents.md]]
- [[../concepts/tool-accessibility.md]]

## Open questions
- Which parts of the Cline harness belong in a public SDK versus remaining product-specific?
- How much of the runtime should be stable API versus inspectable implementation detail?

## Backlinks
- [[../concepts/harness-engineering.md]]
- [[../concepts/multi-agent-orchestration.md]]

### Chrome DevTools MCP CLI wrapper

Source note: `wiki/sources/conao3-rust-chrome-devtools-cli-wrapper-x-2026-05-22.md`

# Chrome DevTools MCP CLI wrapper

## Source Metadata
- Raw path: [[../../raw/articles/conao3-rust-chrome-devtools-cli-wrapper-x-2026-05-22.md]]
- Original URL: https://x.com/conao_3/status/2057735782157418722
- Primary URL: https://github.com/conao3/rust-chrome-devtools
- Author: Conao3 (@conao_3)
- Posted: 2026-05-22T08:10:16.000Z
- Captured: 2026-05-24 via xurl bookmarks capture
- Type: X post / GitHub repo pointer
- Evidence strength: bookmark snapshot metadata plus GitHub repo card

## Linked URLs
- https://github.com/conao3/rust-chrome-devtools
- https://x.com/conao_3/status/2057735782157418722

## Bookmark text
> @yusukebe Chrome devtools mcp、コンテキスト圧迫するので、軽くラップしたcli使ってます！

## What it says
This is a practical browser-debugging pattern: keep Chrome DevTools access behind a thinner CLI wrapper so the main agent session does not have to carry the full complexity of browser control.

## Why it matters
It is a small but useful example of tool accessibility as a harness choice. The right abstraction level can reduce context pressure without removing the capability.

## Related concepts
- [[../concepts/tool-accessibility.md]]
- [[../concepts/harness-engineering.md]]
- [[../concepts/coding-agents.md]]

## Open questions
- Which browser-debugging actions deserve a dedicated thin CLI versus a full MCP surface?
- When does wrapper thinness start hiding useful state instead of reducing noise?

## Backlinks
- [[../concepts/tool-accessibility.md]]
- [[../concepts/harness-engineering.md]]

### GBrain v0.14 jobs server for OpenClaw

Source note: `wiki/sources/gbrain-jobs-server-openclaw-x-2026-04-20.md`

# GBrain v0.14 jobs server for OpenClaw

## Source Metadata
- Raw path: [[../../raw/articles/gbrain-jobs-server-openclaw-x-2026-04-20.md]]
- Original URL: https://x.com/garrytan/status/2046060505127895051
- Primary URL: https://x.com/garrytan/status/2046060505127895051
- Author: Garry Tan (@garrytan)
- Posted: 2026-04-20T02:56:53.000Z
- Captured: 2026-05-24 via xurl bookmarks capture
- Type: X image post
- Evidence strength: bookmark snapshot metadata plus image-card summary

## Linked URLs
- https://x.com/garrytan/status/2046060505127895051
- https://x.com/mronge/status/2046059959759360001/photo/1

## Bookmark text
> GBrain v0.14 now has a jobs server for OpenClaw that significantly increases throughput and reduces gateway load, based on proven patterns from BullMQ.

## What it says
The post describes a jobs server addition to OpenClaw that improves throughput and reduces pressure on the gateway layer.

## Why it matters
This is a concrete example of the control plane moving from "nice to have" to core infrastructure once an agent system starts handling real workload volume.

## Related concepts
- [[../concepts/gateway-control-plane.md]]
- [[../concepts/background-agents.md]]
- [[../concepts/long-running-agents.md]]
- [[../concepts/company-brain.md]]

## Open questions
- Which workloads should be pushed into jobs versus kept in-session?
- What observability is required so gateway load changes do not hide latent failures?

## Backlinks
- [[../concepts/gateway-control-plane.md]]
- [[../concepts/background-agents.md]]

### Headless Mac mini setup for AI agents

Source note: `wiki/sources/mronge-headless-mac-mini-ai-agents-x-2026-05-22.md`

# Headless Mac mini setup for AI agents

## Source Metadata
- Raw path: [[../../raw/articles/mronge-headless-mac-mini-ai-agents-x-2026-05-22.md]]
- Original URL: https://x.com/mronge/status/2057885356163494051
- Primary URL: https://x.com/mronge/status/2057885356163494051/photo/1
- Author: Matt Ronge (@mronge)
- Posted: 2026-05-22T18:04:37.000Z
- Captured: 2026-05-24 via xurl bookmarks capture
- Type: X image post
- Evidence strength: bookmark snapshot metadata plus image-card summary

## Linked URLs
- https://x.com/mronge/status/2057885356163494051
- https://x.com/mronge/status/2057885356163494051/photo/1

## Bookmark text
> 6 mistakes I made setting up my headless Mac mini for AI agents:
> 1. Used my personal iCloud account
> 2. Left FileVault ON
> 3. Forgot auto-login
> 4. Bought an HDMI dummy plug
> 5. Trusted the default sleep settings
> 6. Port forwarded the public internet

## What it says
The post is a practical checklist of avoidable setup mistakes for a headless Mac mini used as an agent host.

## Why it matters
It is a compact reminder that agent infrastructure fails at the mundane layers first: account boundaries, login state, sleep policy, and exposure control.

## Related concepts
- [[../concepts/gateway-control-plane.md]]
- [[../concepts/agent-management.md]]
- [[../concepts/background-agents.md]]
- [[../concepts/harness-engineering.md]]

## Open questions
- Which baseline hardening should be standardized for headless agent hosts?
- Which parts of this checklist belong in setup automation instead of tribal knowledge?

## Backlinks
- [[../concepts/gateway-control-plane.md]]
- [[../concepts/agent-management.md]]
- [[../concepts/background-agents.md]]

### OpenAI Developers plugin for Codex

Source note: `wiki/sources/openai-developers-plugin-codex-x-2026-05-11.md`

# OpenAI Developers plugin for Codex

## Source Metadata
- Raw path: [[../../raw/articles/openai-developers-plugin-codex-x-2026-05-11.md]]
- Original URL: https://x.com/OpenAIDevs/status/2053925962287583379
- Primary URL: https://x.com/OpenAIDevs/status/2053925962287583379/video/1
- Author: OpenAI Developers (@OpenAIDevs)
- Posted: 2026-05-11T19:51:24.000Z
- Captured: 2026-05-24 via xurl bookmarks capture
- Type: X video post
- Evidence strength: bookmark snapshot metadata plus video-card summary

## Linked URLs
- https://x.com/OpenAIDevs/status/2053925962287583379
- https://x.com/OpenAIDevs/status/2053925962287583379/video/1

## Bookmark text
> Codex can now help you build AI apps and agents faster with OpenAI APIs using the OpenAI Developers plugin.

## What it says
The plugin gives Codex a more direct path into the OpenAI API surface for building apps and agents.

## Why it matters
It is a clean example of tool accessibility: the platform's own dev APIs become first-class inside the agent workflow instead of living outside it.

## Related concepts
- [[../concepts/tool-accessibility.md]]
- [[../concepts/coding-agents.md]]
- [[../concepts/harness-engineering.md]]

## Open questions
- Which OpenAI developer surfaces should be exposed to Codex next?
- Does tighter product/API integration reduce friction enough to change developer habits?

## Backlinks
- [[../concepts/tool-accessibility.md]]
- [[../concepts/coding-agents.md]]
- [[../concepts/harness-engineering.md]]

### LegalOn - AI-driven hiring and token budget

Source note: `wiki/sources/tsunoda-legalon-ai-driven-hiring-token-budget-x-2026-05-20.md`

# LegalOn - AI-driven hiring and token budget

## Source Metadata
- Raw path: [[../../raw/articles/tsunoda-legalon-ai-driven-hiring-token-budget-x-2026-05-20.md]]
- Original URL: https://x.com/Tsunoda_LegalOn/status/2057007417544581313
- Primary URL: https://x.com/i/article/2056956761270255616
- Author: 角田望｜LegalOn Technologies CEO (@Tsunoda_LegalOn)
- Posted: 2026-05-20T07:56:00.000Z
- Captured: 2026-05-24 via xurl bookmarks capture
- Type: X quote tweet / X article pointer
- Evidence strength: bookmark snapshot metadata plus article title card

## Linked URLs
- https://x.com/Tsunoda_LegalOn/status/2057007417544581313
- https://x.com/i/article/2056956761270255616

## Bookmark text
> 中途採用をゼロベースで見直し、トークン予算を確保した話_LegalOnのAI駆動化へのアプローチ

## What it says
The article frames AI adoption as an operating tradeoff: rethink hiring, preserve growth drivers, and allocate token budget explicitly instead of treating model usage as free background noise.

## Why it matters
It is a concrete example of AI ROI thinking turning into org design and budgeting, not just a tooling discussion.

## Related concepts
- [[../concepts/ai-roi-model.md]]
- [[../concepts/organizational-intent-clarity.md]]
- [[../concepts/company-brain.md]]
- [[../concepts/agent-management.md]]

## Open questions
- How should token budgets be tracked alongside headcount and infra budgets?
- Which hiring decisions actually become leverage points for AI-heavy workflows?

## Backlinks
- [[../concepts/ai-roi-model.md]]
- [[../concepts/organizational-intent-clarity.md]]
- [[../concepts/company-brain.md]]

## 更新された概念・地図

### AI ROI Model

KB note: `wiki/concepts/ai-roi-model.md`

---
aliases:
  - AI ROI Model
  - ROI of AI-assisted Software Development
  - AI Value Model
---

# AI ROI Model

## Definition
A structured way to estimate the return on AI-assisted software development by linking AI adoption to delivery metrics, business value, and adoption costs.

## Why It Matters
AI productivity claims are not enough for enterprise adoption. A credible model connects engineering indicators to financial outcomes while accounting for hard costs, learning costs, instability, and uncertainty.

## Related Concepts
- [[ai-adoption-j-curve]]
- [[verification-tax]]
- [[evidence-quality]]
- [[organizational-intent-clarity]]
- [[product-responsibility-distribution]]
- [[sustainable-ai-work]]
- [[agentic-jevons-paradox]]

## Supporting Sources
- [[../sources/dora-roi-ai-assisted-software-development.md]]
- [[../sources/simon-willison-gitlab-act-2.md]]
- [[../sources/tsunoda-legalon-ai-driven-hiring-token-budget-x-2026-05-20.md]]

## Model Shape
- Value: headcount reinvestmen

### Company Brain

KB note: `wiki/concepts/company-brain.md`

---
aliases:
  - Company Brain
---

# Company Brain

## Definition
A shared organizational context substrate that collects, structures, and updates company knowledge so multiple agents and humans can work from the same durable understanding layer.

## Why It Matters
A Company Brain is the company-scale version of a compiled wiki or context graph. It shifts agent performance from one-off prompting toward maintained context infrastructure.

## Related Concepts
- [[context graph]]
- [[compiled wiki]]
- [[agent knowledge loop]]
- [[agent management]]
- [[context farming]]
- [[organizational-intent-clarity.md]]

## Supporting Sources
- [[../sources/brett-goldstein-agentic-micro-companies-company-brain-x.md]]
- [[../sources/tsumotokai-context-graphs-agent-long-term-memory-x.md]]
- [[../sources/contextconor-enterprise-understanding-context-graph-x.md]]
- [[../sources/rohit-context-layer-compounding-systems-x.md]]
- [[../sources/recerqa-pdm-abolished-speakerdeck.md]]
- [[../sources/iwashi86-or

### Gateway Control Plane

KB note: `wiki/concepts/gateway-control-plane.md`

---
aliases:
  - Gateway Control Plane
  - Agent Gateway
---

# Gateway Control Plane

## Definition
A coordination layer that receives events from multiple channels, normalizes them, routes them to the appropriate agent/session, enforces session policy, broadcasts state, and returns results to the originating surface.

## Why It Matters
Personal and managed agents often have many entry points: chat apps, web UIs, device nodes, cron jobs, hooks, and webhooks. Without a control plane, those entry points fragment state and make it hard to coordinate long-running work safely.

## Related Concepts
- [[harness-engineering]]
- [[tool-accessibility]]
- [[context-engineering]]
- [[structured-handoff-artifacts]]
- [[long-running-agents]]
- [[background-agents]]

## Supporting Sources
- [[../sources/gargetisha-openclaw-under-the-hood-x-article.md]]
- [[../sources/newspicks-harness-engineering-what-is-it.md]]
- [[../sources/voxyz-ai-openclaw-shell-jobs-x.md]]
- [[../sources/openclaw-clawsweeper-r

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
