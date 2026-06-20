<!-- generated: 2026-06-20T13:02:02.901239+00:00 -->
<!-- kb_daily_digest_date: 2026-06-20 -->
# KB Daily Digest Source — 2026-06-20

このページは、knowledge-base-llm の日次更新を NotebookLM に読み込ませるための公開向けソースページです。
Discord通知よりも文脈を厚めに残し、Podcast化しやすいように、今日追加・更新されたソース、概念、地図を文章中心で整理します。

## 今日の全体像

# KB Daily Digest 2026-06-20

UTC 2026-06-20 の knowledge-base-llm 更新は、agent harness が「個別ツールを呼ぶ仕組み」から「組織の業務面に埋め込まれる運用基盤」へ寄っていることを示す ingest だった。新規 raw は AWS Blocks の Zenn 記事 1本と、X bookmark batch 由来の 5本、計 6本。新規 wiki source は `aws-japan-aws-blocks-ai-agent-intro-zenn.md`、`claudedevs-enterprise-managed-auth-extension-to-mcp-x-2026-06-18.md`、`layerx-tech-prompt-log-driven-ai-workflow-x-2026-06-18.md`、`openaidevs-codex-record-replay-skill-x-2026-06-18.md`、`slackhq-slackbot-mcp-client-x-2026-06-18.md`、`tyehoshua-claude-agent-for-jira-x-2026-06-18.md`。あわせて `infrastructure-from-code`、`harness-engineering`、`human-in-the-loop`、`managed-agents`、`tool-accessibility`、`agent-harness-landscape`、`harness` navigation が更新され、KB全体では「agent をどう作るか」よりも「どの実行面・承認面・接続面に置くか」が強調された。

全体トレンドは、MCP / managed agents / workflow compilation / infrastructure from code が同じ地図上に乗ってきたことだ。Slackbot の MCP client、Claude Agent for Jira、ClaudeDevs の Enterprise-Managed Auth は、いずれも agent や connector をエンドユーザーのチャットやチケットに置きつつ、裏側では管理者承認、権限、監査、組織スケールの接続性を必要とする。LayerX と OpenAI Developers の Record & Replay は、繰り返し発生する作業をログや実演から抽出し、Skill / Command / Schedule のような再利用可能な artifact に変換する流れを補強している。AWS Blocks はそのさらに下で、RAG、streaming、tool calls、approval、conversation state、CDK synthesis を typed application construct として束ねる例になっている。

重要ソースの1本目は AWS Japan / showish による AWS Blocks のハンズオン記事。AWS Blocks は TypeScript の Infrastructure from Code framework として紹介され、`Agent` と `KnowledgeBase` Blocks を使った support agent demo が扱われている。KB上で特に重要なのは、local mocks、CDK synthesis、deployed runtime implementation、Bedrock/RAG wiring、streaming、tool calls、conversation state、human approval/resume までが一つの開発面に圧縮されている点だ。`needsApproval: true` によって tool call を人間承認チェックポイントに変えられることも、agent harness の承認設計として大きい。著者の実行では v0.1.1 の template / dependency / local dev-server まわりに揺れもあり、証拠品質は「具体的な hands-on として中程度、運用判断には公式docsとの照合が必要」と見ている。

重要ソースの2本目は Slack の Slackbot MCP client announcement。Slackbot が Replit、Amplitude、Linear、Canva などを含む 20以上の partner apps を MCP 経由で扱う、という公式 product update で、KBでは tool accessibility と managed-agent control plane の材料になる。ここでの読みどころは、MCP が単体の開発者向け protocol ではなく、チームの日常業務が集まるチャット面に入ってくることだ。いっぽうで bookmark snapshot だけでは、connector auth、admin approval、read/write scope、監査ログの詳細は分からない。したがってこの source は「Slack が MCP を業務ハブの接続層として扱っている」という方向性には強いが、セキュリティモデルの判断材料としては追跡が必要。

