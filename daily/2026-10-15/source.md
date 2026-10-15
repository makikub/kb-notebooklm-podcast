# トレースが見えても、キャンペーンは見えない — 定期AIエージェントの監視を三層に分ける

2026年10月15日｜公開用読み物ソース

## 要点

AIエージェントの「監視」は単一の機能ではない。何をしたかを追う**観測**、その連続した行動が目的にかなうかを確かめる**評価**、危険なら止める**制御**を別々に設計する必要がある。トレースが出力できても、誤った判断を自動で検知・停止するとは限らない。

## 10月14日の一次情報

AnthropicはClaude Platform release notesで、Messages APIリクエストとClaude Managed AgentsセッションのOpenTelemetry exportをベータ公開したと記した。SDKはPython、TypeScript、C#、Go、Java、PHP、Rubyでspanを出し、API側はClaude ConsoleでOpenTelemetry destinationを設定する。同じ更新には、Claude Platform on AWSでManaged Agentsのscheduled deploymentsが利用可能になったとある。ただしリリースノートはトレースの精度、保存範囲、品質向上を実測したものではない。[1]

同日のAnthropicの選挙対策報告は、局所判定の限界を別角度から示す。外部のISDとMcCain Instituteとのテストでは、単独の有害依頼は拒否できても、個々には無害に見えるタスクへ分割された悪用キャンペーンを見逃し得た。Anthropicは多段階の悪用を識別する分類器を追加したと説明する。これは選挙ユースケースでの同社報告であり、一般のエージェント監視にそのまま同じ性能を当てはめられない。[2]

## 読み方と実装への翻訳

1. **観測**: ジョブID・実行時刻・ツール呼び出し・結果を追跡可能にする。ログやspanの存在は、正しさの証明ではない。[1]
2. **評価**: 単一ステップの拒否率だけでなく、複数ステップを通した行動の組み合わせをレビューする。異なる目的の小さな操作が悪い成果へ収束しないかを見る。[2]
3. **制御**: 送信、公開、削除、権限変更などには独立した停止・承認ゲートを置く。観測基盤が異常を示しても、ゲートがなければ作業は止まらない。これはKBの運用リスク・評価マップからの設計上の推論。[3][4]

## 定期ジョブの最小チェック

- 入力源が読めなかったとき、0件と記録せず失敗・部分取得を区別する。
- 出力の根拠と実行対象を照合し、完了は対象システムで読み戻す。
- 高影響アクションは観測とは別に承認または停止ゲートを置く。
- トレースに個人情報や認証値が混じらないか、収集範囲と保存先を事前に確認する。

このチェックは特定ベンダー機能の保証ではなく、既存KBマップと今回の発表から組み立てた運用案である。

## 出典と対応関係

[1] Anthropic, *Claude Platform release notes*, 2026-10-14: https://platform.claude.com/docs/en/release-notes/overview
[2] Anthropic, *Preparing for the 2026 US midterms*, 2026-10-14: https://www.anthropic.com/news/2026-us-midterms
[3] Private KB, `wiki/maps/agent-deployment-gates-and-operational-risk.md`（事前制約、デプロイ前検証、人間へのエスカレーション、事後観測の整理）
[4] Private KB, `wiki/maps/eval-review-reliability.md`（決定論的チェック、独立評価、トレースからの改善）

制限：OpenTelemetry exportはベータ。選挙対策の数値や検知能力はAnthropicによる報告であり、本稿の定期ジョブへの実証結果ではない。Private KB原文や個人ブックマーク投稿はこの公開ページに含めない。
