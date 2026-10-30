# 長いエージェント作業、文脈をいつ捨てるか

2026年10月30日 JST / KB日次読み物

長く続くAIエージェントの作業では、会話を長く保持すること自体が目的ではない。いまの文脈が正しいか、次の仕事と関連するかを確かめ、必要なら作業状態を外部に残して切り替える。これは非公開KBの「Context Management Decision Map」を出発点に、Anthropicの一次資料で具体化した実務上の整理だ。[1][2][3]

## 続ける、巻き戻す、要約する

同じ課題の次の一手で、会話の前提が信頼できるなら続ける。失敗した調査・実装の分岐を引きずっているなら、説明を重ねるより最後の健全な地点へ巻き戻す。履歴が長いだけなら要約（compact）も選べるが、残す情報は選別され、先の仕事に必要な細部が落ちる可能性がある。[1][2]

## 切り離す、作り直す

独立した調査や大量の中間出力は別の作業者に任せ、親の文脈を汚さない。蓄積した会話全体の信頼性が低い場合は、進捗・完了条件・検証結果をファイルやコミットに残して新しいセッションへ渡す。Anthropicの長期実装向け記事は、機能一覧、進捗記録、初期化手順などを引き継ぎの道具として挙げる。[1][2][3]

## 切り替え前に残すもの

最低限、目的、直前に確認した動作、未解決の問題、次に検証する一手を記録する。要約だけを絶対視せず、元ファイルやテスト結果に戻れるようにしておく。何をいつ切り替えるかの境界は運用上の提案であり、下記の資料が普遍的な閾値を測定した結果ではない。[1][2][3]

## 出典と限界

- [1] 非公開KB `wiki/maps/context-management-decisions.md` — continue / rewind / clear / compact / delegate / reset の判断を整理したマップ（複数資料からの統合）。
- [2] Anthropic, *Using Claude Code: session management and 1M context* — https://claude.com/blog/using-claude-code-session-management-and-1m-context 。利用方法に関する一次資料であり、各手段の比較実験ではない。
- [3] Anthropic, *Effective harnesses for long-running agents* — https://www.anthropic.com/engineering/effective-harnesses-for-long-running-agents 。引き継ぎの実装例を示すが、他の手段より常に優れていると証明するものではない。