重要ソースの3本目は OpenAI Developers の Record & Replay と LayerX の prompt-log-driven AI workflow を合わせて読むのがよい。Record & Replay は「一度ワークフローを見せると Codex skill として再利用できる」という product framing で、生成される skill が inspectable / editable であることが強調されている。LayerX 側は、AI conversation logs を見直して繰り返し作業を見つけ、Skills、Commands、Schedules に昇格する仕組みを示している。片方は実演から skill を作る話、もう片方はログの集約とレビューから workflow artifact を作る話だが、KB上ではどちらも workflow compilation と trace-driven improvement の同じ流れに入る。

ClaudeDevs の Enterprise-Managed Auth extension for MCP と Tamar Yehoshua の Claude Agent for Jira は、agent が企業内で使われるときの運用境界を補強した。Enterprise-Managed Auth は、admin が connector を組織単位で centrally authorize し、ユーザーが初回ログイン時から接続済みの tool / data に到達できる、という方向性を示す。Claude Agent for Jira は、Jira task をそのまま prompt / handoff unit とし、Claude が issue を読み、codeを書き、PRを返すという managed background agent の形を示す。どちらも便利さだけでなく、central policy、revocation、audit、review gate、ticketing system への状態反映が次の問いになる。

概念更新では `wiki/concepts/infrastructure-from-code.md` が新規追加され、application code から infrastructure を導出する設計として AWS Blocks が位置づけられた。`harness-engineering`、`human-in-the-loop`、`managed-agents`、`tool-accessibility` には AWS Blocks や X bookmark batch 由来の接続が追加され、`agent-harness-landscape` では agent framework、enterprise connector、chat hub、issue-driven agent、workflow compilation が一枚の landscape に近づいた。`harness` navigation にも AWS Blocks source が追加され、local-first agent demo から cloud deployment / generated resource review に入る導線ができている。

実務上の示唆は、agent 導入の重心が「モデルに何を頼むか」から「作業面をどこに置き、権限と再利用性をどう管理するか」へ移っていることだ。Slack や Jira のような既存業務面に agent が入るほど、ユーザーの採用障壁は下がるが、connector scope、admin consent、承認フロー、PR review、ログ保持が設計の中心になる。AWS Blocks のような framework は cloud 側の構成を速く作れるが、生成される CloudFormation resources、コスト、runtime behavior、local mock と本番 Bedrock の差分を review gate に乗せる必要がある。Record & Replay や LayerX 型の仕組みは、良い手順を reusable skill にしやすい一方で、低品質な手順を schedule や command として固定化しないためのレビューが必要になる。

Podcastで掘るなら、今日は「agent harness は、開発者の手元の便利ツールから、組織の control plane へどう変わっているのか」を主題にすると話しやすい。最初に AWS Blocks で下層の infrastructure / runtime 圧縮を見て、次に Slackbot MCP と Claude Agent for Jira で業務面への埋め込みを見て、最後に Record & Replay / LayerX で繰り返し作業の skill 化を扱う構成がよい。次に追う問いは、MCP connector の enterprise auth / audit semantics、Jira-driven coding agent の review gate、AWS Blocks v0.1.x の安定性、そして workflow compilation の品質基準の4つ。

公開HTML: https://makikub.github.io/kb-notebooklm-podcast/digest/2026-06-20/

NotebookLM用 source.md: https://makikub.github.io/kb-notebooklm-podcast/digest/2026-06-20/source.md


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

### AWS Japan / showish - AWS Blocks AI Agent Intro

Source note: `wiki/sources/aws-japan-aws-blocks-ai-agent-intro-zenn.md`

---
aliases:
  - AWS Blocks AI agent intro Zenn
  - AWS Blocks support agent demo
source_url: "https://zenn.dev/aws_japan/articles/aws-blocks-ai-agent-intro"
raw: "../../raw/articles/aws-japan-aws-blocks-ai-agent-intro-zenn-2026-06-18.md"
captured: "2026-06-20"
---

# AWS Japan / showish - AWS Blocks AI Agent Intro

## Summary
This Zenn article introduces AWS Blocks as a TypeScript [[../concepts/infrastructure-from-code.md]] framework and walks through a local-first AI support-agent demo built with `Agent` and `KnowledgeBase` Blocks.

The important KB signal is that AWS Blocks packages several agent-harness concerns into typed application constructs: local mocks, CDK synthesis, deployed runtime implementations, Bedrock/RAG wiring, streaming, tool calls, conversation state, and [[../concepts/human-in-the-loop.md]] approval/resume.

