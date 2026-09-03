<!-- generated: 2026-09-03T00:20:00Z -->
<!-- primary_topic: wiki/maps/harness-engineering-vendor-comparison.md -->
# Execution Plane Split — Cursor Self-Hosted vs Fairwind Gate

- Date: 2026-09-03
- Theme slug: `harness-engineering-vendor-comparison`
- Primary topic: `wiki/maps/harness-engineering-vendor-comparison.md`
- Purpose: NotebookLM向けの対話用ソース。KBのベンダー比較地図を、Cursor の実行面分割（self-hosted workers）と Google の Fairwind ゲート（CodeMender + Flash Cyber）として読み直す。モデル比較の再話でも、Gemini 発売の再話でも、昨日のオーケストレーションFAQの続きでもない
- News angle: Cursor 2026-09-02 Self-hosted machines（https://cursor.com/changelog/self-hosted-machines と https://cursor.com/blog/self-hosted-machines）。ツール実行は自ネットワーク。エージェントループ／推論／計画は Cursor cloud のまま。My Machines 対 Team Pools。hibernate。sandboxes は AWS Lambda / Coder / Cloudflare / Daytona / Modal / Namespace / Vercel / E2B。computer use は Linux + Mac。Cursor-hosted が既定。同じ日の aside: Google Gemini 3.8 Flash + 3.8 Flash Cyber（https://blog.google/innovation-and-ai/models-and-research/gemini-models/3-8-flash-and-3-8-flash-cyber/）。workhorse は導入価格 $0.75 / $3.75、2026-12-31 まで。2027-01-01 から $1.50 / $7.50。Cyber は Fairwind + CodeMender で trusted defenders にゲート（https://blog.google/innovation-and-ai/technology/safety-security/fairwind-program/）。追加の一行: Anthropic 9/2 background computer use in Cowork / Claude Code（macOS 15+ で背景が既定。Pro/Max。Team / Enterprise は今は無し）（https://support.claude.com/en/articles/14128542-let-claude-use-your-computer-in-cowork と https://x.com/claudeai/status/2095226833293685100）。デスクトップ対 self-hosted 対 Fairwind の一行。核にしない。Cursor の OpenAI 巻き戻しへの一次応答はまだ無い（不在の一行。Cursor の声明は発明しない）。OpenAI は 9/2–9/3 に、既出の Path to Astra / healthcare を超える高信号の API/モデル投下は無い。X bookmarks は今ラン 0（X MCP は needsAuth）。SpaceX.com/updates は JS shell。発射記録は発明しない。昨日の Fable 5.1 / orchestration FAQ は連続の一行まで

## Talking points（3〜5分）

1. 昨日は親と検証とバスだった。今日はワーカーがどこで走るかである。リードは Cursor Self-hosted machines である。Gemini 発売の再話ではない。Fable の再話でもない。
2. KBの問いは「どのモデルが強いか」ではない。実行と制御と許可が、どこに住むかである。
3. 地図が支えるのは、ハーネスは周囲の系である、という収束である。Cursor の軸は、実行を自ネットワークへ移し、ループを cloud に残す。Devin Outposts は、同じ分割を先に書いていた。
4. Google の Fairwind は、もう一つの極である。CodeMender + Flash Cyber を trusted defenders にゲートする。許可はプログラムの門に住む。
5. 巻き戻しへの一次はまだ無い。OpenAI の 9/2–9/3 投下は無い。Anthropic の background computer use はデスクトップ実行の一行。X は 0。主題は動かさない。

## 今日の読み方

knowledge-base-llm の `Harness Engineering Vendor / Practitioner Comparison` は、各ソースがハーネスを何のために組み立て、何を強調するかを並べた地図である。中心命題は単純である。エージェントの質はモデルだけではない。周囲の系である。検証はループに埋めよ。明示の成果物は、暗黙の記憶より強い。長い仕事は分解と連続を要す。

