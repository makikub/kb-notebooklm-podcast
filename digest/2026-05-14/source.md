<!-- generated: 2026-05-14T13:02:54.288587+00:00 -->
<!-- kb_daily_digest_date: 2026-05-14 -->
# KB Daily Digest — 2026-05-14  
## Nested Learningが投げかける「記憶は外に置くのか、モデルの中で学ぶのか」

2026-05-14 UTC の `knowledge-base-llm` では、Google Research の “Introducing Nested Learning: A new ML paradigm for continual learning” が新しく取り込まれ、それに合わせて `continual-learning` 概念ノートが追加されました。既存の `agent-knowledge-loop`、memory navigation、関連する source note も更新されています。

今日の更新は、単に新しい研究ブログを1本追加した、というよりも、このKBがこれまで扱ってきた「エージェントの記憶」をめぐる議論の座標軸を変えるものです。これまでは、ファイル、wiki、RAG、ハンドオフ成果物、コンテキストグラフ、エージェントの実行ログなど、知識をモデルの外側にどう保存し、再利用し、監査するかが大きなテーマでした。今日の Nested Learning は、その議論に対して「では、どの知識や学習能力は、将来的にモデル内部へ戻せるのか」という問いを差し込みます。

外部記憶は、見える、直せる、消せる、引用できる、レビューできる、という強みがあります。一方で、モデル内部の継続学習がうまく働くなら、知識やスキルはより自然に合成され、毎回検索してプロンプトに詰め込むよりも効率的に使えるかもしれません。今日のKB更新は、この二つを単純な勝ち負けではなく、「どの層にどの記憶を置くべきか」という設計問題として扱うための足場を作っています。

---

## 今日の全体トレンド

今日の中心トレンドは、エージェント記憶の議論が「保存場所」から「学習階層」へ広がったことです。

これまでKB内の memory / knowledge substrate 周辺では、知識を外部化するパターンが強く扱われてきました。たとえば、raw material を取り込み、wiki note にコンパイルし、質問応答やエージェント作業に使い、また有用な出力をKBへ戻す。これは `agent-knowledge-loop` として整理されている考え方です。このループでは、知識はモデルの外にあり、Markdown、wiki、source note、navigation page、map、glossary などとして残ります。

この外部化は実務的です。なぜなら、何を根拠にしたかを追いやすく、間違いを直しやすく、古くなった情報を無効化しやすく、必要なら人間がレビューできます。業務で使うエージェントや長期運用される知識基盤にとって、これは非常に重要な性質です。

しかし今日追加された Google Research の Nested Learning は、この前提を少し揺さぶります。このソースは、モデルアーキテクチャと最適化アルゴリズムを別々の部品として見るのではなく、更新頻度の異なる複数の学習プロセスが入れ子になったものとして捉える枠組みを提示しています。つまり、attention、backpropagation、optimizer momentum といった仕組みも、広い意味では記憶や学習のプロセスとして見直せる、という視点です。

ここで現れるのが、外部化された記憶とモデル内部の記憶の対立軸です。知識をファイルやwikiに残すべきか。それとも、モデルの重みや内部メモリ、更新頻度の異なるアーキテクチャ上のモジュールに学ばせるべきか。今日のKBは、この問いを `continual-learning` という新しい概念ノートに集約し始めました。

---

## なぜこの更新がKBにとって重要か

このリポジトリ自身が、まさに外部化された知識ループだからです。

`knowledge-base-llm` は、ソースを取り込み、ノート化し、概念として整理し、関連地図に接続し、日次ダイジェストとして再編集します。これは、モデルが内部で学習するのではなく、モデルの外に知識構造を作り、そこにエージェントや人間が戻ってくる仕組みです。

今日の Nested Learning は、その前提に対してメタな問いを投げます。もし将来、モデルが継続的に新しい知識やスキルを取り込み、古い能力を壊さず、必要なときに自然に合成できるなら、外部KBの役割は何になるのか。

一つの可能性は、外部KBが不要になる、という単純な話ではありません。むしろ、役割が変わる可能性があります。外部KBは、すべての記憶を保持する倉庫というよりも、出典、根拠、レビュー、評価、監査、無効化、ロールバックのための制御面になるかもしれません。モデル内部が「使える知識」を担い、外部KBが「説明できる知識」「検証できる知識」「更新管理できる知識」を担う、という分担です。

今日追加された `continual-learning` ノートは、この分担を考えるための接続点です。定義は、モデルやエージェントシステムが、重要な古い能力を失わずに新しい知識やスキルを獲得する能力。関連概念として、`agent-knowledge-loop`、`context-engineering`、`durability`、`trace-driven-improvement`、`evidence-quality` が接続されました。これにより、継続学習は単なるモデル研究の話ではなく、KB設計、エージェント運用、証拠品質、耐久性の問題として読めるようになっています。

