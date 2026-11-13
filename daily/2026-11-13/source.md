# 速いモデルを選ぶ前に、成功タスク当たり費用を測る

2026年11月13日 / KBの読み物

## 結論
モデルの入力単価や速度だけでは、agent運用の費用は決まらない。失敗、やり直し、検証、人のレビューまで含めて「成功タスク当たり費用」を測る。これは既存KBの[AI導入ROI map](https://github.com/makikub/knowledge-base-llm/blob/main/wiki/maps/ai-adoption-roi-and-capability-investment.md)に基づく運用上の提案であり、特定モデルの優劣を保証するものではない。

## 新しい一次情報
Googleは11月12日、Gemini 4 Hydrogenを日常的なcoding/agent実行向けモデルとして発表した。Gemini API、AI Studio等で提供し、発表時点のAPI価格は入力100万token当たり$1.50、出力$7.50。AntigravityのOrchestratorは同一セッション内でCarbonとHydrogen等を切り替える。GoogleはTerminal-Bench 4.0でCarbonに近いタスク成功率を保ちながら、平均quota 24%減・完了19%高速化と報告する。ただしベンダーの測定値で、個別の開発現場の節約額ではない。原典：[Google公式発表](https://blog.google/innovation-and-ai/models-and-research/gemini-models/introducing-gemini-4-hydrogen/)。

## 読み方を変える三つの問い
1. **仕事を分けられるか。** 設計・難しい調査と、編集・テスト・検証のような実行を分け、どの役割にどのモデルを使ったかを記録する。
2. **単価以外も数えたか。** token費用だけでなく、再試行回数、実行時間、失敗率、レビュー時間を同じタスク単位で集計する。KBには[Googleの小規模なモデル振り分け実験](https://github.com/makikub/knowledge-base-llm/blob/main/wiki/sources/google-cost-per-task-2026-11-03.md)も記録している。その実験では、ルータを足すことが常に得とは限らなかった。
3. **検証を省いていないか。** 速く生成した差分も回帰テストや人の判断を必要とする。[agent deployment gatesのmap](https://github.com/makikub/knowledge-base-llm/blob/main/wiki/maps/agent-deployment-gates-and-operational-risk.md)が整理するように、pre-merge検査と本番の観測を別々に設ける。

## 小さな実験
同じ実務タスクを複数件選び、固定モデル運用と振り分け運用を比較する。成功の定義を事前に固定し、token・再試行・所要時間・レビュー工数を記録する。Googleの発表値をそのまま期待値にせず、自社タスク分布に対して再現する。

## 根拠と限界
- 一次情報：[Google — Introducing Gemini 4 Hydrogen](https://blog.google/innovation-and-ai/models-and-research/gemini-models/introducing-gemini-4-hydrogen/)（2026-11-12）。価格・提供範囲・Orchestratorの発表値。
- KB map：[AI Adoption ROI and Capability Investment](https://github.com/makikub/knowledge-base-llm/blob/main/wiki/maps/ai-adoption-roi-and-capability-investment.md)；[Agent Deployment Gates and Operational Risk](https://github.com/makikub/knowledge-base-llm/blob/main/wiki/maps/agent-deployment-gates-and-operational-risk.md)。概念整理であり新たな測定結果ではない。
- 未確認：自社ワークロードでの効果、正式な提供条件の変更、独立評価。private KBへのリンクは閲覧権限がある読者のみ開けるため、本文単体で主要な論点と原典を示した。
