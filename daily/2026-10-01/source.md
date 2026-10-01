# 「100万トークン」を導入可能性と取り違えない：Gemini 4 Argonの評価ゲート

2026年10月1日｜Googleの公式発表とKBのデプロイゲート・マップから読む

## まず何が発表されたか
Googleは9月30日、Gemini 4 Argonを発表した。複雑なコーディング、企業の知識作業、防御的サイバーセキュリティを対象とする新モデルだ。ただし、発表時点の提供先はFairwind Programに参加する信頼されたサイバー防御者。開発者・企業・消費者への一般提供は今後としており、今日誰でもAPIで使えるという意味ではない。[Google公式発表](https://blog.google/innovation-and-ai/models-and-research/gemini-models/gemini-4-argon/)

## 出力上限と価格を、アクセス条件と分ける
記事が述べる「100万トークン」は**1回の軌跡で生成できる出力の上限**（従来64Kから拡張）で、入力コンテキスト長ではない。導入価格は100万トークン当たり入力$2・出力$10、キャッシュ入力は95%割引。記事脚注は導入期間後の価格を$4/$20と記す。長い出力が可能なことも、価格が公表されたことも、現時点の一般アクセスや自社業務での採算を証明しない。[Google公式発表](https://blog.google/innovation-and-ai/models-and-research/gemini-models/gemini-4-argon/)

## 公表ベンチを導入判定へ直結しない
GoogleはDeepSWE v1.1で77.9%、AutomationBenchで51.3%、CWE-bench v1で68%などを示す。これらはまず**ベンダーの公表値**として扱い、独立した自社評価結果に読み替えない。同社はRustへの大規模移行例にも言及する一方、そのような重要な変更には自動・手動の監査やエミュレーション検証を実施中と説明する。能力の高さを主張する記事自体も、検証を省いてよいとは言っていない。[Google公式発表](https://blog.google/innovation-and-ai/models-and-research/gemini-models/gemini-4-argon/)

## 実務の四つのゲート
KBの「Agent Deployment Gates and Operational Risk」マップは、エージェントの生成速度がレビュー能力を超える場合に、事前構造チェック、デプロイ前検証、人間へのエスカレーション、本番後の観測を分ける。これを今回の発表に当てはめると、①利用資格と正式なモデルIDが確認できるまで採用予定に入れない、②限定プレビューでは自社タスクと費用を小さく測る、③セキュリティや大規模変更は人間の承認と独立レビューを残す、④公開後も逸脱・コスト・変更失敗を観測する、の順になる。これは*KBを用いた編集上の提案*で、Googleが保証する導入手順ではない。[KBマップ](https://github.com/makikub/knowledge-base-llm/blob/main/wiki/maps/agent-deployment-gates-and-operational-risk.md) / [Google公式発表](https://blog.google/innovation-and-ai/models-and-research/gemini-models/gemini-4-argon/)

## 今日の周辺差分
Anthropicは`claude-sonnet-4-5-20250929`を9月30日に非推奨とし、APIでの廃止予定を11月30日、推奨移行先を`claude-sonnet-5-5`と示した。新モデルへの期待とは別に、既存システムの移行期限と回帰試験を管理したい。[Anthropic公式廃止予定表](https://platform.claude.com/docs/en/about-claude/model-deprecations)

OpenAIのDecisions APIは公式X投稿で限定プレビューが告知されたが、今回の監視では製品本文・仕様を裏取りできなかった。ニュース一覧が403となったため、同社の新着を網羅したとも主張しない。この話題は未確認のまま本編の確定事実に混ぜない。[OpenAIDevs投稿](https://x.com/OpenAIDevs/status/2105003318917697873)

## 原典と編集根拠
- [Google: Gemini 4 Argon: our next era of frontier intelligence（2026-09-30）](https://blog.google/innovation-and-ai/models-and-research/gemini-models/gemini-4-argon/)
- [Anthropic: Model deprecations（2026-09-30更新）](https://platform.claude.com/docs/en/about-claude/model-deprecations)
- [KB: Agent Deployment Gates and Operational Risk](https://github.com/makikub/knowledge-base-llm/blob/main/wiki/maps/agent-deployment-gates-and-operational-risk.md)（非公開KB。閲覧権限のない読者向けに四層の内容は本文で説明済み）
- [KB: AI Adoption ROI and Capability Investment](https://github.com/makikub/knowledge-base-llm/blob/main/wiki/maps/ai-adoption-roi-and-capability-investment.md)（価格・検証税・不安定性コストの補助的な編集視点）
