# 見つけるAIの次に必要な、直すためのゲート

## 問い
AIが脆弱性や修正候補を速く発見できるようになったとき、発見を実際のリスク低減へどうつなげるか。

## 根拠の道筋
1. KBの `wiki/maps/agent-deployment-gates-and-operational-risk.md` は、機械的な変更前検査、実環境の検証、人へのエスカレーション、運用後の観測を分ける。[1]
2. Anthropicは2026年10月8日、重要インフラ向けCIDPと、OSSプロジェクトに無料で定期スキャンするOSS Scannerを発表した。OSS Scannerの報告はモデル生成で、人による送信前レビューなし。誤った深刻度などを含み得ると明記した。真陽性率90%超は同社の予測であり、検証済み実績ではない。[2]
3. KBの `wiki/maps/approval-policy-patterns-and-escalation.md` は、自動実行・助言的レビュー・阻止するレビュー・人だけが実行する工程を区別する。[3]

## 統合（推論）
発見コストが下がるほど、保守者の検証容量がボトルネックになり得る。そこで発見数ではなく、再現確認・誤検知判定・優先順位・修復の各段階でどこを止め、誰が判断するかを運用設計に入れる。[1][2][3] CIDPやOSS Scannerで社会全体の被害が減ったと断定するには、現時点の発表だけでは不足する。

## 実務の最初の一歩
対象リポジトリの保守者に、1週間に確認できる報告数と修正を出せる件数を確認する。その上で「再現可能性」「影響範囲」「修正案のテスト」の三点を満たした報告だけを優先キューへ送り、誤検知と修復までの日数を記録する。これは提案であり、公式の推奨手順ではない。

## 限界
情報源は当事者の発表。無償スキャンの対象、利用条件、精度の実測値を一般化しない。OTでは設備の停止や変更に固有のリスクがあるため、OSSの運用をそのまま転用できない。[2]

## KBでの位置づけ
- `wiki/maps/agent-deployment-gates-and-operational-risk.md`：リリース前後の検証・停止
- `wiki/maps/approval-policy-patterns-and-escalation.md`：自動承認と人の判断
- `wiki/sources/anthropic-cyber-mission-2026-10-08.md`：今回の公式一次資料

## 原典
[1] KB `wiki/maps/agent-deployment-gates-and-operational-risk.md`
[2] https://www.anthropic.com/news/anthropic-cyber-mission
[3] KB `wiki/maps/approval-policy-patterns-and-escalation.md`