---

## 重要ソース3本

### 1. Google Research — Nested Learning

今日の主役は、Google Research の “Introducing Nested Learning: A new ML paradigm for continual learning” です。

このソースは、現在のLLMの限界として、静的な事前学習知識、有限のコンテキスト窓、そして素朴にパラメータを更新したときに起きうる catastrophic forgetting を挙げています。そのうえで、モデルアーキテクチャと最適化アルゴリズムを、異なる文脈の流れと更新頻度を持つネストした学習システムとして統一的に捉える枠組みを提示します。

KB上で重要なのは、Nested Learning が「記憶」を短期コンテキストと長期重みだけに分けない点です。source note では、backpropagation、attention、optimizer momentum が広い意味で associative memory として扱われること、また continuum memory system によって、異なる速度で更新される記憶モジュールを設計できる可能性が整理されています。

この発想は、エージェント記憶の議論に強く関係します。従来の実務的なエージェント設計では、記憶はしばしば外に置かれます。ファイル、wiki、RAG、ハーネス、ハンドオフ、トレース、メモリDBといった形です。しかし Nested Learning は、記憶や学習をモデル内部の複数レベルに配置できる可能性を示します。

また、Google Research のソースでは proof-of-concept として Hope architecture が紹介されています。source note では、Hope は Titans を拡張し、self-modifying recurrent memory と CMS blocks を組み合わせるものとして整理されています。報告対象には、言語モデリング、common-sense reasoning、long-context Needle-in-a-Haystack tasks、continual learning、knowledge incorporation が含まれます。

ただし、KBではこのソースを慎重に扱っています。今日取り込まれたのは研究ブログ / paper announcement であり、詳細なベンチマークや手法の妥当性は関連 paper に委ねられています。そのため、現時点では「強く実証済みの結論」というよりも、「モデル内部の継続学習を考えるための重要な設計仮説」として位置づけるのが適切です。

### 2. Ilija Lichkovski — continual learning desiderata for LLMs

2本目は、既存ソースである Ilija Lichkovski / @carnot_cyclist の continual learning desiderata thread です。今日新規追加されたものではありませんが、Nested Learning の追加に合わせて `continual-learning` 概念ノートの supporting source として重要性が増しました。

このスレッドの中心は、LLMにおける継続学習を、分布シフトの下で順次学習し、catastrophic forgetting を避け、古い能力を保ちながら新しい能力を合成する問題として捉えることです。source note では、強い継続学習には、一般能力の保持、効率性、段階をまたいだスキル合成が必要だと整理されています。

このソースは、KB内では「外部化偏重」へのカウンターとして機能します。RAG、ファイルベース memory、ハーネスによる足場は実用的ですが、それだけで能力が本当に合成されるのか。検索して持ってくるだけではなく、モデルの中にスキルとして取り込まれたほうが、長期的にはより強くなるのではないか。この疑問を担うソースです。

また、replay-heavy や regularization-heavy な方法が本当の問題を回避している可能性、capacity expansion だけでは compositionality の問題を解けない可能性も open question として残されています。今日の Nested Learning と並べることで、このスレッドは「どのような内部学習なら、外部記憶の限界を越えられるのか」という問いの背景になります。

### 3. neural_avb — Agentic Memory / Memory Transfer Learning

3本目は、neural_avb の Agentic Memory / Memory Transfer Learning thread です。こちらは、モデル内部ではなく、外部化されたエージェント記憶の側から重要です。

このソースでは、過去のエージェント実行トレースを offline に処理し、複数の記憶表現として保存する考え方が示されています。source note では、trajectory、workflow、summary、insight という4種類のメモリ形式が整理されています。特に、最も抽象度の高い insight-level memories が、タスクやドメインを越えて転移しやすい可能性がある、という点が重要です。

ここで扱われているのは、finetuning ではなく retrieval-based memory です。つまり、過去の経験をモデル内部に焼き込むのではなく、推論時に関連する記憶を検索してプロンプトに入れる。これは、今日の Nested Learning と非常に対照的です。

しかし、単純な対立ではありません。neural_avb のソースは、外部記憶にも抽象化の階層があることを示します。生の軌跡をそのまま再利用するのか、ワークフローとして再利用するのか、要約として残すのか、より抽象的な手続き的洞察として残すのか。これは、Nested Learning が語る multi-rate memory や nested optimization の発想と、別のレイヤーで響き合います。

外部に置く場合でも、記憶は単なるログではなく、再利用可能な知識へ変換される必要があります。一方で、古い記憶が現在のタスクに合わず negative transfer を起こす問題も残ります。この点は `continual-learning` ノートの tradeoffs にも接続されました。

