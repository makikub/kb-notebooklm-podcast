<!-- generated: 2026-05-30T13:01:25.738738+00:00 -->
<!-- kb_daily_digest_date: 2026-05-30 -->
# KB Daily Digest Source — 2026-05-30

このページは、knowledge-base-llm の日次更新を NotebookLM に読み込ませるための公開向けソースページです。
Discord通知よりも文脈を厚めに残し、Podcast化しやすいように、今日追加・更新されたソース、概念、地図を文章中心で整理します。

## 今日の全体像

# KB Daily Digest 2026-05-30

2026-05-30 UTC の knowledge-base-llm では、新規 raw/wiki/sources の追加は確認できませんでした。一方で `outputs/notebooklm-podcast/2026-05-30/notebooklm-source.md` が新規生成され、今日の compile テーマとして `wiki/maps/approval-policy-patterns-and-escalation.md` が取り上げられています。内容は「approval policy」を単なる自動実行のオン・オフではなく、行為のリスク、レビューのタイミング、権限の広がり、失敗時のエスカレーションを組み合わせた設計空間として扱うものです。

今日の全体トレンドは、エージェントの自律性を増やすほど重要になる「承認の置き場所」を、ハーネス設計の中核として捉え直す流れです。低リスクの read や bounded search は安く通し、状態変更や外部公開、広い権限付与、再帰的な委任にはレビューや人間の明示承認を残す、という勾配のある設計が軸になっています。これは既存KBの `agent-harness-landscape`、`coding-agent-harness-patterns`、`eval-review-reliability`、`agent-deployment-gates-and-operational-risk` と強く接続しています。

重要ソースの1本目は Anthropic auto mode です。ここでは承認プロンプトの摩擦を、単なるUX問題ではなく安全性とスループットの両方に効くプロダクト設計問題として扱っています。常に確認する運用は遅く、完全バイパスは危険なので、classifier-mediated auto approval のような中間層を置く発想が、今日の地図に「静的 allow/deny だけでは足りない」という観点を与えています。

2本目は Codex subagents docs です。承認ポリシーは単体エージェントのツール利用だけで閉じず、委任そのものにも拡張されます。サブエージェントが親の sandbox や approval policy をどう継承するか、同時実行数やネスト深度をどう制限するかは、エージェントに「誰へ何を任せる権限を与えるか」という別レイヤーの承認問題です。KB上では、delegation chains の権限を最小化する問いとして整理されています。

3本目は OpenAI Codex plugin for Claude Code です。このソースは、同じ reviewer agent でも、使い方によって advisory review と blocking review に分かれることを明確にします。実装途中や完了前に助言を返すレビューは速度を保ちやすい一方、merge、deploy、publish のような境界に置くレビューは作業完了を止めるゲートになります。今日の compile では、この差分が「レビューのタイミング」という設計軸として取り込まれています。

関連する補助材料として、Anthropic scheduled tasks docs は recurring autonomous work における環境、connector、branch control の重要性を示し、Mercury / Zaid 周辺の材料は hard-block、明示的な tool approval、token budget、inspectable identity file をローカルエージェントの差別化要素として位置づけています。Akshay Pachaar の材料は、permissive permissions は速く感じられるが production では restrictive defaults が安全であり、tool overexposure 自体が隠れた承認・安全性リスクになる、という実務上の緊張を補っています。

KB内の概念地図としては、`approval-policy-patterns-and-escalation` が、auto-allowed actions、advisory review、blocking review、human-only execution というエスカレーション段階を明示し、`eval-review-reliability` の generator/evaluator split や `agent-deployment-gates-and-operational-risk` の operational risk とつながる形になりました。つまり、品質保証の話と権限管理の話が別々ではなく、「どこで止めるか」「何を機械的に検査するか」「どの曖昧さを人間に戻すか」という同じ設計面に載っています。

実務上の読みどころは、承認負荷を品質やレイテンシと同じく測定対象にすることです。すべてを人間承認に寄せると運用が詰まり、すべてを自動承認に寄せると被害範囲が広がります。したがって、read と bounded local inspection は安く、medium-risk changes は advisory review や branch-safe defaults へ、merge/deploy/publish/high-impact background work は blocking gate へ、繰り返し失敗や広範囲変更や不確実性上昇時には human approval へ、という運用ルールに落とすのが今日の要点です。

Podcastで掘るなら、「承認はモデル品質が上がるほど不要になるのか、それとも強いモデルほど権限設計が重要になるのか」という対立軸がよさそうです。また、classifier-mediated approval がどの程度信頼できるのか、常に block すべき行為は何か、delegation chains では権限をどう減衰させるべきか、token budget や cost ceiling を承認ポリシーに含めるべきか、という未解決問いも自然に会話にできます。

公開ページと NotebookLM Podcast では、今日の新規 raw/source 追加がないことを前提に、単なる新着紹介ではなく「compile によって approval policy の地図がどう読みやすくなったか」を中心に扱うのが適切です。特に、ハーネスエンジニアリングの中で approval policy を安全機構、レビュー機構、委任制御、運用コスト制御の交点として説明すると、KB全体の地図更新として意味が通りやすくなります。


## 重要ソース

## 更新された概念・地図

## NotebookLM Podcast用メモ

- まず今日の全体トレンドを話してから、重要ソースを3本に絞って深掘りする。
- ソース単体の紹介で終わらせず、既存KBの概念や地図がどう更新されたかを会話に含める。
- 最後に、明日以降の調査問いを2〜3個提示する。
