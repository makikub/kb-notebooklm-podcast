# バックグラウンドで動くAIに必要なのは、操作の速さより承認の境界

2026年11月20日。Googleが前日に発表したGeminiアプリMac版のcomputer useは、ファイル、デスクトップアプリ、Webをまたぐ操作をバックグラウンドで実行する。隔離されたウィンドウで動き、メイン画面とカーソルを占有しない。利用者はアクセスできるアプリを選び、ライブプレビューを見て一時停止し、重要な操作を承認する。提供は米国・英語からの段階展開だ。[1]

## 「見える」と「止められる」は違う

プレビューは行動を観察する手段であり、承認は実行前の境界である。たとえば配送フォームの入力をAIに任せる場合、PDFの読取りと下書き作成は比較的戻しやすい。しかし外部への送信、購入、共有範囲の変更は結果が外へ広がる。Googleの発表にはフォーム入力や出品下書きなどの例がある一方、どの行為が「重要な操作」に当たり必ず確認されるか、その一覧や実測の安全性は示されていない。[1]

この読み方は非公開KBの`wiki/maps/agent-deployment-gates-and-operational-risk.md`と`wiki/maps/approval-policy-patterns-and-escalation.md`からの編纂上の推論である。両マップは構造チェック、実行前承認、実行後の検出を別の層として整理している。製品に同じ仕組みが実装されていると断定するものではない。

## 小さく試すなら

まず外部送信を伴わないサンプルファイルで、指定アプリだけに許可し、下書きが期待通り作られるか観察する。次に誤った入力、キャンセル、承認待ちの表示を確かめる。最後に外部作用を含む本番作業へ広げる場合は、操作を止める権限と結果の読み戻しを確認する。これは導入実験の提案であって、Googleの品質保証ではない。

## 関連する別の変化

OpenAIの11月19日付API変更履歴はGPT-Live-1.1と、WebRTCの非アクティブ時に推論を一時停止して発話で再開するstandby設定を記す。[2] セッションを「裏で続ける」か「待機させる」かは資源の問題、コンピューター操作を「実行してよい」かは権限の問題。二つの変更を同じ自動化機能として混同しない。standbyの実際の費用・復帰時間は、この変更履歴だけでは分からない。[2]

## 出典と編纂元

[1] Google, “Let Gemini tackle repetitive chores on your Mac,” 2026-11-19. https://blog.google/innovation-and-ai/products/gemini-app/computer-use-mac/
[2] OpenAI API Changelog, 2026-11-19. https://developers.openai.com/api/docs/changelog.md

編纂元（非公開KB内の参照位置）: `wiki/sources/google-gemini-mac-computer-use-2026-11-19.md`, `wiki/sources/openai-api-live-2026-11-19.md`, `wiki/maps/agent-deployment-gates-and-operational-risk.md`, `wiki/maps/approval-policy-patterns-and-escalation.md`。この読み物は原典を上記に明記した独立した要約であり、非公開のブックマーク原文を転載していない。
