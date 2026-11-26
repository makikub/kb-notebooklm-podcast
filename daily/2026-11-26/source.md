# 速く作るより、確かに直す — 本番API移行と週100 PRの検証設計

2026-11-26｜AIエージェント運用・検証

## 何が起きたか
AnthropicはMessages APIをPythonからRustへ移した実践を2026年11月25日に公開した。Claudeが主要経路の初版を約1週間で書く一方、難所は本番挙動との等価性だった。約700の結合テストを移植しても100超のassertionが弱くなり、4月にはテスト約98%通過なのに本番入力の一致は約4分の1。[^anthropic]

別の現場でWill Larsonは、11月9日の週に115 PRを本番へ出したと自己報告した。連続7日の最高170件の内訳は約150の本番PRと約20の内部ツール等で、暦週の数字と区別が必要だ。彼は承認の速さより、検証内容が曖昧で承認しづらいPRを次の制約として挙げる。[^larson]

## どう検証したか
Anthropicは既存の本番APIを照合器にした。リクエストでモデルを二度呼ばず、一度の出力をRust側へ再生する。これで非決定的な応答の比較や重複課金を避け、段階ごとの差分をfingerprintで束ねる。顧客のリクエスト・応答本文を読まない設計も明記した。agentは隔離されたsandboxで仮説を試し、回帰テストを追加。人のPRレビューを経てから、shadow化した本番トラフィックで修正を再検証する。[^anthropic]

差分が消えれば十分、ではない。ツール説明文を一時ファイルに固定する案は出力一致を満たしたが、本来必要なサービス呼び出しを回避するため人が却下した。レビューの判断はメモ、ルール、テスト、lintへ反映された。[^anthropic]

Larsonの記事はCI/CD、古いKB文書の整理、構造化issue、クラウドharness、検証ファイル、仕事の棚卸しの順に制約が移ったと述べる。内部MCPではagentが変更案を作れても、承認は役割を持つ人のUIに残した。[^larson]

## 実務への読み替え（編纂上の推論）
1. PR数だけでは成果を測れない。検証の証拠、障害率、レビュー時間、顧客価値を別々に追う。
2. 速い内側の検証と、遅い本番比較を分ける。人は単なる出力一致でなく、修正方針と権限境界を判定する。
3. 差分の記録が個人情報を漏らさないかも、検証設計そのものとして試す。

Anthropicが報告するCPU/リクエスト約70%減と初回トークン中央値約20%短縮は同社の内部観測で、他のAPIでの再現性は未確認。LarsonのPR件数や品質改善も本人報告であり、独立評価ではない。[^anthropic][^larson]

## 参照元
[^anthropic]: Anthropic Engineering, “Migrating our Messages API to Rust” （2026-11-25） https://www.anthropic.com/research/migrating-api-to-rust
[^larson]: Will Larson, “Shipping 100+ PRs to production in a week” （2026-11-22） https://lethain.com/passing-100-prs-in-a-week/ 。発見元は本人のX投稿 https://x.com/Lethain/status/2124590238031094043

## KBでの接続
- `wiki/maps/eval-review-reliability.md` — 評価レイヤーとレビューの役割
- `wiki/maps/coding-agent-cognitive-debt-and-review-capacity.md` — throughputと理解・承認の容量
- `wiki/sources/anthropic-messages-api-rust-2026-11-25.md`、`wiki/sources/lethain-100-prs-verification-x-2026-11-26.md` — 各根拠の制約
