# エージェントの「会社の記憶」は、保存より訂正が難しい

2026年10月26日 JST / KB日次読み物

「エージェントに社内文書を読ませる」と「エージェントが頼れる組織の記憶を持つ」は違う。前者は検索の問題、後者は出典、権限、有効期限、訂正の問題だ。この記事はKBの [[context-graph-and-company-brain]] マップを、KarpathyのLLM Wiki、Google CloudのOpen Knowledge Format（OKF）、CognitionのAgent Memory Repoの一次資料と照合して整理したもの。各提案は相互運用の実証ではなく、設計の比較である。[1][2][3][4]

## まず、出典から編集可能な知識を作る

Karpathyの個人KB構想では、原資料を`raw/`に残し、LLMが要約と相互リンクを備えたMarkdownのwikiへ「コンパイル」する。人間は原典と編集済みページを行き来でき、生成した報告も戻して蓄積する。[1] 重要なのはベクトル検索を否定することではなく、よく使う知識を毎回一から発見せず、検査可能な形に編んでおくことだ。

Google Cloudが発表したOKF v0.1は、Markdown、前付けメタデータ、リンクからなる知識束の交換形式を提案する。必須の`type`を除き、各ドメインのモデルや節立てには余地を残す。Googleは参照用の生成器・可視化器も示すが、これだけで組織間の普及や、古い事実の自動訂正まで証明されたわけではない。[2]

## 「見つかる」と「今使ってよい」は別の質問

KBの文脈グラフ・会社の記憶マップは、Markdown wikiを人がレビューできる編集面、関係グラフを時点・権限・決定経緯の問い合わせ面として区別する。[3] 例えば「A社の請求ルール」を見つけても、そのルールが今日も有効か、当該担当者に見せてよいか、誰の承認で変わったかは、類似検索だけでは決められない。これはマップからの設計上の推論であり、特定製品の必須構成を意味しない。

CognitionのAgent Memory Repoは、短い`MEMORY.md`と出典付きの小さな記録をGit上に置き、Dreamingによる整理を提案する。[4] Gitの差分が見えることと、内容が正しいことも別だ。要約された誤りが次のセッションの前提になり、さらに共有メモリへ昇格するなら、元資料へ戻れる経路と、無効化を承認する人が必要になる。[3][4]

## 小さく始めるなら

1. `raw`を不変の原資料、wikiを編集可能な仮説・要約とし、段落から出典に戻れるようにする。[1][3]
2. 記録ごとに「誰に有効か」「いつまで有効か」「確かめた日時」を持たせる。未確認の推論は事実と分ける。[3]
3. 自動整理はまず変更提案に留め、矛盾や失効の検知、レビュー、差し戻しを設計する。検索精度よりも訂正までの時間を測る、というのが本稿の提案だ。[3][4]

## 出典と限界

- [1] Andrej Karpathy, Personal LLM Knowledge Bases（2026-04-02）— https://x.com/karpathy/status/2039805659525644595
- [2] Google Cloud, How the Open Knowledge Format can improve data sharing（2026-06-12）— https://cloud.google.com/blog/products/data-analytics/how-the-open-knowledge-format-can-improve-data-sharing/
- [3] Private KB: `wiki/maps/context-graph-and-company-brain.md` と `wiki/maps/research-os-query-paths.md`。本文中の設計上の推論はこのマップを基礎に再構成した。
- [4] Cognition, Agent Memory Repo — https://cognition.com/agent-memory-repo （KB照合: `wiki/sources/cognition-agent-memory-repo-2026-10-05.md`）。自動整理の正確性は独立に評価していない。

この記事は組織の知識基盤の設計上の比較であり、OKFの普及率、Cognition製品の正確性、特定の検索方式の優劣を示す実験結果ではない。
