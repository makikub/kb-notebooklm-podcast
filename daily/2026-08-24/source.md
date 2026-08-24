<!-- generated: 2026-08-24T01:30:00Z -->
<!-- primary_topic: wiki/maps/coding-agent-harness-patterns.md -->
# Coding-Agent Harness Patterns for Always-On Agents

- Date: 2026-08-24
- Theme slug: `coding-agent-harness-patterns`
- Primary topic: `wiki/maps/coding-agent-harness-patterns.md`
- Purpose: NotebookLM向けの対話用ソース。KBマップの8パターンを、常時稼働コーディングエージェントの実務論点として読み直す
- News angle: Cursor Origin beta (2026-08-17) + Cloud Agents Subscriptions / `/goal` / subagent VMs (2026-08-19)

## Talking points（3〜5分）

1. エージェントの品質はモデルより、周囲のハーネスで決まる。
2. 8月17日の Origin beta と 8月19日の Cloud Agents 更新は、「一回答えて終わる助手」から「起きているあいだ仕事を続ける作業者」への製品化である。
3. 常時稼働になるほど、8つのハーネスパターンがプロンプトより先に効く。
4. `/goal` は計画の寿命を伸ばし、Subscriptions はローカル作業の外側までループを伸ばし、subagent VMs は検証役を安く分ける。
5. 速く回す場所と、人間が止める場所を分けないと、常時稼働は複利ではなく事故の自動化になる。

## 今日の読み方

knowledge-base-llm の `Coding-Agent Harness Patterns` は、コーディングエージェントの品質がプロンプトではなく、計画ファイル、環境、テスト、レビュー、公開後の監視に依存し始めたときに「ハーネスエンジニアリング」になると整理している。

マップは後から Pattern 9 以降も増えているが、今日の読み物は最初の8パターンを軸にする。理由は単純で、Cursor のこの1週間は、その8つが製品機能として表に出てきた週だからだ。

2026-08-17、Cursor は Origin を early beta として有料プランに出した。リポジトリ、PR、コード閲覧、GitHub 双方向同期が Cursor の中に入る。公式の言い方では、GitHub から始めたものは GitHub が source of truth のまま。agent-native な機能は「soon」と先送りされている。

2026-08-19、Cursor changelog は Cloud Agents を「always-on agents can operate as a system」と書いた。Subscriptions で PR・Slack・スケジュールに起き、`/goal` で長い目標を持ち、subagent は独立 VM で衝突せず動く。steering は途中の操作を切らさず、次の tool call まで待つ。

今日の問いは「Cursor が何を出したか」ではない。「常時稼働エージェントを、どのハーネスで安全に走らせるか」である。

## Pattern 1. Plan as handoff artifact

セッション単位の `plan.md` を、会話の中に消える意図ではなく、引き継げる契約にする。

なぜ効くか:
- 意図が見える
- context reset しても復帰できる
- verifier が批評できる安定した対象になる

Cursor 角:
`/goal fix all flaky tests and make CI green` は、一回のプロンプトではなく、完了まで持つ目標である。Custom Mode や `/loop` と組むと、計画はチャット履歴ではなく運用オブジェクトになる。常時稼働では、計画がない目標はただの無限ループに見える。

対話の種:
「今日の `/goal` は、ファイルに残る計画になっているか。それともチャットの一言か。」

## Pattern 2. Verifier split without full multi-agent overhead

重い思考は独立した一時 thinker に出し、一人の deliberator が批評して統合する。実行役を丸ごと複製する必要はない。計画レビューか実装レビューだけ分ければよい。

なぜ効くか:
- evaluator の利点を安く取れる
- 自己採点バイアスを減らす
- 運用者の頭の中は単純なまま

Cursor 角:
subagent VMs は、このパターンの製品化に近い。各 subagent は隔離されたプロジェクトコピーと clean context を持つ。親の変更を別環境で試す、独立した修正を swarm する、衝突せず並行する。常時稼働では「同じエージェントが自分の仕事を自分で褒める」状態が長く続くので、検証役の分離は贅沢ではなく保険になる。

対話の種:
「作った人と同じ文脈で採点させていないか。新鮮な VM で見るべき差分はどれか。」

## Pattern 3. Environment bootstrapping before task work

未来のコーディングタスクを頼む前に、走れるリポジトリ基準を用意する。

なぜ効くか:
- setup 失敗でタスク予算を溶かさない
- tests / linters / smoke に意味のある起点を与える
- 環境自体が壊れていると、評価信号が崩れる

Cursor 角:
subagent が「自分のマシン」を持つほど、壊れた baseline は複製される。Origin 側の repo / checks / diffs が見えても、install が毎回落ちる、テストが赤のまま、生成物が検索に混ざるなら、Subscriptions は壊れた環境を定期的に起こすだけになる。常時稼働の最初の仕事は、機能追加ではなく boot 可能な状態である。

対話の種:
「エージェントが起きる前に、どのコマンドが緑であるべきか。」

## Pattern 4. Cheap deterministic checks on every step

再生成が安くなったら、end-to-end tests を振る舞いの契約にする。lint、hooks、pre-commit、tests を実装のすぐ隣で回す。

なぜ効くか:
- エラー検出を左に寄せる
- レビュー負担を減らす
- 規約をエージェントが使える信号にする

