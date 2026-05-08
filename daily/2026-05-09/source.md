<!-- generated: 2026-05-09T03:00:35.414750+09:00 -->
<!-- primary_topic: wiki/maps/research-os-query-paths.md -->
# 今日のランダムテーマ：Research OS Query Paths

日付: 2026-05-09  
主題ノート: `wiki/maps/research-os-query-paths.md`

今回のテーマは、知識ベースを「資料置き場」ではなく「Research OS」として使うための入口設計である。

中心にある問いはシンプルだ。

> 繰り返し出てくる実務上の質問に対して、KBはどのノートから読み始め、どの概念を経由し、どの根拠を確認し、どんな形で答えを返すべきか。

`Research OS Query Paths` は、この問いに対するルーティング表である。  
単なるリンク集ではない。質問の型ごとに、読む順番、見るべき概念、信頼できるソース、弱いシグナル、アウトプット形式、そしてリポジトリへの書き戻し先を定義する。

この設計の狙いは、KBを「検索して終わり」の場所から、「問いに答え、足りないノートを見つけ、知識を更新する運用システム」へ変えることにある。

---

# なぜPodcast向きか

このテーマはPodcast向きである。理由は、表面的には地味な「ノート構造」の話に見えるが、実際にはAIエージェント時代の知識運用、レビュー負荷、文脈管理、組織記憶、RAG、評価品質までつながるからだ。

会話で扱いやすい対立軸が多い。

- KBは「保管庫」なのか、「作業OS」なのか
- 検索は「キーワード検索」なのか、「質問ごとの導線設計」なのか
- エージェントに必要なのは「大量の文脈」なのか、「必要な順番で開ける地図」なのか
- レビューは「人間の最終確認」なのか、「ハーネス層として設計される評価ループ」なのか
- RAGは「ベクトル検索」だけで足りるのか、「階層ナビゲーション」や「グラフ探索」も必要なのか

さらに、`Research OS Query Paths` は抽象論に閉じていない。  
「開発ワークフローにエージェントを導入したい」「長時間動くエージェントを安定させたい」「レビュー負荷を減らしたい」「会社やチームの脳を作りたい」といった、実務者がそのまま言いそうな問いを入口にしている。

Podcastでは、この「質問の形をした入口」という発想を軸にすると話しやすい。  
リスナーにとっても、自分のKBやドキュメント群をどう変えればよいかを想像しやすい。

---

# 背景と文脈

## KBをResearch OSにするという発想

`Research OS Query Paths` の目的は、KBを単なるソース要約の一覧ではなく、研究や実務判断のためのOSとして使えるようにすることだ。

その中核命題は次のように言える。

> 役に立つ compiled wiki は、繰り返し現れるユーザーの質問を安定した経路に流すべきである。まず地図から始め、概念をたどり、最も強い証拠を確認し、最後に根拠ある答えを返す。必要なら欠けているノートを作る。

ここで重要なのは、「答えそのもの」よりも「答えに至る道筋」を保存する点である。  
同じ質問が再び来たときに、毎回ゼロから検索するのではなく、すでに整えられた経路を使う。

## Query path template

Query path は、 recurring question、つまり繰り返し現れる質問ごとに定義される。

テンプレートは以下の6要素で構成されている。

1. **Start map**  
   最初に開くべき統合ノート。入口となる地図。

2. **Concepts to inspect**  
   答えるために必要な再利用可能な語彙。概念ノート群。

3. **Strongest sources**  
   一次情報、公式文書、高信頼の根拠。

4. **Weak signals**  
   Xのスレッド、実務者の逸話、まだ推測的なリード。

5. **Output shape**  
   答え、比較、チェックリスト、ロードマップ、追加調査キューなど、最終成果物の形。

6. **Repo writeback**  
   耐久性のある答えをどこに保存するか。

この設計は、NotebookLMのようなシステムにも相性がよい。  
会話の中で「まず地図」「次に概念」「強い根拠」「弱いシグナル」「アウトプット」「書き戻し」という流れを追えるため、単なる要約よりも深い議論になりやすい。

---

# 中心アイデア

## 1. 質問を入口にする

このノートの最大の特徴は、ノート分類ではなく、ユーザーの質問を起点にしていることだ。

たとえば、次のような質問がすでに Query Path として定義されている。