昨日の読み物は、親と検証とバスだった。その列は今日の核ではない。一行の連続に留める。8/28 のハーネス風景も、8/26 の制御分類も、今日は補助である。今日読むのは、実行面である。

Cursor は 9/2、「Self-hosted machines」を changelog に載せ、同日のブログで「Run cloud agents on machines you manage」と書いた。ツール実行は、自ネットワークの内部機械に置く。コードベース、ビルド成果物、秘密は、そちらに残る。エージェントはツール呼び出しを局所で扱う。動くのは実行環境だけである。エージェントループ、推論、計画は Cursor cloud のままである。ツール出力は推論のために Cursor へ戻る。コードを含みうる。トランスクリプトは Cursor が処理し、保存しうる。Cursor は、顧客ネットワークへ入る接続を開始しない。ワーカーは Cursor CLI の `agent worker start` である。外向きの長寿命 HTTPS である。

My Machines は、一台のラップトップか VM を口座へつなぐ。個人の流れである。Team Pools は、チームか企業の名前付きキューである。要求が来れば伸び、切断すれば縮む。プールは一つのリポジトリに縛られない。名前を付け、空いているワーカーが請求を取る。アイドルは hibernate できる。再接続窓の中でフォローアップが来れば、スナップショットを戻す。sandbox は、既にある面に載せる。AWS Lambda、Coder、Cloudflare、Daytona、Modal、Namespace、Vercel、E2B。computer use は Linux と Mac である。デスクトップを見て、Cursor から制御できる。Cursor-hosted の専用 VM は、いまも既定である。

ページが今日のレンズになるのは、分割である。実行は家に残る。ループはベンダーの雲に残る。これは新しいモデルの発表ではない。地図がすでに持っていた実行面の軸が、第一当事者の製品になった、という角である。

同じ日の薄い行だけ置く。Google は Gemini 3.8 Flash と 3.8 Flash Cyber を書いた。Flash は workhorse である。導入価格は $0.75 / $3.75 per MTok。2026-12-31 まで。2027-01-01 から $1.50 / $7.50。Cyber は Fairwind 経由である。CodeMender と組んで、trusted defenders にゲートする。発売の再話にはしない。許可の門として一行置く。追加の一行: Anthropic 9/2 は Cowork / Claude Code の background computer use である。macOS 15+ で背景が既定。Pro/Max。Team / Enterprise は今は無い。デスクトップ対 self-hosted 対 Fairwind の一行である。核にしない。Cursor の巻き戻しへの一次応答は、2026-09-03 時点でも無い。OpenAI は 9/2–9/3 に、既出の Path to Astra / healthcare を超える高信号の投下は無い。X bookmarks は今ラン 0。SpaceX.com/updates は JS shell で本文が取れなかった。発射は書かない。

今日の問いは「3.8 Flash は何点か」ではない。「実行はどこか。ループはどこか。許可はどこか」である。

## 1. 実行は家に残る — ツールは自ネットワークで走る

KBの Cursor 軸は、エージェント先行の作業面と、局所／雲の受け渡しを書いてきた。今日の製品は、その受け渡しを、実行面として固定する。自ネットワークの機械が、作業コピーを持ち、ファイルを直し、コマンドを走らせる。内部のソース管理と内部サービスに、直接届く。カスタムハードウェア、GPU、iOS の Mac、Kubernetes、既存の sandbox、Cloud Agent のビルドに載せにくい OS とパイプライン。公式が挙げる、使うときの条件である。

なぜ効くか:
- 秘密と成果物の位置が、推論の位置と分離して見える
- 「クラウドエージェント」を、全部をベンダー VM に置くことと混ぜない
- 既定は Cursor-hosted のままなので、移す理由を先に書ける

