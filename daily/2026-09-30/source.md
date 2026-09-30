# Dotsの「読み取り専用」は、操作全体の無条件な安全ではない

2026年9月30日｜OpenAIの公式資料から、継続エージェントの権限境界を読む

## まず事実：Dotsは何をするか
OpenAIは9月29日、GPT-6 Astraを使う継続エージェント「Dots」を発表した。各dotは独立したクラウドPCを持ち、ユーザーが接続したアプリやブラウザを使って作業できる。最初は対象地域のProとBusiness Premiumへ順次展開し、Enterprise等のベータは管理者の有効化が必要だ。これは全ユーザーへの一律提供ではない。[OpenAI製品発表](https://openai.com/index/introducing-dots/)

## 調査と操作は別の権限境界
Dotsの「proactive research」は、接続済み情報を探して非公開メモを作るバックグラウンド工程だ。OpenAIの安全説明では、この工程のツールはコード上で読み取り専用に制限され、直接のメッセージ送信、接続アプリの変更、ブラウザ・デスクトップ操作はできない。一方、その調査から生まれた後続のアクションは、通常のルールとチェックを経て実行されうる。「調査が読み取り専用」から「dotの全作業が読み取り専用」とは言えない。[OpenAI安全説明](https://openai.com/index/how-we-build-safety-security-and-privacy-into-dots/)

OpenAIはアプリ権限、Custom Rules、Activity Viewと、操作直前の独立したAuto-reviewを説明する。Auto-reviewは計画した操作と指示・ルール・必須安全条件を照合し、許可、確認要求、代替手段への移行、または停止につなげる。送信やファイル変更などはこの仕組みの対象となるが、すでに与えた承認が操作をカバーする場合は新しい確認なしで進むこともある。恒常的に「書き込みのたびに人間が確認する」設計ではない。[OpenAI安全説明](https://openai.com/index/how-we-build-safety-security-and-privacy-into-dots/)

## 接続を切ることと、忘れさせることは違う
接続アプリを外すと、その経路からの新しい情報共有は止まる。しかしOpenAIは、dotがすでに学んだ情報は自分の文脈に残ると明記する。既知情報まで消したいときは、アクセス解除だけで済ませず、dotの文脈リセットや保存情報の取り扱いを別途確認する必要がある。これは公式仕様からの運用上の推論であり、接続解除そのものの削除効果を主張するものではない。[OpenAI安全説明](https://openai.com/index/how-we-build-safety-security-and-privacy-into-dots/)

## 導入前に検証する小さな表
1. **読み取り**：どのアプリ・フォルダ・デバイスが見えるか。proactive researchに許す対象を絞れているか。
2. **書き込み**：メッセージ、共有、ファイル変更、購入のどこに承認・Auto-review・人間への引き継ぎがあるか。既存の承認が何をカバーするか。
3. **保持**：接続解除後も残る文脈をどう点検・リセットできるか。
4. **検証**：一つの代表タスクで承認前後の画面と成果物を読み戻し、意図しない操作がないか確かめる。

この四分割はKBの承認ポリシー、エージェント運用ゲート、評価・レビューのマップを元にした*編集上の整理*。OpenAIの製品保証や一般的な安全性の実測値ではない。ベンダー自身も誤りの可能性を明記している。[OpenAI製品発表](https://openai.com/index/introducing-dots/) / [OpenAI安全説明](https://openai.com/index/how-we-build-safety-security-and-privacy-into-dots/)

## 同日の関連発表（主題とは分ける）
OpenAIはGPT-6.1 Solも公開した。API標準料金は100万トークン当たり入力$2、キャッシュ入力$0.10、出力$10。従来Solからキャッシュ入力が半額だが、通常の入力・出力単価は同額だ。モデル仕様ではResponses APIのツール呼び出しに対応し、Chat Completionsではツール呼び出しに対応しない。Dots自体はAstra駆動であり、このSolの料金をDotsの課金として適用してはならない。[GPT-6.1 Sol発表](https://openai.com/index/introducing-gpt-6-1-sol/) / [モデル仕様](https://developers.openai.com/api/docs/models/gpt-6.1-sol)

DevDay総覧は対象プランでChatGPT利用枠を16社の参加ツールへ広げると説明した。CognitionのDevinが含まれるが、利用枠と参加条件があるため「無制限利用」とは読めない。[OpenAI DevDay総覧](https://openai.com/index/devday-2026-recap/)

## 原典
- [OpenAI: Introducing dots（2026-09-29）](https://openai.com/index/introducing-dots/)
- [OpenAI: How we build safety, security, and privacy into dots（2026-09-29）](https://openai.com/index/how-we-build-safety-security-and-privacy-into-dots/)
- [OpenAI: Introducing GPT-6.1 Sol（2026-09-29）](https://openai.com/index/introducing-gpt-6-1-sol/)
- [OpenAI API: GPT-6.1 Sol model specification](https://developers.openai.com/api/docs/models/gpt-6.1-sol)
- [OpenAI: DevDay 2026 Recap（2026-09-29）](https://openai.com/index/devday-2026-recap/)
