# 速いモデルと長い文脈、その前に確認する境界

2026-11-10 JST / 単独で読めるKB読み物。原典は文末参照。

## 新モデルの性能と利用資格は別の話

Anthropicは2026年11月9日、Claude Fable 5.2とMythos 5.2を発表した。同じ基盤モデルだが、安全対策と利用資格が異なる。Fableは一般に利用できる一方、Mythosはサイバーセキュリティや生命科学の検証プログラムを通じた対象組織向けだ。[1] 「同じモデルだから同じ作業を同じ条件で実行できる」とは読めない。

## トークン単価とタスク単価を分ける

両モデルの発表価格は入力100万トークン当たり8ドル、出力100万トークン当たり40ドル。任意のfast modeはそれぞれ16ドルと80ドルで、生成速度は最大2.5倍と説明される。[1] 標準モードでも前世代より最大30%高速というのは提供元の測定値である。実務では入力・出力の構成、必要なeffort、再試行数、完了までの時間を合わせて「成功タスク当たり」で測るべきだ。最後の一文はKB側の推論であり、発表が自社ワークロードでの節約を保証するわけではない。

## 長文脈の学習技術をAPI上限と混同しない

GoogleはTPU 8txを機密推論向け、8i Maxを巨大な文脈を扱う計算向けとして発表した。[2] 同日のGoogle Cloud記事は、MaxText v0.2.4で長文脈の学習に四つの並列化方式を実装し、特定のLlama 3.1 8BとTPU構成で最大1400万トークンへの拡張を報告した。[3] これは学習系の実験結果であり、Gemini APIや手元のモデルの入力上限が1400万トークンに変わったという意味ではない。

## 導入時の三つの問い

非公開KBの「Agent Deployment Gates and Operational Risk」マップと本日の一次情報を突き合わせると、①利用できるモデルと許可される作業は何か、②成功タスク当たりの費用と遅延はどうか、③学習基盤・推論基盤・API仕様のどこに変更があるか、を別々に確認するのがよい。これは運用上の提案であり、二社の製品を直接ベンチマーク比較した結論ではない。

## 出典とKB経路
- [1] [Anthropic — Claude Fable 5.2 and Mythos 5.2](https://www.anthropic.com/claude-fable-and-mythos-5-2)（一次情報、2026-11-09）
- [2] [Google — TPU 8tx and 8i Max](https://blog.google/innovation-and-ai/infrastructure-and-cloud/global-network/tpu-8i-max-and-8tx/)（一次情報、2026-11-09）
- [3] [Google Cloud — MaxText Context Parallelism](https://developers.googleblog.com/en/announcing-long-context-training-on-tpus-with-maxtext-context-parallelism/)（一次情報、2026-11-09）

非公開KB側の根拠経路: `wiki/maps/agent-deployment-gates-and-operational-risk.md` → `wiki/sources/anthropic-fable-mythos-5-2-2026-11-09.md` / `wiki/sources/google-tpu-8tx-8i-max-2026-11-09.md` / `wiki/sources/google-maxtext-context-parallelism-2026-11-09.md`。製品発表と本稿の推論は区別した。