## Key Claims
- AWS Blocks follows an "Infrastructure from Code" model: application code is the source from which AWS infrastructure is derived.
- A single `Block` can expose a local implementation, a CDK construct, and a deployed runtime implementation.
- Local development can start without AWS credentials or Docker-style emulation; the local path is mainly for wiring verification.
- The `Agent` and `KnowledgeBase` Blocks compress RAG, tools, streaming, conversation state, and approval mechanics into a small TypeScript surface.
- `needsApproval: true` turns a tool call into a human approval checkpoint.
- The same app can be deployed to AWS, where the Blocks expand into resources such as Bedrock Knowledge Bases, S3 Vectors, DynamoDB, API Gateway, SQS/Lambda, Step Functions, IAM, S3, and CloudFront/S3 hosting.
- AWS Blocks is promising but still early; the author's v0.1.1 run hit template, dependency, and local dev-server issues.

## Evidence /

### ClaudeDevs - Enterprise-Managed Auth extension comes to MCP

Source note: `wiki/sources/claudedevs-enterprise-managed-auth-extension-to-mcp-x-2026-06-18.md`

# ClaudeDevs - Enterprise-Managed Auth extension comes to MCP

## Source Metadata
- Raw path: [[../../raw/articles/claudedevs-enterprise-managed-auth-extension-to-mcp-x-2026-06-18.md]]
- Raw bookmark capture: [[../../raw/x/bookmarks/bookmarks-20260620T0000Z.json]]
- Original URL: https://x.com/i/status/2067655887662272723
- Primary URL: https://x.com/ClaudeDevs/status/2067655887662272723/video/1
- Author: ClaudeDevs (@ClaudeDevs)
- Posted: 2026-06-18T17:09:13.000Z
- Captured: 2026-06-20 via xurl bookmarks capture
- Type: X post / product update
- Evidence strength: bookmark snapshot metadata plus official product teaser

## Summary
This post announces Enterprise-Managed Auth support for MCP. The core claim is that admins can centrally authorize connectors for their organization, reducing first-login friction and making MCP more viable in enterprise deployments.

## Key Claims
- MCP now supports the Enterprise-Managed Auth extension.
- Admins can centrally authorize connectors for the whole organization.
- Users should reach a useful first-login state with tools and data already connected.

## Evidence / Examples
- The tweet text directly names centrally managed authorization.
- The announcement is framed as an admin and deployment feature rather than a consumer-facing convenience.
- This is the kind of control plane that matters when connectors scale beyond a small team.

## Evidence Quality
- Source type: X official product update
- Confidence: high for the extension announcement; medium for implementation details
- Supports: enterprise tool accessibility, gateway control, and approval-policy design
- Main limitations: the bookmark does not expose connector scoping rules or audit semantics
- Best use: connect MCP adoption discussions to operational governance and permi

### LayerX Tech - prompt-log-driven AI workflow

Source note: `wiki/sources/layerx-tech-prompt-log-driven-ai-workflow-x-2026-06-18.md`

# LayerX Tech - prompt-log-driven AI workflow

## Source Metadata
- Raw path: [[../../raw/articles/layerx-tech-prompt-log-driven-ai-workflow-x-2026-06-18.md]]
- Raw bookmark capture: [[../../raw/x/bookmarks/bookmarks-20260620T0000Z.json]]
- Original URL: https://x.com/i/status/2067463450348196081
- Primary URL: https://tech.layerx.co.jp/entry/prompt-log-driven-ai-workflow
- Author: LayerX Tech (@LayerX_tech)
- Posted: 2026-06-18T04:24:32.000Z
- Captured: 2026-06-20 via xurl bookmarks capture
- Type: X bookmark / blog article card
- Evidence strength: bookmark snapshot metadata plus linked blog title and description

## Summary
LayerX describes a system for reviewing prompt logs, finding repeated work, and turning those repeats into Skills, Commands, and Schedules. This is one of the clearest examples in the capture set of trace-driven improvement becoming a reusable workflow layer.

## Key Claims
- AI conversation logs can be mined for repeated work.
- Repetitive work can be promoted into reusable Skills, Commands, and Schedules.
- Workflow review is part of the operational loop, not an afterthought.

