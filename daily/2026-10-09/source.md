# HTTP 200の先にある失敗を、誰が見つけるか

## 問い
エージェントがエラーなく動き続けているとき、回答や処理が間違っていないとどう確かめるか。ここでは本番の失敗を発見する観測ループと、止める責任を混同しない。

## 根拠の道筋
1. GoogleのAQuAは会話の最大1,000件を標本化し、所見をクラスタ化して別モデルが最大3件の全文で検証する。デプロイ時に固定したソースの行へ診断をつなぎ、修正やPRは自動では行わない。32セッションを使った例は参照実装のデモであり、一般化可能な精度ではない。[1]
2. Anthropicの定期エージェント実装は、ソースが読めない日に『新着なし』と報告せず、該当カーソルを保留する。Slackへの投稿を確認して初めて記録を更新する。つまり観測障害と送達障害を別々の状態に置く。[2]
3. Anthropicが10月8日に告知した11月12日発効予定のポリシーは、危険な物理動作を伴う使用で監督者の観察・停止能力と切断時の安全状態を求める。これは品質スコアでは代替できない停止ゲートだ。[3]

## 統合（推論）
本番運用には、(A)健康状態の監視、(B)会話内容の評価と根拠確認、(C)人間が介入できる停止・送達確認の三層が要る。AQuAは主にB、定期エージェントのカーソル設計はCの報告整合性、ポリシーは高リスクCの要件を示す。各社の製品を組み合わせれば自動的に保証されるわけではない。[1][2][3]

## 実務の最初の一歩
『API成功だが内容を誤る』『情報源の読取失敗』『通知結果が不明』を別テストケースにし、評価結果・ソース版・最後に確認した送達IDを残す。個人情報を含む会話の標本化は権限と保管期間を先に決める。[1][2]

## 限界
AQuAの品質改善率や費用はここでは未測定。Anthropicポリシーの適用判断は告知だけでなく全文を確認する必要がある。ブラウザ履歴の外部送信など別のデータ境界も残る。[3][4]

## KBでの位置づけ
- `wiki/maps/agent-deployment-gates-and-operational-risk.md`：ゲート全体像
- `wiki/maps/eval-review-reliability.md`：独立評価の構成
- `wiki/navigation/operations.md`：長時間実行と送達の参照経路

## 原典
[1] https://developers.googleblog.com/the-outer-loop-insights-first-an-ambient-quality-agent-that-diagnoses-your-production-agent/
[2] https://claude.dev/blog/building-effective-agent-automations/
[3] https://www.anthropic.com/news/2026-usage-policy-update
[4] https://github.com/ThariqS/ai-newtab