Cursor 角:
Cloud agents は作った PR に自動 subscribe し、CI を直し、bot comments に返す。安い決定的チェックがないと、このループはノイズを往復する。flaky な CI に `/goal` を向けると、エージェントは「直し続ける」が、人間は「何が完了か」を失う。常時稼働では、安いチェックが心拍になる。

対話の種:
「人間が見る前に、機械が落とすべき赤は何か。」

## Pattern 5. Progress visibility through lightweight artifacts

重いスキーマが要らないなら、task list を進捗ログにする。spec は実装で決まったことを追記する生きた意図であり、コーディング前に凍らせない。

なぜ効くか:
- セッションをまたいで続きやすい
- 同期コストが下がる
- 人間もエージェントも、完了と未完了を同じ面で見られる

Cursor 角:
Subscriptions は「いつの間にか進んでいる」状態を作る。Slack で `@cursor check back in an hour` と言えるのは便利だが、戻ってきたときに見るべきはチャット全文ではない。task list、更新された spec、PR の checks、残件。Origin の PR timeline / diffs は、その可視性を IDE の中に寄せる。agent-native 機能はまだ soon でも、進捗をファイルに残す習慣は今日から要る。

対話の種:
「寝ているあいだに進んだ仕事を、どの成果物で朝確認するか。」

## Pattern 6. Extend the harness beyond local execution

commit、push、PR、autofix、自動レビューまでループを伸ばす。heartbeat 型モニタは、PR comments、doc comments、Slack、スケジュールを見て、新しい証拠が来たら再開する。

なぜ効くか:
- 納品をコーディング段階で切らない
- 統合面でしか出ない問題を拾う
- コードがローカルを出たあとも、ハーネスが結果を調整できる

Cursor 角:
これが 8月19日の中心である。Subscriptions はクラウドエージェント限定で、イベント源に subscribe して起きる。作った PR を completion まで運ぶ。Origin（8月17日）は、そのループが触る repo / PR / search を Cursor 内に置く。GitHub が source of truth のままでも、レビュー面がエージェントの隣に寄ると、Pattern 6 は「あとで GitHub を見る」から「同じ面で続ける」に変わる。

対話の種:
「ローカルで緑なら終わり、にしていないか。公開後に誰が起きるか。」

## Pattern 7. Shared rubric for semantic review

決定的チェックと、安定したレビュー rubric を対にする。

なぜ効くか:
- 人間レビューとモデルレビューが揃う
- ループ同士を比較できる
- 曖昧で漂うコメントが減る

Cursor 角:
常時稼働エージェントは、CI だけでなく「意味」も直し続ける。受け入れ条件、対象外、リスク、公開可否、ユーザー影響が rubric になっていないと、bot comments への返信は量だけ増える。Custom Mode は skill をピン留めする「always on skill」だが、ピン留めするものが曖昧なら、焦点ではなく癖が常時オンになる。

対話の種:
「この PR を通してよい条件を、人間とエージェントが同じ言葉で言えるか。」

## Pattern 8. Ecosystem curation as harness assembly

skills、subagents、MCP、memory、hooks、IDE 連携のカタログは見る。ただし作業ハーネスに昇格させるのは、小さな信頼済みセットだけにする。

なぜ効くか:
- 散らばった生態系を選べる部品にする
- plugin sprawl 自体が故障モードになるのを防ぐ
- 直接評価する価値のある道具の研究キューを残す

Cursor 角:
Origin、Subscriptions、`/goal`、subagent VMs、Custom Modes、steering は、全部を同時に「オン」にする話ではない。まずは計画、安いチェック、隔離された検証、PR までのループ、止める場所。プラグインを増やす前に、今の8つがファイルと CI と rubric になっているかを見る。常時稼働は、未整理な道具箱を一晩中振る機械にもなる。

対話の種:
「今週オンにした機能のうち、来週も残す信頼済みセットはどれか。」

## 制御の層で見ると

Feedforward: plan、`/goal`、architecture notes、repo conventions、Custom Mode。
In-loop: hooks、Subscriptions、steering、task-list、subagent VMs。
Feedback: lint、tests、PR review、autofix、人間の accept / reject。

Cursor の1週間は、この3層をクラウドに伸ばした。だから「賢いモデルが常時動く」ではなく、「3層がイベントで起きる」。

## 実務のとりはじめ

大きな基盤は要らない。今日からできる最小セット:
- 長い目標は `/goal` でも、`plan.md` か task list に残す
- エージェントが起きる前に、install と安いテストを緑にする
- 生成役と検証役を分ける。可能なら fresh VM
- PR までループを伸ばすが、本番・秘密・破壊的操作は人間ゲート
- 繰り返す指摘は、会話ではなく hook / skill / rubric / テストへ戻す

マップ後半の Pattern 9 以降（rule-update loop、codebase legibility、harness owner、durable threads、manager-subagent fleet）は、この8つが回ってから効く。常時稼働は、その順番を飛ばす誘惑を強くする。

## 次に考えるとよさそうな問い

- 今夜エージェントを起きていてよいイベント源は、PR、Slack、スケジュールのどれか？
- `/goal` の完了条件は、CI 緑だけか。rubric 上の意味も含むか？
- subagent に渡す前に、どの環境チェックが必須か？
- Origin をレビュー面として使うとして、source of truth はどこに残すか？
- 繰り返している指摘を、どのテスト、skill、hook に昇格させるか？
- 人間だけが止めるべき変更は、どれか？