今日の角:
地図の Cognition / Devin 軸は、オーケストレーションと実行の分割を、すでに Outposts として書いていた。Devin Cloud が計画と推論を持ち、セッションごとの Devbox が実行して壊す。ワーカーは外向き HTTPS である。Cursor の self-hosted は、同じ棚の第一当事者版である。新しい分類ではない。実行を家に残し、ループを雲に残す、という角が、製品の既定の隣に並んだ。

対話の種:
「この仕事のツール実行は、誰の機械か。秘密はどこに残るか。内部サービスへ届く必要があるか。」

## 2. ループは雲に残る — 推論を局所にしたことではない

公式は、動くのは実行環境だけだと書く。エージェントループ、推論、計画は Cursor cloud である。ツール出力は戻る。コードを含みうる。トランスクリプトは処理され、保存されうる。アクセス面は、デスクトップ、cursor.com、mobile、Slack、GitHub、Linear のままである。社内では、マージする PR の 60%超を cloud agents が作る、と書く。役割が広がるほど、機械の位置が問題になる、という導入である。

なぜ効くか:
- 「自ホストした」と「推論も家に置いた」を混ぜない
- 爆破半径は、実行面だけ見ても足りない。戻る出力と残る記録がある
- ハーネスの測定とレビュー面は、ループ側に残る。地図の Cursor 軸の、見え方の話である

今日の角:
地図の収束は、質は周囲の系だ、である。実行を移しても、系の全部は移らない。OpenAI 軸の供給面は、change-of-control の時計の上にある。Tab / Auto / Cloud / Background Agents / Automations / CLI / API は Cursor 経由のまま。局所の Chat と Agent だけが、利用者鍵かゲートウェイを取れる。今日の self-hosted は、その供給面への一次応答ではない。不在のまま置く。実行面の話と、モデル供給の話を、一つに書かない。

対話の種:
「自ホストしたのは実行か。推論か。戻る出力にコードが乗るか。記録はどこに残るか。」

## 3. My Machines と Pools — 誰がワーカーを取れるか

My Machines は一台である。個人の流れである。Pools は名前付きキューである。コントローラが要求キューを見て、チームが渡した spawn スクリプトで機械を足す。空いていれば取る。なければ待つ。アイドル時間を過ぎれば、機械はリセットしてプールへ戻れる。ワークスペースを残すこともできる。hibernate は、高い機械を温存しないためのスナップショットである。再接続窓の外なら、新しい機械へ移せる。プールはリポジトリに縛られない。

sandbox の列は、自前の隔離層を一から作らせない、という角である。AWS Lambda、Coder、Cloudflare、Daytona、Modal、Namespace、Vercel、E2B。computer use は Linux と Mac である。必要なデスクトップ一式があれば、クリックし、打ち、画面を撮り、ブラウザを動かす。

なぜ効くか:
- 個人の一台と、チームのキューは、許可の単位が違う
- リポジトリに縛られないプールは、実行面を共有資源にする
- hibernate は、温存コストと、復元時間のトレードオフを製品にする

今日の角:
地図の Trae 軸は、sandbox、quota、policy gateway を、本番の点検表に圧縮する。今日の Pools は、その表の実行面である。Anthropic 軸の環境制御と、MHS の物理安全評価ゲートは、別の門である。装置へ出す前に評価する。Cursor の Pools は、チームのキューへ出す前に、名前と spawn と窓を書く。門の位置が違う。同じ「ゲート」に潰さない。

対話の種:
「これは一台か。名前付きプールか。誰が spawn するか。hibernate の窓は書いてあるか。」

## 4. Fairwind は門である — CodeMender と Cyber の許可面

同じ日の Google は、Gemini 3.8 Flash と 3.8 Flash Cyber を出した。Flash は workhorse である。導入価格は 3.7 と同じ $0.75 / $3.75。期限は 2026-12-31。翌日から $1.50 / $7.50。発売の再話にはしない。見るのは Cyber の門である。