---

## 更新された概念・地図

### `wiki/concepts/continual-learning.md`

今日の最も大きな概念追加は、`Continual Learning` ノートです。

このノートでは、継続学習を「モデルやエージェントシステムが、重要な古い能力を失わずに新しい知識やスキルを獲得する能力」と定義しています。ここで重要なのは、対象がモデル単体に閉じていないことです。エージェントシステム全体、つまり外部メモリ、検索、wiki、ハーネス、トレース、評価ゲートまで含めて、継続的に学ぶ仕組みとして捉えられます。

tradeoffs では、in-weight learning は retrieval より効率的に合成される可能性がある一方、外部記憶のほうが inspection、edit、invalidation、citation に強いと整理されています。また、agent trace memory は finetuning なしに性能を改善しうる一方、古いトレースや不一致な記憶による negative transfer のリスクがあるとされています。

open questions も重要です。どの能力を parametric にするべきか。どの能力を外部化された memory / harness layer に残すべきか。catastrophic forgetting、negative transfer、stale internal memories をどう検出するのか。モデルの振る舞いが継続的に変わる場合、人間のレビューや評価ゲートはどう変わるべきか。これらは、今後のKB更新で繰り返し戻ってくる問いになりそうです。

### `wiki/concepts/agent-knowledge-loop.md`

`Agent Knowledge Loop` も更新されました。この概念は、LLMがソースを取り込み、ノートを編み、wiki上で質問に答え、有用な出力をまたKBへ戻すループを表します。

今日の更新により、supporting sources に Google Research の Nested Learning が追加されました。これにより、agent knowledge loop は、単なる外部化されたKB運用パターンではなく、モデル内部の継続学習との比較対象になりました。

重要なのは、`agent-knowledge-loop` が否定されたわけではないことです。むしろ、外部化された知識ループの強みがより明確になります。すなわち、provenance、lint、review、contradiction detection、stale claim の発見、unsupported derived facts の抑制といった機能です。Nested Learning が内部記憶の可能性を広げるほど、外部KBは「学習の置き場」だけでなく「学習を統制する面」として重要になります。

### `wiki/navigation/memory.md`

memory navigation には、`continual-learning` が Core Concepts として追加され、Google Research の source note が Key Source Entrypoints に入りました。

これにより、agent memory、knowledge base、compiled notes、context graphs、team/company brains、retrieval architecture などを調べる導線の中に、モデル内部の継続学習が正式に接続されました。今後、memory navigation は「外部メモリ設計の入口」であると同時に、「外部記憶と内部学習の境界を考える入口」になります。

### `wiki/sources/README.md` と関連 source note

Source Notes の一覧にも Google Research の Nested Learning ノートが追加されました。また、carnot_cyclist と neural_avb の既存 source note は、`continual-learning` との関係が明確になりました。

この変更によって、3つの立場が見えやすくなっています。

ひとつは、Google Research の Nested Learning。これは、アーキテクチャと最適化をネストした学習システムとして捉え、内部メモリの階層化を考える立場です。

もうひとつは、carnot_cyclist の continual learning desiderata。これは、LLMが本当に継続的に学ぶには何が必要か、外部化だけで十分なのかを問う立場です。

最後が、neural_avb の agentic memory。これは、過去のエージェント経験を外部記憶として抽象化し、検索して再利用する立場です。

---

## 実務での読みどころ

実務での焦点は、「どの知識をどこに置くべきか」です。

まず、監査が必要な知識は外部化に向いています。根拠を示す必要がある、古くなったら更新しなければならない、誰が見ても修正できる必要がある、誤りが業務上のリスクになる。こうした知識は、wiki、source note、RAG、ハンドオフ成果物、評価ログのような形で残すほうが扱いやすいです。

一方で、毎回プロンプトに入れなくても自然に使ってほしいスキルや、複数タスクにまたがって合成されるべき能力は、モデル内部の継続学習がうまく働くなら魅力的です。たとえば、特定の手続き、検証習慣、問題分解の癖、長期的に安定したスキルのようなものは、外部検索だけでは摩擦が大きい場合があります。ただし、今日のKBが扱った範囲では、それを安全かつ監査可能に実現する方法はまだ open question です。

また、外部記憶にも設計上の工夫があります。neural_avb のソースが示すように、過去の経験をそのまま trajectory として残すだけでなく、workflow、summary、insight へ抽象化することで、再利用性が変わります。これは、現場のエージェント運用に直結します。ログをただ貯めるだけでは、使える記憶にはなりません。どの抽象度で残すか、どのタイミングで検索するか、古くなった記憶をどう捨てるかが重要になります。

