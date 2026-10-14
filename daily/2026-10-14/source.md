# 夜間に走るエージェントは、誰が「採用しない」を決めるのか

2026年10月14日公開。Googleが2026年10月13日に公開したADK Pythonの最適化事例を、非公開KBの `wiki/maps/coding-agent-harness-patterns.md` と `wiki/maps/agent-deployment-gates-and-operational-risk.md` の観点から読み直す。ここだけで読めるよう、事例の条件と限界を明記する。

## 要点
Googleのチームは、約20.5万行・約800ファイルの `google/adk-python` でGemini 4 Argonを夜間に約11時間動かし、PRで6つの性能改善を提案させた。採用したのは、セッション履歴をコピーする前に絞る変更と、重いパッケージを必要時まで読み込まない変更の2つ。残り4つは保守者が却下した。[1] エージェントが「6案を作った」ことより、人間が危ない4案を見分け、未マージPRを安全に削れたことが重要だ。

## 指示を足す前と後
最初の約2時間の試行はカスタムのリポジトリ規約なしでもボトルネックを見つけた。しかし、公開JSONスキーマを変えかねない認証モデルへのフック、mockの端ケース漏れ、216件の近傍テストだけの実行などが残った。2回目は `.agents/skills` に保守規約を置き、Antigravityの `/goal` で目的と「PRは開くがマージしない」を維持。16,892件の公開テストを実行した。[1]

これは、一般にスキルを置けば無人運用が安全になるという証明ではない。ADK固有の規約、テスト、保守者の判断がセットになった事例だ。非公開KBのハーネス・マップは、長時間の実行にも「読める制約」「動作の検証」「人へのエスカレーション」を別々のゲートとして設計する。[2][3]

## なぜ4案を落としたか
却下された案には、ガベージコレクション後に古いデータを返しうる弱参照ベースのキャッシュ、OpenTelemetryの非公開属性への依存、エンドツーエンドで効果のない複雑な整形、合成ベンチだけを速める索引があった。[1] ベンチの数字だけで採否を決めず、公開APIとの互換性、将来の保守性、実際のユーザー経路を確認した。

Google公表のホールドアウト計測では、長い会話でメモリ内セッション準備のオーバーヘッドが約40%低減、`import google.adk`が21%高速化。一方で新しいプロセスから初回リクエストまでの時間はほぼ横ばい。前者は `InMemorySessionService` に関する改善で、外部DBなど別のセッションストアの読み取り速度まで改善したとは言えない。[1] これは開発元の条件付き計測であり、他社のコードベースでの再現値ではない。

## 現場で試すなら（筆者の提案）
夜間タスクは、公開APIを変えない・既存テストを実行する・ホールドアウトの性能指標をPRへ書く・自動マージしない、という四つの条件を先に明文化する。翌朝は改善率だけでなく、却下した案と理由をレビュー記録に残す。動作確認を通っても運用上の危険が残るため、デプロイ前後のゲートは別に置く。[2][3]

## 限界と出典
事例はGoogleの自社報告であり、ベンチの外部再現や他のプロジェクトへの一般化は未確認。性能改善と安全性は別の指標。ロボット制御向けの同日発表[4]も、シミュレーションと実機の検証境界という別の課題を提示する。公開ページにはXブックマークの原文を含めていない。

[1] Google Developers Blog, “Optimizing a 200,000-line Python codebase overnight with Gemini 4 Argon” (2026-10-13): https://developers.googleblog.com/optimizing-a-200000-line-python-codebase-overnight-with-gemini-4-argon/

[2] 非公開KB `wiki/maps/coding-agent-harness-patterns.md` および `wiki/sources/google-argon-adk-overnight-2026-10-13.md` （2026-10-14更新）。

[3] 非公開KB `wiki/maps/agent-deployment-gates-and-operational-risk.md` （変更前検査・デプロイ前検証・人の承認・運用後観測を区別）。

[4] Google Developers Blog, “Gemini 4 Argon for Robotics” (2026-10-13): https://developers.googleblog.com/gemini-4-argon-for-robotics/
