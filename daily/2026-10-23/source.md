# 判断は速く、変更は止める——自己修復エージェントの二つのゲート

2026年10月23日 JST / KB日次読み物

AIエージェントが障害に気づき、自分で直す。ここで「何をするか決める」速度と「本番に反映する」権限を混ぜると、速い誤判断も速く本番に届く。2026年10月22日のOpenAIとGoogleの一次資料を、KBの制御分類・デプロイゲートのマップに照らして読む。両社の製品を統合した実証ではなく、設計上の比較である。[1][2][3][4]

## 判定は、答えの型まで限定する

OpenAIはDecisions APIをgpt-6-lunaで一般提供した。テキスト・画像・JSONから、条件の真偽確率、選択肢、ルーブリックに基づくスコアを返す専用APIである。共通入力のキャッシュや最大400問/要求も追加された。公式はResponses API比で「約10倍高速」と説明するが、これは自社の性能説明であり、任意のワークロードの精度・費用を保証する比較結果ではない。[1]

KBの制御分類では、これは推論的な「判定」層に置ける。ただし確率が高いことと、ポリシーを満たすことは別だ。数値の閾値で進めてよい低リスク操作と、独立の検証・承認を要する操作を事前に分ける、というのがここからの設計上の推論である。[3]

## 実行には別の拒否経路を置く

GoogleのProject Chrysalisは、Gemini Agent Platform/ADK、BigQueryを使い、障害時の一時的な緩和策を合成・検証するリファレンス構成だ。記事はAST制約、OPAによるSLAポリシー、Model Armor、Cloud KMS、Binary Authorizationを組み合わせ、永続的なエージェント階層変更にはSREの明示的な承認を要求する。[2]

ここで重要なのは「自己修復できる」という看板より、実行前の機械的拒否と、後戻りしにくい変更での人間の介入を分けたこと。KBのデプロイゲート・マップも、構造検査、実行前の検証、人間へのエスカレーション、本番監視を異なる層として整理している。[4]

## 1.8秒という数字の読み方

Chrysalisの記事はBlack Fridayのキャッシュ障害を模したシミュレーションで初回緩和まで1.8秒、HTTP 5xxが0%になったと報告する。これを実顧客環境での再現性や安全性の実績として読むのは誤りだ。モデル・障害注入・トラフィック条件が異なれば結果は変わる。[2]

実装に移すなら、まず対象操作の権限表、失敗時のロールバック、一時緩和の有効期限、承認画面に示す証拠、障害後の監視を自社の環境で検証する。これは[2]を[3][4]へ対応付けた提案であり、Googleによる標準要件の宣言ではない。

## 出典と限界

- [1] OpenAI, Decisions API documentation / API changelog (2026-10-22) — https://developers.openai.com/api/docs/guides/decisions.md
- [2] Google Developers Blog, Architecting Governed, Self-Evolving AI Agents on Google Cloud (2026-10-22) — https://developers.googleblog.com/architecting-governed-self-evolving-ai-agents-on-gemini-agent-platform/
- [3] Private KB map: wiki/maps/agent-harness-control-taxonomy.md（制御の分類。内容を検証して本文へ再構成）
- [4] Private KB map: wiki/maps/agent-deployment-gates-and-operational-risk.md（運用ゲート。本文は独立して読めるよう再構成）

OpenAIの速度とGoogleのシミュレーション値は各社の主張で、独立評価や相互比較ではありません。
