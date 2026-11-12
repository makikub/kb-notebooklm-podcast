# agentの判断を、承認できる画面に変える

2026-11-12 JST / Googleの一次情報とKBのマップを根拠にした独立して読める解説。発表内容と運用上の推論を区別する。

## 判断と画面は別の部品になった

Googleは11月11日、Gemini Decisions APIを発表した。`gemini-decision-1`はテキスト、画像、音声、動画、PDFを受け、yes/no・複数選択・順序付きスコアの問いに確率を返す。1回の入力で最大1,000問を評価でき、モデルルーティングやポリシーチェックなどの有界な判断を想定している。[1] Googleが示す150–250msの応答と入力100万トークン当たり0.10ドルは発表時の条件であり、任意の実務データでの保証ではない。

同日、生成UI用のA2UI 1.0も初の安定版となった。agentが表示内容を記述し、アプリが登録済みのネイティブ部品で描画する。双方向関数呼び出し、アクセシビリティ、拡張メタデータが追加された。Web・Flutter・iOS向けレンダラーが紹介されている一方、Android Jetpack Composeの1.0対応は今後の予定だ。[2]

## 「判断した」と「実行してよい」は違う

ここからはKBのagent harness control taxonomyとapproval policy mapsに基づく*運用上の推論*である。Decisions APIで候補を絞り、A2UIで根拠と選択肢を表示し、送信・変更・購入などの副作用前に人の承認を求める構成なら、判断・説明・実行の境界を分けやすい。しかしAPIの信頼度だけで自動実行を許可するのは飛躍だ。自分の業務データで校正を測り、権限、取り消し可能性、監査ログを別途設計する必要がある。

A2UIの発表は「病欠の朝」の例で、複数アプリへの依頼をまとめて提示し、確認まで何も送らない体験を説明する。[2] これはプロトコル自体がすべての副作用を防ぐという証明ではない。実際の確認と送信の境界は実装ごとに検証したい。

## 実装前に確かめる三点

1. 判定: 曖昧な入力で信頼度が校正されているか。低信頼ならどこへ戻すか。
2. 表示: 使えるコンポーネントと表示される根拠を誰が管理するか。端末ごとの1.0対応差も確認する。
3. 実行: 人の確認が実際の副作用より前にあるか。監査・取り消しは可能か。

## 原典
- [1] [Google — Gemini Decisions API: Fast, calibrated multimodal decisions](https://blog.google/innovation-and-ai/technology/developers-tools/gemini-decisions-api/)（2026-11-11、公式ブログ）
- [2] [Google Developers Blog — A2UI 1.0](https://developers.googleblog.com/a2ui-10-build-delightful-fast-reliable-agentic-experiences/)（2026-11-11、公式ブログ）

KB内の根拠経路：`wiki/maps/agent-harness-control-taxonomy.md` と `wiki/maps/approval-policy-patterns-and-escalation.md` → `wiki/sources/google-gemini-decisions-api-2026-11-11.md` と `wiki/sources/google-a2ui-1-0-2026-11-11.md`。