- 「開発ワークフローにエージェントを導入したい」
- 「長時間動くエージェントを安定させたい」
- 「レビュー負荷を減らしつつ安全性を失いたくない」
- 「会社やチームの脳を作りたい」
- 「ベンダーやツールのアプローチを比較したい」
- 「どの根拠が十分に強いのか知りたい」
- 「RAGで広いコーパスをカバーする質問に答えたい」
- 「エージェントのコンテキストを運用予算として管理したい」

これは、KBの使い方を「どの文書を読むか」から「どの問いに答えるか」へ変える。

## 2. 地図から始める

各パスは Start map を持つ。

たとえば、開発ワークフローにエージェントを導入したい場合、入口は `agent-harness-landscape.md` である。

このマップは、エージェント性能がモデル単体ではなく、周囲のハーネスに強く依存するという立場を取る。  
ここでいうハーネスには、リポジトリ構造、制御、成果物、テスト、レビューループ、オーケストレーションパターンなどが含まれる。

`Agent Harness Landscape` は、主な次元を次のように整理している。

- 行動前のガイダンス  
  feedforward controls、短い地図的指示、アーキテクチャ文書、明示的計画、機能リスト、テンプレートやスキル

- 行動後の修正  
  テスト、リンター、構造チェック、ブラウザ検証、AIレビュー、評価エージェント、定期的なクリーンアップ

- セッションをまたぐ継続性  
  進捗ログ、コミット履歴、機能リスト、initializer agent の出力、context resets

- 自律性の制御  
  approval policy、人間のチェックポイント、classifier-mediated approvals、machine-checkable invariants

- 役割分離  
  planner、generator、evaluator、maintenance / cleanup agents

つまり、Start map は話題全体の見取り図として機能する。  
いきなり個別ソースに飛ぶのではなく、まず何を問題空間として見るべきかを確認する。

## 3. 概念ノートで語彙をそろえる

Query Path は、必ず Concepts to inspect を持つ。  
これは、答えを安定させるための語彙層である。

たとえば、エージェント導入のパスでは以下の概念が挙げられている。

- harness engineering
- agent-recognizable repository
- coding agents
- approval policy

長時間動くエージェントを安定させるパスでは、以下が重要になる。

- long-running agents
- structured handoff artifacts
- context resets
- incremental progress

レビュー負荷を減らすパスでは、以下が中心になる。

- machine-checkable invariants
- feedback controls
- self-verification
- human-in-the-loop

この構造により、NotebookLMが会話を組み立てるときにも、単発の事例紹介ではなく、共通語彙を使った比較や抽象化がしやすくなる。

## 4. 強い根拠と弱いシグナルを分ける

`Research OS Query Paths` では、Strongest sources と Weak signals を分ける。  
これは evidence quality の考え方と直結している。

「どの根拠が十分に強いのか知りたい」という Query Path では、入口は `evidence-quality-and-source-trust.md` であり、概念として evidence-quality、knowledge-base-linting、compiled-wiki が挙げられている。

強い根拠としては、一次ドキュメント、リポジトリ、ポストモーテム、内部運用ノートが重視される。  
一方で、Xスレッドや実務者の逸話は弱いシグナルとして扱われることがある。

この区別は、Podcastで深掘りしやすい。  
AIエージェント領域では、実務者の観察や製品発表が速く流れる一方で、信頼できる検証や運用知見は限られる。だからこそ、ソースの強さを明示する必要がある。

## 5. 出力形を先に決める

Query Path では、Output shape が指定される。  
これが非常に実務的である。

たとえば、

- エージェント導入なら  
  **adoption roadmap + minimum viable harness checklist**

- 長時間エージェントの安定化なら  
  **continuation / reset / delegate decision tree**

- レビュー負荷削減なら  
  **gate design checklist + review escalation policy**

- 会社やチームの脳なら  
  **architecture sketch + governance questions**

- ベンダー比較なら  
  **control surface, autonomy, verification, handoff, deployment model による比較**

- 根拠評価なら  
  **evidence audit or confidence-ranked answer**

- RAGの広範なコーパスカバレッジなら  
  **hierarchy navigation vs vector search vs graph traversal のアーキテクチャ比較**

問いに対して、どんな成果物を返すべきかを最初から定めておく。  
これにより、調査が漫然とした要約に流れにくくなる。

## 6. Writebackで知識が育つ

最後に Repo writeback がある。  
これはResearch OSらしい部分である。

答えを出して終わりではなく、どこに知識を戻すかを決める。

例として、エージェント導入の答えが一般化するなら `outputs/reports/` または新しい map に保存する。  
長時間エージェントの新しい事例が出たら `context-management-decisions.md` を強化する。  
レビュー負荷削減なら、deployment-gate や review-rubric map を更新する。

