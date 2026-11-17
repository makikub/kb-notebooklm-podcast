# AIエージェントを長く動かす前に：費用、行動、検証の三つの境界

2026年11月17日。長く動くcoding agentを増やすとき、何を保ち、何を止め、何を確かめるのか。Googleの11月16日公開記事2本とClaude Codeチームの実践記事を、既存KBの運用ゲートに接続する。各社の試算・内部報告と実測結果は分けて読む。

## 1. セッションは続け、計算資源は休ませる

Googleは利用者との複数ターンのsessionと、コードを実行するsandbox/workerを分ける。Agent Substrateのactorをidle時にobject storageへsuspendし、workerを再利用する。AXのTaskはファイルを復元できるが、現時点のresumeではプロセスは再起動する。よって「会話の連続性」と「プロセスの継続」は同義ではない。[1]

Googleの試算は、100 coding agents、毎時2 prompts、2分のidle timeoutなどを置き、専用Pod方式に比べnode費用40%減とする。毎時4 promptsでは削減4%、約4.5 promptsで逆転するモデル。CPU requestを下げるovercommitを考慮すると、専用Podが安くなる場合もある。*40%はGoogleの仮定付きモデルで、一般的な節約率ではない。* [1]

## 2. 行動の逸脱は、稼働後にも見る

GoogleのAgent Anomaly DetectionはPrivate Preview。11月16日の手順書は、意図的に権限過大なサポートagentを用い、正常な注文照会と給与情報へ逸脱するsessionを別々に流す。ログ/traceから後者を検知し、Cloud MonitoringやSecurity Command Centerへ通知する例だ。[2] 9月の発表は仕組みの公開、11月の手順は導入・検証方法の追加である。[4]

このデモは検知成功の実例だが、全ての逸脱を止める証拠ではない。監視の前に権限を絞ることが第一。しかもpromptと応答内容のtelemetryを有効化するので、保存地域、機密データ、権限を先に審査する。[2]

## 3. 生成コードは実行した証拠で判断する

Claude Codeチームは、E2E、性質テスト、旧実装とのdifferential test、実アプリの動作確認を組み合わせる。差分に応じてチェックを選び、3回なお失敗したら人に渡す。レビュー規則はPR内の改変から隔離し、古いcommitを対象にした合格を無効とする。[3]

チームが報告するコード作成・レビューの約90%や内部graderの改善は、当事者の運用例だ。自社の品質を保証しない。KBのreview rubricも、正しさ、安全性、テスト、理解可能性を別々に問う。[3][5]

## 運用への含意（筆者の推論）

計算資源を止めてもsessionを復元できる設計、行動の異常を後から見つける仕組み、変更の前にテストと実行で立証する仕組みは代替関係にない。まずpeak hourの利用頻度を測り、権限とtelemetryの範囲を定義し、レビューの対象commitを固定する。費用削減、検知率、品質向上はそれぞれ別の指標で検証する。[1][2][3][5]

## 原典・KB

[1] Google Developers, “Agents are sessions, not requests” (2026-11-16): https://developers.googleblog.com/agents-are-sessions-not-requests-size-gke-node-pools-for-ai-agent-sessions/  
[2] Google Developers, “Securing Your Agents” (2026-11-16): https://developers.googleblog.com/securing-your-agents-a-hands-on-guide-to-agent-anomaly-detection/  
[3] Addy Osmani / Claude developer blog, “How the Claude Code team thinks about verification” (2026-11-16): https://claude.dev/blog/how-the-claude-code-team-thinks-about-verification/  
[4] Private KB: `wiki/sources/google-agent-anomaly-detection-private-preview-2026-09-16.md`  
[5] Private KB: `wiki/maps/agent-session-runtime-economics-2026-11-17.md`, `wiki/maps/coding-agent-review-rubric.md`。一次情報は[1]–[3]。
