# 内部MCPを安全につなぐには、ネットワークと「誰の権限か」を分ける

2026年11月23日。Googleが11月20日に公開した実装ガイドは、Gemini Enterpriseから組織内のCloud Run MCPサーバーへ、公開インターネットに露出させずに接続する方法を説明する。[1] これは新モデルの発表ではなく、エージェントが社内データを使うときの経路と権限を設計するための実装例だ。

## 「中に置いた」だけでは足りない
Cloud Runの内部限定ingressを有効にすると、通常の公開経路からの呼び出しは拒否される。Googleの構成はGemini EnterpriseのEgress Agent GatewayからPrivate Service Connectで組織VPCへ入り、Private Google AccessまたはGoogle APIs用PSCを通じてCloud Runへ到達する。Shared VPCのDNSは対象MCPサーバーの完全修飾ドメイン名だけを私設化する。`*.run.app`全体を上書きすると他のサービスの名前解決まで壊す恐れがあるためだ。[1]

## 二つの身元を混ぜない
GoogleはCloud Run IAMでサービス側のID token（`X-Serverless-Authorization`）を検査し、コンテナ側では`Authorization: Bearer`の利用者OAuth tokenを検証する構成を示す。前者は「許可されたGemini Enterpriseから来たか」、後者は「誰の代わりに何ができるか」を問う。ネットワーク到達性、サービスの認証、利用者の認証は代替関係ではない。[1]

## 実務に引く境界（編纂上の提案）
非公開KBの「Private MCP Boundaries」と「Agent Deployment Gates and Operational Risk」は、経路・認証・ツール実行前の承認・事後の検出を別層で整理する。Googleの資料にすべてのMCPツールの権限モデルや承認動作が実装済みと書かれているわけではない。小さな検証では、VPC外からの拒否、許可されないサービスIDの拒否、期限切れの利用者tokenの拒否、DNSの影響範囲を一つずつ確かめたい。外部へ送信するツールなら、さらに送信前の承認と送信後の結果照合を分ける。[1]

このガイドは参照実装と設定手順を示すが、任意の組織の本番環境で安全性を実証するものではない。特にユーザーごとのデータ認可は、実装先のAPIと権限設定で検証する必要がある。

## 原典と編纂元
[1] Google Developers Blog, “How to securely connect internal Cloud Run MCP servers to Gemini Enterprise,” 2026-11-20. https://developers.googleblog.com/en/how-to-securely-connect-internal-cloud-run-mcp-servers-to-gemini-enterprise/

編纂元（非公開KB）: `wiki/sources/google-cloud-run-mcp-2026-11-20.md`、`wiki/maps/private-mcp-boundaries-2026-11-23.md`、`wiki/maps/agent-deployment-gates-and-operational-risk.md`、`wiki/maps/approval-policy-patterns-and-escalation.md`。Xブックマーク原文は転載していない。
