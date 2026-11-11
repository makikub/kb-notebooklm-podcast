# エージェントをチームで動かすとき、共有するのは何か

2026-11-11 JST / 一次情報を基にした独立して読める解説。発表内容と運用上の推論を区別する。

## 個人のエージェントから、チームの作業面へ

Cursorは11月10日、9月に始めたProjectsを複数人対応のベータへ拡張した。各人は自分のcoordinatorとworker agentとの会話を持ちながら、要件書・図面・仕様・モックなどをProjectの共有文脈に置く。共有タスクボードは人とエージェントの担当、対応するPRを同じ面に並べる。[1] これは単なるチャット共有より、作業の状態と根拠を次の担当者へ引き継ぐ設計に近い。

同社が示す例では、オンコールの交代時に未対応の問題や進行中の仕事を次の担当者のcoordinatorが把握する。別々の担当者のagentがUI変更とDBスキーマ変更の依存関係を先に調整する例もある。[1] ただし、これらはCursorの説明と社内事例であって、組織を越えた効果測定ではない。ベータは全ユーザーへ段階展開中とされる。

## モデルを強くする話とは別に評価する

Googleは同日、Gemini 4 Carbonを有料の開発者・企業向けAPIで利用可能と発表した。導入価格はArgonと同じ入力100万トークン2ドル、出力10ドル。Antigravityの複数agentを束ねる`/swarm`はプレビューであり、Cyber向け先行提供はFairwindプログラムという別の資格条件を持つ。[2] 「高性能なモデルがある」ことと「チームの誰が何を共有し、どの権限で動けるか」は異なる問いだ。

Googleが併せて発表したMKA評価は、視覚資料を扱う200タスクを共通のagent harness・ツール・サンドボックス・ターン予算で比較する。[3] ベンダーが示す順位や費用比は、その評価条件の下で読むべきで、自社のコードや業務のタスク当たり費用を直接予測しない。

Anthropicの公式Xアカウントは、Claude Whiteboards、Sheets、Dataを「本日から段階的に提供」と告知した。[4] この短い投稿は機能名と提供開始の根拠にはなるが、チーム共有のアクセス制御や全アカウントへの展開完了を裏づけない。

## 導入時の確認点

ここからは発表文からの*運用上の推論*である。チーム導入なら、(1)共有ファイル・決定・PRの権限、(2)担当交代後に古い決定を訂正・失効できるか、(3)同じ作業を同じharnessで評価したときの成功率と費用、を別々に確かめたい。共有文脈が増えるほど、誤った決定まで再利用されないよう、出典と更新責任が重要になる。

この読み筋は、KBの「Context Graph and Company Brain」マップにある、文脈の出典・有効期間・権限・訂正という視点から組み立てた。新製品の自動的な安全性を保証する主張ではない。

## 原典
- [1] [Cursor — Cursor Projects is now multiplayer](https://cursor.com/blog/projects-multiplayer)（2026-11-10、公式ブログ）
- [2] [Google — Gemini 4 Carbon is now available](https://blog.google/innovation-and-ai/models-and-research/gemini-models/gemini-4-carbon-now-available/)（2026-11-10、公式ブログ）
- [3] [Google — Introducing the Multimodal Knowledge Agent benchmark](https://blog.google/innovation-and-ai/models-and-research/gemini-models/multimodal-knowledge-agent-benchmark/)（2026-11-10、公式ブログ）
- [4] [Claude公式X — Whiteboards, Sheets and Data](https://x.com/claudeai/status/2120206365759094857)（2026-11-10、公式投稿）

KB内の根拠経路：`wiki/maps/context-graph-and-company-brain.md` → `wiki/sources/cursor-multiplayer-2026-11-10.md`、`wiki/sources/google-carbon-2026-11-10.md`、`wiki/sources/google-mka-2026-11-10.md`、`wiki/sources/claude-whiteboards-sheets-data-x-2026-11-10.md`。
