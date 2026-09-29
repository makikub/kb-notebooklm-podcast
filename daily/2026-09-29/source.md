# Sonnet 5.5への移行で、最初に確かめるべき「成功したのに失われる状態」

2026年9月29日｜一次資料から読むモデル切替と運用検証

## 新モデルの数字より、移行の前提を確認する
Anthropicは9月28日、Claude Sonnet 5.5を公開した。Claude API、Amazon Bedrock、Google Cloudなどから提供される。Anthropicの紹介では、Sonnet 5に比べて生成は30%以上速く、タスク当たりの費用は最大30%低い。**入力$2、出力$10、キャッシュ読み取り$0.20／100万トークンというAPI単価は、Sonnet 5と同額**だ。費用差は少ないトークンで同じ作業を終えたという同社テストによるもので、料金表が一律に30%値下げされたという意味ではない。[Anthropic製品発表](https://www.anthropic.com/claude-sonnet-5-5)

同社公表のTerminal-Bench 4.0ではSonnet 5.5が70.6%、Sonnet 5が10.3%。ただし、モデルの能力を自社の開発タスクに置き換えるには、ベンチの条件だけでなく実際のレビューと再実行の負担を測る必要がある。複雑でオープンエンドの判断にはOpus 5.5の方が強いとAnthropic自身も説明している。[Anthropic製品発表](https://www.anthropic.com/claude-sonnet-5-5)

## APIの「正常終了」が十分ではないケース
9月28日の[Claude APIリリースノート](https://platform.claude.com/docs/en/release-notes/overview)は、Sonnet 5用コードからの移行で五つの破壊的な差分を列挙した。前段のthinkingを無効にしたい場合は、high以下のeffortで`thinking: {"type":"between_tools"}`を使う。`tool_choice`の`any`/`tool`は400エラーとなる。thinking blockはモデルと会話に結び付けられ、旧computer-use tool `computer_20251124`はClaude API/Google Cloudで受け付けられない。旧Opus 4.8/4.7とSonnet 5はadvisorに指定できない。各条件と代替リクエストは[公式移行ガイド](https://platform.claude.com/docs/en/models/sonnet-5-5/migration-guide)で確認したい。

さらに、Sonnet 5.5が生成したthinking blockを別の、リンクされていないアカウントが送ると、**リクエストは成功しても、そのblockはモデルに渡されず捨てられる**。APIが200を返すだけでは状態の引き継ぎを保証できない。これは上記リリースノートに明示された挙動であり、旧モデルのblockには当てはまらない。[Claude APIリリースノート](https://platform.claude.com/docs/en/release-notes/overview)

## 切替の小さな検証順序
1. 現在のリクエストでthinking設定、forced tool choice、保存したthinking block、computer-use tool、advisorを使っているか洗い出す。該当したものは移行ガイドに沿って修正する。
2. 同じ代表タスクを旧モデルと新モデルで実行し、期待結果・失敗した境界条件・総トークン・所要時間・人間のレビュー工数を比べる。タスク単価とトークン単価を混同しない。
3. アカウントをまたぐ会話再開では、レスポンスの成功だけでなく、保持されるはずの情報が次の出力に反映されたか別途確認する。安全性が重要な操作は承認ゲートも維持する。

この順序はKBの `wiki/maps/eval-review-reliability.md`（評価・レビューの信頼性）と `wiki/maps/ai-adoption-roi-and-capability-investment.md`（AI導入ROI）を踏まえた*運用上の推論*で、ベンダーが一律の移行手順として保証したものではない。KBは非公開だが、このページの事実関係は上記の公開一次資料だけでも追える。

## 今日の関連シグナル（主題とは区別）
ブックマークからは、Cloudflareの[cf CLI発表](https://blog.cloudflare.com/cloudflare-cf-cli-launch/)と、Cognitionの[Devin価格改定投稿](https://x.com/cognition/status/2104633216145436831)も拾えた。前者は操作面の拡大、後者はベンダーが示すモード別価格変更で、いずれもSonnet 5.5の評価結果を証明するものではない。料金条件や独立ベンチは未検証のまま扱う。

## 原典
- [Anthropic: Introducing Claude Sonnet 5.5（2026-09-28）](https://www.anthropic.com/claude-sonnet-5-5)
- [Anthropic: Claude API release notes（2026-09-28の項）](https://platform.claude.com/docs/en/release-notes/overview)
- [Anthropic: Sonnet 5.5 migration guide](https://platform.claude.com/docs/en/models/sonnet-5-5/migration-guide)
- [Cloudflare: Introducing cf（2026-09-28）](https://blog.cloudflare.com/cloudflare-cf-cli-launch/)
- [Cognition公式X投稿（2026-09-28）](https://x.com/cognition/status/2104633216145436831)