Nested Learning が示す未来像を急いで実務に持ち込む必要はありません。しかし、外部KBを設計する側は、今から「これは外に置くべき記憶なのか、それとも将来的にはモデル内部で学ばれるべきスキルなのか」と考える価値があります。特に、provenance と rollback が必要な知識は外部に残し、反復的な手続きや抽象的な作業習慣は内部化候補として見る、という整理は有用です。

---

## Podcastで掘ると面白い論点

Podcast向けには、「AIエージェントの記憶は、ファイルに残すべきか、モデルの中で学ばせるべきか」という問いから入ると自然です。

最初に、現在の実務ではなぜ外部記憶が重要なのかを話せます。ファイル、wiki、RAG、ログ、ハンドオフ成果物は、モデルが忘れても残ります。人間が見られます。間違いを直せます。引用できます。業務ではこの透明性が大きな価値を持ちます。

次に、Nested Learning の視点を紹介します。もし attention、backpropagation、optimizer momentum まで含めて記憶や学習の仕組みとして見直せるなら、モデル内部にも複数の記憶階層がありうる。短期コンテキストと長期重みだけではなく、更新頻度の違うメモリが連続体として存在するかもしれない。ここで、外部KB中心の世界観が少し揺れます。

そのうえで、carnot_cyclist の in-weight continual learning 論を挟むと、議論に緊張感が出ます。外部記憶は便利だが、能力の合成という意味では限界があるのではないか。検索して思い出すだけではなく、本当に学んで身につける必要があるのではないか。

最後に、neural_avb の agentic memory を置くと、外部記憶側も単純ではないことがわかります。過去のトレースをただ保存するのではなく、抽象的な insight に変換すれば、モデル内部学習とは別の形で転移が起きるかもしれません。

この流れにすると、結論は二択ではなくなります。外部か内部かではなく、どの知識をどの層に置くか。外部KBは何を担い、モデル内部は何を担うか。内部学習が進んだとき、provenance、invalidation、rollback をどう保つか。ここが今日のいちばん面白い論点です。

---

## 次に追う問い

今後追うべき問いは、まず「どの知識が外部化に向き、どの知識が内部化に向くのか」です。安定した世界知識、変化の速いローカル状態、組織固有のルール、作業手順、検証習慣、抽象的な問題解決スキルは、それぞれ違う扱いが必要になりそうです。

次に、「内部学習の provenance をどう扱うのか」です。外部KBなら、どのソースから来た知識かを追えます。間違いがあればノートを直せます。しかし、モデル内部に学ばれた知識について、何が変わったのか、なぜ変わったのか、どの証拠に基づくのか、どう戻すのかは難しい問題です。

三つ目は、「negative transfer と catastrophic forgetting をどう検出するのか」です。外部記憶でも、古い insight が今のタスクに悪影響を与えることがあります。内部学習なら、古い能力を壊すリスクがあります。どちらの場合も、評価と監視が必要です。

四つ目は、Hope architecture のどの要素が報告された性能に効いているのかです。source note では、CMS blocks、self-modification、Titans-style surprise memory、Nested Learning 全体の枠組みなどが候補として挙がっています。今日の取り込み範囲では、詳細な切り分けはまだできません。

最後に、このKB自身の設計にも問いが戻ってきます。`knowledge-base-llm` は今後も外部化された知識ループとして、出典、概念、地図、日次更新を蓄積していくはずです。そのとき、この外部KBは「モデルに記憶させる代替物」なのか、それとも「モデルが継続的に変わる時代の監査・評価・意味づけの層」なのか。今日の更新は、その問いを開きました。

---

## NotebookLM Podcast用メモ

- 今日のテーマは「AIエージェントの記憶は外に置くのか、モデルの中で学ばせるのか」。
- 主役ソースは Google Research の Nested Learning。
- Nested Learning は、architecture と optimizer を、異なる更新頻度を持つ nested learning system として見る。
- KB上の重要ポイントは、memory を短期 context と長期 weights だけでなく、continuum memory system として捉えること。
- Hope architecture は proof-of-concept として紹介されているが、詳細な実証は paper 側に委ねられているため、KBでは研究仮説として慎重に扱う。
- carnot_cyclist の thread は、in-weight continual learning の必要性を主張するカウンター軸。
- neural_avb の thread は、外部化された agent trace memory を trajectory / workflow / summary / insight に抽象化する立場。
- 今日追加された `continual-learning` 概念ノートは、この三つをつなぐ中継点。
- 実務上の対立軸は、効率的な合成を期待する内部学習と、監査・編集・無効化・引用に強い外部記憶。
- 結論は二択ではなく、「どの知識をどの層に置くか」。
- Podcastの締めは、内部学習が進むほど、外部KBは記憶倉庫ではなく provenance、evaluation、rollback のための制御面になるかもしれない、という話にすると自然。