## Evidence / Examples
- The captured tweet explicitly mentions prompt-log aggregation.
- The linked blog article title says the team built a system to review AI interactions.
- The description points to a process for converting repeated prompts into reusable work artifacts.

## Evidence Quality
- Source type: X bookmark snapshot with linked blog article card
- Confidence: medium-high for the workflow pattern; medium for implementation specifics
- Supports: workflow compilation, trace-driven improvement, skill packaging, and KB linting
- Main limitations: the bookmark does not include the full article body
- Best use: connect recurring-task detection to durable workflow ar

### OpenAI Developers - Record & Replay turns a workflow into a reusable skill

Source note: `wiki/sources/openaidevs-codex-record-replay-skill-x-2026-06-18.md`

# OpenAI Developers - Record & Replay turns a workflow into a reusable skill

## Source Metadata
- Raw path: [[../../raw/articles/openaidevs-codex-record-replay-skill-x-2026-06-18.md]]
- Raw bookmark capture: [[../../raw/x/bookmarks/bookmarks-20260620T0000Z.json]]
- Original URL: https://x.com/i/status/2067681320281723113
- Primary URL: https://x.com/OpenAIDevs/status/2067681320281723113/video/1
- Author: OpenAI Developers (@OpenAIDevs)
- Posted: 2026-06-18T18:50:17.000Z
- Captured: 2026-06-20 via xurl bookmarks capture
- Type: X post / product announcement
- Evidence strength: bookmark snapshot metadata plus official product teaser

## Summary
OpenAI frames Record & Replay as a way to show Codex a workflow once and then reuse it as a skill. The feature is explicitly described as turning a demo into an inspectable, editable skill, which makes the underlying automation much easier to maintain and audit than a one-off run.

## Key Claims
- A workflow can be recorded once and reused as a Codex skill.
- The resulting skill is inspectable and editable.
- Recurrent administrative work is a legitimate target for this packaging approach.

## Evidence / Examples
- The tweet text explicitly uses "Show Codex a workflow once. Reuse it as a skill."
- The post names recurring tasks such as expense reports and time-off requests.
- The wording suggests a durable workflow artifact rather than a single ephemeral completion.

## Evidence Quality
- Source type: X official product teaser
- Confidence: high for the feature framing; medium for exact UX and lifecycle details
- Supports: navigable agent skills, workflow compilation, and rule-update loops
- Main limitations: the bookmark does not expose the full authoring model or review flow
- Best use: compare skill creation and reuse with oth

### Slackbot - MCP client adds more than 20 partner apps

Source note: `wiki/sources/slackhq-slackbot-mcp-client-x-2026-06-18.md`

# Slackbot - MCP client adds more than 20 partner apps

## Source Metadata
- Raw path: [[../../raw/articles/slackhq-slackbot-mcp-client-x-2026-06-18.md]]
- Raw bookmark capture: [[../../raw/x/bookmarks/bookmarks-20260620T0000Z.json]]
- Original URL: https://x.com/i/status/2067638851938463962
- Primary URL: https://x.com/SlackHQ/status/2067638851938463962/video/1
- Author: Slack (@SlackHQ)
- Posted: 2026-06-18T16:01:31.000Z
- Captured: 2026-06-20 via xurl bookmarks capture
- Type: X post / product announcement
- Evidence strength: bookmark snapshot metadata plus official product teaser

## Summary
Slackbot's MCP client is framed as a general work hub with more than 20 partner apps. The explicit examples are Replit, Amplitude, Linear, and Canva, which suggests Slack is treating MCP as a connector layer for day-to-day team operations rather than a niche integration demo.

## Key Claims
- Slackbot can now front a large set of partner apps through MCP.
- The integration surface spans coding, analytics, task tracking, and design tools.
- The product direction is toward a chat-native control plane for work.

## Evidence / Examples
- The tweet text explicitly says "more than 20 partner apps".
- Named examples include Replit, Amplitude, Linear, and Canva.
- The linked video implies this is an official product update rather than a community workaround.

