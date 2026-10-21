# AIの承認ゲートは「どこで止めるか」から設計する

2026年10月21日 JST / KB日次読み物

エージェントの安全設計を「人が最後に確認する」の一言に畳むと、実行前に止める必要がある操作まで事後検査に回ってしまう。Anthropicが10月20日にベータ終了を告知したClaude Enterprise向けInference hooksは、組織管理のHTTPSサーバーへ会話を送り、推論前にallow/denyを受け取る仕組みだ。[1][2]

## どの時点で、何を止めるか

公式文書によれば`prompt`は推論前に走る。組織がValidate tool callsを有効にすれば`tool_call`もツール実行前に判定する。期限は既定5秒で、サーバー不達・エラー時は組織が通すか止めるかを選べる。監査を先行させるshadow modeや、対象割合を少しずつ上げる段階導入もある。[2]

KBの承認ポリシー・マップは、ゲートを行為の危険度、確認のタイミング、運用時の例外処理に分ける。[3] これに当てはめると、Inference hooksは「モデルに回答させる前」に組織境界を置く例であり、PRのCIチェックや実行後のCompliance API監査とは目的が異なる。これは公開仕様とKBを合わせた設計上の推論であり、実測の安全効果ではない。

## 網羅しない部分を先に書く

添付は抽出テキストとメタデータで届き、生の画像・ファイルバイトは届かない。画像だけの情報はそのゲートで検査できず、`tool_call`にも対象外の内蔵ツールがある。また対象はClaude Enterprise組織で、Claude PlatformのAPI組織やBedrock/Google Cloud向けではない。[2] 「全入力・全ツールを必ず遮断できる」と言い換えないことが重要だ。

## 次の小さな設計実験

導入を検討する組織なら、最初に「止めたい機密データの型」「画像や対象外ツールの別の制御」「判定サーバー不調時のfail-open/closed」「誤検知を測るshadow期間」を一枚に整理する。まずログのみで観測し、遮断する範囲を狭く決めてから進める。これは運用上の提案であり、Anthropicによる効果保証ではない。

## 出典と限界

[1] Anthropic, Claude Platform release notes, 2026-10-20: https://platform.claude.com/docs/en/release-notes/overview 〔ベータ終了の一次告知〕

[2] Anthropic, Inference hooks documentation: https://platform.claude.com/docs/en/manage-claude/inference-hooks 〔適用範囲・例外・障害時設定の一次仕様。実運用での遮断精度は示さない〕

[3] KB map, `wiki/maps/approval-policy-patterns-and-escalation.md`（非公開KB内の承認ポリシー整理。ここで必要な分類は本文に記載した。一次の性能測定ではない）