つまり、Query Path は読むための道筋であると同時に、KBを継続的に改善する運用ループでもある。

---

# 実務での使いどころ

## 1. エージェント導入ロードマップを作る

「開発ワークフローにエージェントを導入したい」という問いでは、`agent-harness-landscape.md` が入口になる。

関連する `coding-agent-harness-patterns.md` では、実務的なパターンが整理されている。

- `plan.md` のような計画ファイルを、セッション単位の handoff artifact として使う
- 独立した verifier や reviewer を使い、自己評価バイアスを抑える
- タスク作業前に、リポジトリを runnable な状態に整える
- lint、hooks、pre-commit、tests を実装に近い場所で回す
- タスクリストや仕様を、進捗ログや生きた意図の成果物として使う
- commit、push、PR作成、自動修正、自動レビューまでループを伸ばす

これらは単なる便利テクニックではなく、ハーネス設計の部品である。

## 2. レビュー負荷を減らす

`eval-review-reliability.md` は、レビューと評価の信頼性を実務的に整理している。

中核命題は次の通り。

> エージェントの出力品質は、生成した同じエージェントによる最後のざっとした確認ではなく、別のハーネス層として評価を設計すると改善する。

信頼性レイヤーは大きく4つある。

1. **決定論的チェックを先に置く**  
   lint、typecheck、tests、smoke tests、formatting、structural checks、repository-specific machine-checkable invariants

2. **タスク適合レビュー**  
   要件カバレッジ、エッジケース、後方互換性、ユーザー向け挙動、保守性

3. **独立した evaluator loop**  
   subagent review、adversarial review、blocking review gates、人間へのエスカレーション

4. **trace-driven improvement**  
   失敗を新しいテスト、明確な指示、repo rules、rubrics、lint checks に変換する

これは、Query Path の「レビュー負荷を減らしつつ安全性を失いたくない」という問いにそのまま対応する。

## 3. ベンダーやツールを比較する

`harness-engineering-vendor-comparison.md` は、ベンダーや実務者ごとのハーネス観を比較する地図である。

比較軸としては、control surface、autonomy、verification、handoff、deployment model が挙げられている。

各ソースの強調点は異なる。

- OpenAI  
  リポジトリ設計、machine-enforced invariants、agent-recognizable context、継続的クリーンアップ、cross-agent review / delegation

- Cursor  
  agent-first coding workspace、multi-agent visibility、local/cloud handoff、multi-repo operation、review surfaces、harness measurement

- Cognition / Devin  
  cloud-agent runtime substrate、microVM isolation、snapshotting、warm-pool orchestration、permission inheritance、audit trails

- Anthropic  
  long-running agents、structured handoffs、initializer agents、context resets、planner/generator/evaluator split、MCP、skills、memory、managed-agent outcomes

- LangChain  
  traces、middleware、self-verification hooks、loop detection、reasoning-budget heuristics

この比較は、ツール選定だけでなく、自社のハーネスに何が足りないかを考える材料になる。

## 4. コンテキストを運用予算として扱う

`Research OS Query Paths` には、「エージェントのコンテキストを運用予算として管理したい」という問いもある。  
関連ソースとして、Machine Learning Mastery の context engineering 記事が使える。

このソースは、コンテキストウィンドウをRAMに例える。  
速いが、希少で、高価で、今のステップに必要な情報が入っていなければ役に立たない。

主な主張は以下である。

- 本番エージェントの失敗は、モデル能力不足ではなく context mismanagement から起きることが多い
- context には token billing という金融コストと、attention dilution という認知コストがある
- static context と dynamic context を分けるべき
- append-only の会話履歴は context bloat や context poisoning を招く
- raw recency truncation よりも anchored iterative summarization が有効
- retrieval は自動反射ではなく、予算化された判断であるべき
- token budgeting はエージェントループ全体で測るべき
- context utilization は最大化ではなく、おおよそ 60–80% 程度に保つという考え方が示されている
- recall、artifact、continuation probes などで context failure を評価できる

この話は、長時間エージェントの安定性や、会社の脳、RAG設計とも自然につながる。

---

# 誤解しやすい点・論点

## 誤解1: Query Path はただのリンク集である

違う。  
Query Path は、リンクの集合ではなく、問いに答えるためのプロセス定義である。

Start map、Concepts、Strongest sources、Weak signals、Output shape、Writeback がそろって初めて機能する。

## 誤解2: 強いソースだけ見ればよい