Fairwind は、政府と信頼できる相手向けの、限られたアクセスである。最初の段は、最も進んだサイバー防衛の能力を、trusted な Google Cloud 顧客、政府機関、サイバーの相手に渡す。CodeMender と Gemini 3.8 Flash Cyber を組む。見つけ、検証し、直す。組織のセキュアなクラウドの中で、検証済みのパッチを出す、と書く。3.8 Flash は CBRN とサイバー攻撃へのセーフガードを載せる。3.8 Flash Cyber は、サイバー向けにより緩い緩和である。だから trusted defenders に限る。参加組織は、内部のサイバー、インシデント対応、ペネトレーションのチームにアクセスを限り、多要素認証などを載せる、と書く。650超の相手。Google Cloud の顧客は、公開モデルの CodeMender を Gemini Enterprise Agent Platform で使える、と書く。Fairwind の Cyber とは別の棚である。

なぜ効くか:
- モデルの点数と、誰が走らせてよいかは、別の面である
- ハーネス（CodeMender）とモデル（Flash Cyber）と門（Fairwind）を、一つの発売に潰さない
- 緩い緩和は、能力の話ではない。許可の話である

今日の角:
地図の Anthropic 軸は、Mythos を trusted access に置き、MHS を物理安全評価の後ろに置いた。面ごとに箱が違う。Google の Fairwind は、その棚の今日の行である。Cursor の self-hosted は、実行の位置を顧客へ渡す。Fairwind は、走らせてよい相手を門で限る。どちらも「どのモデルか」ではない。どこに制御が住むかである。ベンチマークの数字は aside に残す。核にしない。

対話の種:
「この能力は、公開の workhorse か。門の向こうの Cyber か。ハーネスは誰のものか。許可はプログラムか。」

## 5. 地図の軸 — 分割は今日始まったのではない

地図の OpenAI 軸は、リポジトリ設計、機械で守る不変条件、相互運用、そして供給面の change-of-control である。Hugging Face の対応は、評価時の隔離、必須の CoT 監視、重大警報の30分停止である。ベンダーのモデル供給は、いまは ToS の制御面である。Cursor 軸は、見え方、受け渡し、Origin、Start from scratch、孤立した下位 VM である。今日の self-hosted は、その受け渡しを、ネットワーク境界まで伸ばす。Cognition 軸は、microVM、スナップショット、warm-pool、Outposts である。計画と推論を雲に残し、実行を捨てられる箱に置く。LangChain は測定。Fowler は語彙。Gota は何を符号化するかの順序。Spillwave は爆破半径。Schmid は OS としてのハーネス。

なぜ効くか:
- 同じ「自ホスト」でも、実行だけ移す系と、推論も家に置く系は、残る記録が違う
- 同じ「ゲート」でも、評価の門と、プログラムの門と、プールの名前は、許可の単位が違う
- ベンダー比較は、点数表ではない。強調する機構の表である

今日の角:
地図の意見の違いは、文脈リセットか、セッション内の middleware か。本番のコーディングか、長いエージェント一般か。ベンチマーク中心か、ワークフロー中心か。今日はその違いを、実行面で切る。Cursor は実行を移し、ループを残す。Google は Cyber を門の向こうに置く。Devin は先に分割を書いていた。新しい軸を足さない。同じ表の、今日の行である。

対話の種:
「比較しているのは点数か。実行の位置か。許可の門か。強調している機構はどれか。」

## 6. モデルを先にしない — 位置を先に名指す

地図の目的は、ベンダー名の議論を、機構の位置の議論に変えることである。実行を家に置けば、秘密は届く。ループを雲に残せば、見え方と推論はベンダー側に残る。プールに名前を付ければ、共有の実行面になる。Fairwind にゲートすれば、緩い緩和は限られた相手に残る。3.8 Flash の導入価格は、workhorse の一行である。Cyber の門を、単価で上書きしない。

