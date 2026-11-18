# AIエージェントの費用を、三つの境界に分けて考える

2026年11月18日公開。単に「安いモデルを選ぶ」だけでは、エージェントが動く費用は管理できない。誰が待てるのか、誰に請求されるのか、何を購入してよいのかを別々に決める必要がある。ここでは11月17日に各社が公開した一次情報をつなぎ、導入前に確かめるべき点を整理する。

## 1. 実行の時間と単価：OpenAI
OpenAIのAPI changelogはGPT-6.2 Astra（高度な推論・コーディング向け）とSol（日常のコーディング・エージェント向け）を追加した。両方ともResponses APIとChat Completionsを利用できるが、ツール呼び出しにはResponses APIが必要だ。同日の別項目では、Responses APIのbackground completionに2時間・8時間の待機枠をpublic betaで追加し、モデルのトークン料金をStandard比でそれぞれ30%・40%低くすると説明している。

これは「すべての仕事が安くなる」ではない。対話中の即時回答と、翌朝までに終わればよいバッチを分けると、待ち時間をコストへ変換できる。期限超過時の再試行や、対象モデル・実際の総額は別に測る必要がある。

原典: https://developers.openai.com/api/docs/changelog （2026-11-17の2項目）

## 2. 請求先と上限：Anthropic
AnthropicのPlatform release notesはLinked billingのベータを告知した。アプリ利用者が自分のClaude組織を接続し、`/v1/messages`または`/v1/chat/completions`の各リクエストに`billing_policy`を設定して支払者を選べる。顧客はClaude Consoleでそのアプリの支出上限を設けたり、連携を解除したりできる。対象はAnthropicへ直接API料金を支払う組織と明記されている。

ここで変わるのはモデルの速度ではなく費用の帰属だ。サービス提供者が全利用料を負担する設計と、顧客の組織が引き受ける設計では、予算の承認者も失敗時の説明責任も違う。ベータの対象資格、上限到達時の挙動、監査ログは実装前に確認したい。

原典: https://platform.claude.com/docs/en/release-notes/overview （2026-11-17）

## 3. 実世界の支出と承認：Google
GoogleはGemini TasksをGemini 4 Hydrogenで米国、日本などに無料展開すると発表し、より高度な機能は米国から段階提供するとした。公式記事には電話予約、Google Pay経由の購入、Google Password Managerへの許可付きアクセスなどの例がある。購入時には確認または事前承認を求め、支出上限も設定できるという。これらの実例は提供元の説明であり、独立した成功率の測定ではない。

タスク実行の料金が無料でも、タスクの結果として商品やサービスを購入すれば別の支出が起こる。プロンプトへの同意と決済への同意を混同しない。予算上限、購入前の人間の確認、利用する外部アプリごとの権限を分離することが重要だ。

原典: https://blog.google/innovation-and-ai/products/gemini-app/tasks-in-gemini-free-new-features/ （2026-11-17）

## 小さく試すなら
一つの実務タスクを選び、(1)完了期限と最大トークン費用、(2)請求先と月額上限、(3)外部購入の許可上限と人間の承認点をそれぞれ明文化する。初回は購入操作を行わず、見積もりと停止条件だけを検証する。各社の公表値や製品説明を自社の実績として扱わない。

編纂: `wiki/maps/agent-session-runtime-economics-2026-11-17.md` と `wiki/maps/agent-deployment-gates-and-operational-risk.md` の「資源・行動・検証」区分を参照し、上記の2026-11-17一次情報で更新。推論部分は節末に分離した。