## Evidence Quality
- Source type: X official product teaser
- Confidence: high for the announcement; medium for exact rollout breadth
- Supports: tool accessibility, managed-agent control planes, and cross-app workflow orchestration
- Main limitations: no technical detail on permissions, connector auth, or admin controls in the bookmark text
- Best use: compare Slack's connector strategy with MCP surfaces from other vendors

## R

### Tamar Yehoshua - Claude Agent for Jira

Source note: `wiki/sources/tyehoshua-claude-agent-for-jira-x-2026-06-18.md`

# Tamar Yehoshua - Claude Agent for Jira

## Source Metadata
- Raw path: [[../../raw/articles/tyehoshua-claude-agent-for-jira-x-2026-06-18.md]]
- Raw bookmark capture: [[../../raw/x/bookmarks/bookmarks-20260620T0000Z.json]]
- Original URL: https://x.com/i/status/2067715685871214817
- Primary URL: https://x.com/TYehoshua/status/2067715685871214817/video/1
- Author: Tamar Yehoshua (@TYehoshua)
- Posted: 2026-06-18T21:06:50.000Z
- Captured: 2026-06-20 via xurl bookmarks capture
- Type: X post / product announcement
- Evidence strength: bookmark snapshot metadata plus product teaser video

## Summary
The post announces Claude Agent for Jira and says it is built on Anthropic's Claude Managed Agents infrastructure. The operational idea is simple but important: a Jira work item becomes the prompt, Claude reads the task, writes code, and returns a PR.

## Key Claims
- Claude Agent for Jira is shipped.
- The integration uses Claude Managed Agents infrastructure.
- Jira tasks can be assigned directly to Claude.
- Claude can read the issue, write code, and open a PR.

## Evidence / Examples
- The tweet text explicitly names the workflow from issue to code to PR.
- The post frames the work item itself as the prompt, which is a strong handoff abstraction.
- The product positioning implies a managed background agent rather than a chat assistant.

## Evidence Quality
- Source type: X product announcement
- Confidence: high for the shipped integration claim; medium for the deeper operational model
- Supports: managed agents, background agents, tool accessibility, and task decomposition
- Main limitations: the bookmark does not expose the review gate or security model
- Best use: compare issue-driven agent handoffs with other long-running work surfaces