巻き戻しへの一次は無い。不在である。声明は補わない。OpenAI の 9/2–9/3 は、既出の Path to Astra / healthcare を超える高信号が無い、という空欄である。投下を補わない。X=0 は、今ランの取得空である。現場の沈黙ではない。SpaceX の発射は書かない。昨日の親とバスは、連続の一行である。再話しない。

今日の角:
「強いモデルを自ホストした」は、地図が支えない文である。自ホストしたのは実行か。ゲートしたのは許可か。ループはどこに残るか。能力の段と、位置の段を、一つに書かない。

対話の種:
「移した面で、残した面を消していないか。門の向こうの能力を、公開の workhorse と同じ棚に置いていないか。」

## なぜ比較地図が部品になるか

- 同じ「クラウドエージェント」でも、実行面とループ面は、住む場所が違う
- 同じ「自ホスト」でも、ツール実行の移動と、推論の局所化は、残る記録が違う
- 同じ「ゲート」でも、プールの名前と、Fairwind のプログラムと、物理安全評価は、許可の単位が違う
- Devin Outposts と Cursor self-hosted は、新しい分類ではなく、同じ分割の二つの行である

KBの言葉では、各ソースが最適化する対象と、強調する機構を先に並べる地図である。昨日のFAQは、誰が次を決めるかの話だった。今日は、実行がどこで走り、ループがどこに残り、許可がどの門に住むかの話である。公式の型は、実行の移動、ループの残留、My Machines / Pools、hibernate、sandbox 列、Linux+Mac の computer use を一次で固定し、Gemini の単価と Fairwind を aside に留め、Cursor の声明と発射と OpenAI の投下を、空欄のまま残す。

## トレードオフ

実行だけ移すと、秘密は家に残る。戻る出力と記録は雲に残る。「自ホスト」の語が、推論の局所化に聞こえる。Pools を共有すると、リポジトリ境界が薄くなる。hibernate の窓を長くすると、温存コストが残る。短くすると、復元が新しい機械になる。Fairwind を発売の再話にすると、門が消える。Cyber の数字を核にすると、許可面がベンチマークになる。巻き戻しの不在を声明にすると、無い文を足す。昨日の親とバスを今日の核にすると、実行面がFAQの続きになる。

だから今日の使い方は、地図を増やすことではない。実行、ループ、プール、門を名指し、Cursor の self-hosted をその上に置く。Gemini 発売の再話にも、Fable の再話にもしない。パートナー引用の sandbox 名を、新しい分類にしない。

## 実務のとりはじめ

大きな基盤は要らない。今日からできる最小セット:
- 自分の面を、ツール実行の位置と、推論／計画の位置に一文ずつ分ける
- 自ホストすると書くなら、移すのは実行か、秘密か、記録か、を先に書く
- 一台なら My Machines、共有ならプール名と spawn と hibernate の窓を一文にする
- sandbox を使うなら、既にある提供者名を書く。自前の隔離層を前提にしない
- サイバーの能力を語るなら、公開の workhorse と、門の向こうの Cyber を分ける
- CodeMender のようなハーネスと、モデルと、プログラムの門を、一つの発売にしない
- 巻き戻しの不在と、OpenAI の空欄と、Anthropic の desktop computer use と、X=0 は、一行のまま核に載せない

昨日は制御の流れを先に名指す話、今日は実行と許可の位置を先に名指す話である。ワーカーを家に置ける公式ページは、分割を先に書く日になる。

## 次に考えるとよさそうな問い

- この仕事のツール実行は、誰の機械か。ループはどこに残るか？
- 自ホストした、と書いたとき、推論も移したことにしていないか？
- これは一台か。名前付きプールか。誰が請求を取るか？
- Fairwind の門と、公開の CodeMender を、同じ棚に置いていないか？
- Devin の分割と Cursor の分割を、別の分類として増やしていないか？
- Gemini の単価や Cursor の不在を、核に昇格させていないか？
