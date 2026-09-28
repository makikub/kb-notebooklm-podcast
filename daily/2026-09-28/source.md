# 画像入力の修正後、どこを再検証するか

2026年9月28日｜公式発表と一次体験から考える、コーディングエージェントの検証設計

## 何が変わったか
OpenAIは9月25日、GPT-6 Sol/Lunaの画像エンコード不具合を修正したと発表した。画像理解が劣化していた可能性があり、APIとCodexの視覚タスク（computer useを含む）への影響を示す。画像入力を含む評価と、影響を受けたワークフローの再実行を勧めている。[OpenAI API changelog](https://developers.openai.com/api/docs/changelog)

同日、AnthropicはClaudeのplugin申請ポータルを発表した。開発者はMCPコネクタやAgent Skillsをまとめて申請し、審査状況と公開後の利用分析を確認できる。有料Claudeプランの開発者向けであり、ClaudeとClaude Codeをまたぐ共通発見体験は今後数週間の展開とされる。[Anthropic公式発表](https://claude.com/blog/build-plugins-for-claude)

## 「修正された」だけで検証は終わらない
画像入力の修正は、以前の結果がすべて誤りだったことも、修正後すべて正しくなったことも証明しない。KBの 「評価・レビューの信頼性」 と 「レビュー能力と認知負債」 は、生成速度とレビュー能力を別に扱う。そこで最初の一手は、画像入力を使う評価ケースと、失敗を再現できる手順を選んで再実行することだ。これは公式の再評価勧告とKBの検証地図を合わせた**運用上の推論**であり、OpenAIが特定の再実行手順を指定したわけではない。[OpenAI API changelog](https://developers.openai.com/api/docs/changelog)

9月25日に公開されたThariqの原著X Articleは、Claude Codeのeffortをlow/mediumの実装・反復とhighの検証に使い分ける試験を紹介する。本人の試行では、難しいタスクの境界条件の検証で高effortが助けになった一方、誤ったアプローチそのものはeffort増加で直らない。これは一人の実験報告であり、OpenAIの修正に対する独立ベンチマークではない。[Thariqの原著](https://x.com/trq212/status/2103576349499855160)

## 今日使える確認の順番
1. 画像入力を含むテストと、前回失敗した実際のフローを特定する。
2. 旧結果・再実行結果・使用モデル・入力条件を並べる。改善の有無を確認するまで、修正の効果を一般化しない。
3. 生成や初期実装の速度と、境界条件の検証・人間のレビューを別枠にする。高effortを使っても、人の承認や独立した期待値を省かない。

## 配布の話は別のゲート
Claudeのpluginポータルは公開までの申請・審査と公開後の利用可視化に関する発表だ。コードや出力の正しさを保証する仕組みと読み替えない。KBの 「承認ポリシーとエスカレーション」 は、配布前の審査と実行時の承認を別のゲートとして考える。*これはKBからの解釈*であり、Anthropic発表に一般的なセキュリティ承認の自動化を示す文はない。[Anthropic公式発表](https://claude.com/blog/build-plugins-for-claude)

## 原典とKBの位置づけ
- [OpenAI API changelog（2026-09-25）](https://developers.openai.com/api/docs/changelog) — 修正の対象と再評価の勧告。
- [Anthropic「Build plugins for Claude」（2026-09-25）](https://claude.com/blog/build-plugins-for-claude) — 申請・審査・配布の仕様。
- [Thariq「Using Claude Code: Spending your effort」（X Article、2026-09-25）](https://x.com/trq212/status/2103576349499855160) — 一人の実験と運用上の提案。
- KB内の根拠: `wiki/maps/eval-review-reliability.md`、`wiki/maps/coding-agent-cognitive-debt-and-review-capacity.md`、`wiki/maps/approval-policy-patterns-and-escalation.md`。非公開KBの主張を公的な独立検証と混同しない。
