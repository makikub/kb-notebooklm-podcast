# 「速いモデル」は、安いエージェントを意味しない

2026年11月19日公開。Googleは前日、Gemini 4 Neonの提供開始を告知した。入力100万トークン当たり3ドル、出力15ドル、キャッシュ入力0.15ドル。100万トークンの文脈窓と4段階のthinking levelを持つ。だが、価格表だけでエージェントの仕事が安くなるとは言えない。どのモデルを、どの実行構成で、どの品質基準に照らすかを分けて考える。

## 価格表からタスク費用へ
長時間のエージェント作業では、入力と出力の量、キャッシュの効き方、ツール呼び出し、失敗時の再試行、最終確認に使う時間が合算される。Neonの公表価格は比較の出発点だが、実際の費用はタスクの条件で変わる。Googleはデフォルトのhigh thinking levelでCarbonよりタスク当たり費用が32%低いと説明する。この数値はGoogleが示した条件に依存し、自分たちの作業で同じ削減率になるという保証ではない。

原典: https://blog.google/innovation-and-ai/models-and-research/gemini-models/introducing-gemini-4-neon/ （2026年11月18日）

## ハーネスを混同しない
GoogleはNeonを単独で走らせるだけでなく、Antigravityで複数のHydrogenサブエージェントを指揮する使い方も紹介した。同じ発表内でSWE-sweepの値がmini-SWE harnessとAntigravityとで異なると示す。これは製品全体の成績をモデル単体の能力として読めないことをよく表している。ただし差の原因をハーネスだけに帰することもできない。評価設定、ツール、試行回数まで揃えて比較する必要がある。

出典: 上記Google公式発表。比較の読み方は `wiki/maps/agent-session-runtime-economics-2026-11-17.md` の資源・行動・検証の境界に基づく編纂上の推論。

## 提供範囲と安全性を分ける
NeonはGemini APIの有料枠、Gemini for business、対象のGoogle AI Pro/Ultra加入者向けAntigravityとGeminiアプリに段階展開する。一方、サイバー向けNeonはFairwind Programの対象防御者へ数日以内の提供予定としている。一般のモデル提供と、制限付きのサイバー機能を同じ「利用可能」でまとめない。

原典: 上記Google公式発表。Googleが示す安全評価・ベンチマークの数値は、第三者による導入先での成功率を意味しない。

## 小さな比較実験
同じ実務タスクを二つか三つ選び、成功基準と停止条件を先に固定する。各モデルで総入力・出力、キャッシュ、再試行、所要時間、レビュー時間を記録する。外部への書き込みは人間の承認を要求し、実行後のログと成果物を別々に検証する。判断軸は「トークン単価」ではなく「検証済みタスク一件当たりの費用」だ。

編纂元: `wiki/maps/agent-session-runtime-economics-2026-11-17.md`、`wiki/maps/agent-deployment-gates-and-operational-risk.md`、`wiki/sources/google-gemini-4-neon-2026-11-18.md`。実験案は編纂上の推論であり、実測結果ではない。原典はGoogleの上記URL。