強いソースは重要だが、弱いシグナルにも役割がある。  
新しい実務領域では、Xスレッドや実務者の逸話が早期警戒や仮説生成に使える場合がある。

ただし、それらは確定的な根拠としてではなく、弱いシグナルとして明示的に扱う必要がある。

## 誤解3: エージェント性能はモデルを替えれば解決する

`Agent Harness Landscape` や関連ノート群は、性能をモデル単体ではなくハーネス全体で見る。  
リポジトリ構造、テスト、レビュー、計画、進捗ログ、権限制御、コンテキスト管理が品質に影響する。

## 誤解4: レビューは最後に人間が見ればよい

`Eval and Review Reliability` は、評価を独立したハーネス層として扱う。  
安い決定論的チェックを先に置き、曖昧または高リスクな変更だけ人間に上げる設計が重要になる。

## 誤解5: RAGはベクトル検索だけの問題である

「広いコーパスカバレッジ質問に答えたい」という Query Path では、hierarchy navigation、vector search、graph traversal の比較が出てくる。  
つまり、検索手法そのものだけでなく、コーパスをどう歩ける形にするかが論点になる。

---

# NotebookLMが会話で拾うとよい問い

- KBを「Research OS」と呼ぶとき、従来のドキュメント集と何が違うのか？
- なぜ「質問の形をした入口」が重要なのか？
- Start map、Concepts、Strongest sources、Weak signals、Output shape、Writeback のうち、一番見落とされやすいのはどれか？
- ハーネスエンジニアリングは、プロンプトエンジニアリングとどう違うのか？
- エージェント導入で、最小限の viable harness とは何を含むべきか？
- レビュー負荷を減らすには、人間を減らすのか、それとも人間が見る前の層を厚くするのか？
- 強い証拠と弱いシグナルを分けないと、どんな失敗が起きるか？
- 長時間エージェントに必要なのは、大きなコンテキストか、よい handoff artifact か？
- コンテキストをRAMのように扱うとは、実務上どういう意味か？
- RAGの設計で、ベクトル検索、階層ナビゲーション、グラフ探索はどう役割が違うのか？
- Writeback がないKBは、なぜ徐々に使いにくくなるのか？
- NotebookLMのようなツールは、このQuery Path構造をどう活かせるか？

---

# 参照したKBノート

- `wiki/maps/research-os-query-paths.md`  
  Research OS Query Paths。質問ごとの入口、概念、根拠、出力形、書き戻し先を定義する中心ノート。

- `wiki/maps/agent-harness-landscape.md`  
  エージェント性能をモデル単体ではなく、リポジトリ構造、制御、成果物、テスト、レビューループ、オーケストレーションで捉える地図。

- `wiki/maps/eval-review-reliability.md`  
  エージェント出力の評価とレビューを、決定論的チェック、タスク適合レビュー、独立評価ループ、trace-driven improvement として整理。

- `wiki/maps/harness-engineering-vendor-comparison.md`  
  OpenAI、Cursor、Cognition / Devin、Anthropic、LangChain などのハーネス設計上の強調点を比較。

- `wiki/maps/coding-agent-harness-patterns.md`  
  `plan.md`、verifier split、環境ブートストラップ、決定論的チェック、進捗アーティファクト、PR後のループなど、実務パターンを整理。

- `wiki/sources/machinelearningmastery-effective-context-engineering-ai-agents.md`  
  コンテキストを希少な運用資源として扱い、static/dynamic context、履歴管理、検索予算、token budgeting、context-quality evaluation を整理する記事。

---

# NotebookLMに期待する話し方メモ

- 最初は「KBを資料置き場ではなくResearch OSにする」という大きな比喩から入る。
- 次に、Query Path の6要素を丁寧に説明する。特に「Start map」と「Writeback」が重要。
- 会話では、抽象論だけでなく「開発ワークフローにエージェントを入れたい」という具体例を早めに出す。
- ハーネスエンジニアリング、レビュー信頼性、コンテキスト予算、会社の脳、RAG設計を、別々の話題ではなく Query Path でつながるものとして扱う。
- 「強い根拠」と「弱いシグナル」を分ける姿勢を強調する。
- トーンは、実務者向けに落ち着いて、少し探究的に。煽らず、「これは地味だが強い設計思想」という雰囲気がよい。
- 最後は、リスナー自身のKBに対して「よく来る質問を3つ選び、それぞれにStart map、Concepts、Sources、Output shape、Writebackを決めてみる」と促すと自然。