## Related Concepts
- [[../concep

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
- [Conversion Packaging](conversion-packaging.md)
- [Organizational Intent Clarity](organizational-intent-clarity.md)
- [Exploratory Organization Lens](exploratory-organization-lens.md)
- [Intelligent Delegation](intelligent-delegation.md)
- [Conversational Feedback Learning](conversational-feedback-learning.md)
- [Spec-Code-Test Loop](spec-code-test-loop.md)
- [Heavy Thinking](heavy-thinking.md)
- [Sustainable AI Work](sustainable-ai-work.md)
- [AI Adoption J-Curve](ai-adoption-j-curve.md)
- [AI Adoption Thresholds](ai-adoption-thresholds.md) — usage-rate bands th

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

### Human in the Loop

KB note: `wiki/concepts/human-in-the-loop.md`

---
aliases:
  - Human in the Loop
---

# Human in the Loop

## Definition
An operating pattern where the human remains the final or periodic decision-maker for selected agent actions or checkpoints.

## Why It Matters
It allows practical deployment of more capable agents without requiring full trust in autonomous action.

## Related Concepts
- [[approval-policy]]
- [[agent-autonomy]]
- [[agent-safety]]
- [[intelligent-delegation.md]]

## Supporting Sources
- [[../sources/anthropic-claude-code-auto-mode.md]]
- [[../sources/tsumotokai-context-graphs-agent-long-term-memory-x.md]]

- [[../sources/y-matsuwitter-harness-roles-meta-definition-x.md]]
- [[../sources/zento-ai-claude-web-slack-summary-routine-x.md]]
- [[../sources/claudeai-claude-code-routines-research-preview-x.md]]
- [[../sources/noahzweben-claude-code-routines-x.md]]
- [[../sources/trq212-ultraplan-x.md]]
- [[../sources/arxiv-intelligent-ai-delegation.md]]
- [[../sources/aws-japan-aws-blocks-ai-agent-intro-zenn.md]]

## Trade

### Infrastructure from Code

KB note: `wiki/concepts/infrastructure-from-code.md`

---
aliases:
  - Infrastructure from Code
  - IFC
---

# Infrastructure from Code

## Definition
An application-development pattern where infrastructure is derived from application code and framework constructs, instead of being authored primarily as a separate infrastructure definition.

## Why It Matters
Infrastructure from Code can reduce the setup cost for agent applications because runtime state, queues, permissions, streaming channels, retrieval infrastructure, and deployment resources can be generated from higher-level app concepts.

For agent systems, this makes the harness more productized: a developer may instantiate an `Agent`, `KnowledgeBase`, or auth block and get local mocks plus deployable cloud infrastructure without manually assembling every service.

## Related Concepts
- [[harness-engineering.md]]
- [[managed-agents.md]]
- [[environment-bootstrapping.md]]
- [[tool-accessibility.md]]
- [[machine-checkable-invariants.md]]

## Supporting Sources
- [[../sources/aws-japan

### Managed Agents

KB note: `wiki/concepts/managed-agents.md`

---
aliases:
  - Managed Agent
  - Managed Agents
---

# Managed Agents

## Definition
Hosted or product-managed agent runtimes that package model execution with tools, permissions, memory, tracing, sandboxing, and operational controls.

## Why It Matters
Managed agents turn agent operation into a deployable surface rather than a local prompt pattern. They make it easier to build roleful domain agents, but they also move important governance decisions into the runtime: what tools are exposed, how memory persists, what is sandboxed, and how humans inspect or intervene.

## Related Concepts
- [[multi-agent-orchestration.md]]
- [[agent-dreaming.md]]
- [[outcomes.md]]
- [[tool-accessibility.md]]
- [[agent-management.md]]
- [[agent-safety.md]]
- [[background-agents.md]]
- [[context-engineering.md]]

## Supporting Sources
- [[../sources/claudeai-claude-managed-agents-intro-x.md]]
- [[../sources/claude-new-in-managed-agents-dreaming-outcomes-orchestration.md]]
- [[../sources/oikon48-claude-ma

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

### Map Notes

KB note: `wiki/maps/README.md`

# Map Notes

Map notes connect multiple concepts and sources.

Examples:
- landscape overviews
- comparison notes
- timelines
- architecture maps
- taxonomy notes
- control vocabularies and cross-source synthesis notes
- deployment-gate and operational-risk notes that connect repo controls to production safety
- evidence-quality and source-trust notes that rank claim support
- query-path notes that route recurring user questions through stable map/concept/source paths
- navigation-support notes that help `wiki/navigation/` expose corpus shape before source-level lookup
- approval-pattern and escalation maps that connect autonomy settings to review burden
- infrastructure-from-code notes that connect application constructs to generated cloud/runtime harnesses

## Current maps

- [Context Graph and Company Brain](context-graph-and-company-brain.md)
- [Agent Onboarding with Domain KB + Codebase](agent-onboarding-kb-codebase.md)
- [Context Management Decision Map](context-management-decisi

### Agent Harness Landscape

KB note: `wiki/maps/agent-harness-landscape.md`

# Agent Harness Landscape

## Purpose
This map connects the emerging idea of harness engineering across several sources and shows how it fits into the broader LLM agents knowledge base.

## Core thesis
Agent performance is not just a function of the model. It depends heavily on the harness: the repository structure, controls, artifacts, tests, review loops, and orchestration patterns around the model.

## Main dimensions

### 1. Guidance before action
- feedforward controls
- short map-like instructions
- architecture docs
- explicit plans
- feature lists
- templates and skills

### 2. Correction after action
- tests
- linters
- structural checks
- browser-based verification
- AI review / evaluator agents
- recurring cleanup tasks

### 3. Continuity across sessions
- progress logs
- commit history
- feature list artifacts
- initializer agent outputs
- context resets

### 4. Control of autonomy
- approval policy
- human-in-the-loop checkpoints
- classifier-mediated approvals
- machine-c

## NotebookLM Podcast用メモ

- まず今日の全体トレンドを話してから、重要ソースを3本に絞って深掘りする。
- ソース単体の紹介で終わらせず、既存KBの概念や地図がどう更新されたかを会話に含める。
- 最後に、明日以降の調査問いを2〜3個提示する。
