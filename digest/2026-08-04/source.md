<!-- generated: 2026-08-04T13:02:09.824566+00:00 -->
<!-- kb_daily_digest_date: 2026-08-04 -->
# KB Daily Digest Source — 2026-08-04

このページは、knowledge-base-llm の日次更新を NotebookLM に読み込ませるための公開向けソースページです。
Discord通知よりも文脈を厚めに残し、Podcast化しやすいように、今日追加・更新されたソース、概念、地図を文章中心で整理します。

## 今日の全体像

# KB Daily Digest 2026-08-04

2026-08-04 UTC の knowledge-base-llm 更新は、Cursor の Google Workspace plugins に関する1件の source note が新規追加された日でした。新規 raw は `raw/x/bookmarks/bookmarks-20260804T0000Z.json` と `raw/articles/cursor-google-workspace-plugins-x-2026-08-03.md`、wiki 側には `wiki/sources/cursor-google-workspace-plugins-x-2026-08-03.md` が追加され、`wiki/INDEX.md` も更新されています。今日の promoted source は1件だけなので、重要ソース3本というよりは、1つの公式プロダクト更新を「X post」「Cursor changelog」「KB source note / bookmark batch」という3つの証拠面から読む日です。

全体トレンドは、coding agent の作業範囲がコードベース内から enterprise workspace へ広がっていることです。Cursor は Gmail、Google Drive、Calendar、Docs、Sheets、Google Chat を plugin surface として提示し、agent が読むだけでなく、書く、作成する、更新する、送る、管理するといった action を取れる形で説明しています。KB 的には「integration が増えた」というニュースではなく、agent harness の tool surface が、開発環境と業務環境をまたぐ control plane になりつつあるという signal として重要です。

重要ソース1本目は Cursor の公式 changelog、`https://cursor.com/changelog/google-workspace-plugins` です。wiki source note では evidence strength が high とされており、理由は bookmark が Cursor 自身の changelog に接続していて、対象 plugin と action が具体的に列挙されているためです。ここで読みたいのは、Google Workspace が「外部コンテキスト」ではなく「直接操作できる workspace surface」として扱われている点です。Gmail や Calendar が agent に読まれるだけなら retrieval の話ですが、draft、send、create、update、manage まで含むと、組織内の実務フローそのものが agent の作用範囲に入ります。

重要ソース2本目は Cursor / @cursor_ai の X post snapshot、`https://x.com/i/status/2084376701539405904` です。capture 時点では 2,080 likes、122 reposts、81 replies、70 quotes、321 bookmarks、93,790 impressions が記録されていました。数字そのものを過大評価する必要はありませんが、agent が Google Workspace を直接扱うという見せ方が、開発者コミュニティで強い反応を得ていることは確認できます。特に「read, write, and act」という短い表現は、今後の coding agent product がどこまで権限を持つべきかという議論を呼びやすい言葉です。

重要ソース3本目は `raw/x/bookmarks/bookmarks-20260804T0000Z.json` と、それをもとに昇格された KB source note です。この bookmark batch には複数の agent / Codex / workflow 系の話題が含まれていましたが、今日 source note として compile されたのは Cursor Google Workspace plugins だけでした。これは、KB が話題性だけでなく、既存概念に接続できる強い product signal を選別していることを示します。単なる link dump ではなく、`tool-accessibility`、`agent-management`、`managed-agents`、`worker-based-composition`、`multi-agent-orchestration` に接続できるものを採用した、という判断が残っています。

概念面では、今回の source note は `tool-accessibility` と強くつながります。tool accessibility は、agent が何を呼び出せるかだけではなく、どの surface が安全に、説明可能に、再現可能に使えるかを問う概念です。Google Workspace plugins は、メール、予定、ドキュメント、スプレッドシート、チャットという everyday work の入口を agent に開くため、便利さと危険さが同時に増えます。読み取り権限だけなら情報漏えいが中心のリスクですが、送信、更新、作成まで含むと、誤送信、予定変更、ドキュメント改変、組織内コミュニケーションへの介入が実務上の論点になります。

地図面では、`agent-harness-landscape`、`agent-harness-control-taxonomy`、`coding-agent-harness-patterns` に接続されています。今日の更新は map ファイル自体を大きく書き換えたわけではありませんが、coding agent harness の範囲を「IDE + repo + terminal」だけに閉じない材料を追加しました。agent harness は、コードを書くための補助装置から、業務アプリをまたぐ action router へ近づいています。そのとき重要になるのは、MCP-style access の有無だけでなく、認可、監査、承認、undo、dry-run、workspace ごとの境界設定です。

実務上の示唆は、workspace access を入れる時点で、agent を「便利な検索窓」ではなく「権限を持つ作業者」として扱う必要が出ることです。Gmail を読める、Docs を作れる、Calendar を更新できる、という機能は、単体ではわかりやすい価値があります。しかし現場で安全に使うには、どの操作が read-only で、どの操作が draft 止まりで、どの操作に人間承認が必要かを分けなければいけません。特に送信、共有、予定変更、ファイル移動のような reversible でない操作は、agent の能力評価よりも運用設計の問題になります。

Podcast で掘るなら、「coding agent はいつから office agent になるのか」という切り口がよさそうです。最初に Cursor の Google Workspace plugins の事実関係を説明し、次に read-only context と write/action access の違いを整理する。そのうえで、Google Workspace のような横断的な業務基盤を agent が触ると、IDE の中だけでは見えなかった guardrail、permission model、audit trail、human-in-the-loop の設計が前面に出る、という流れで話すと今日の更新の意味が伝わりやすいです。

次に追うべき問いは3つあります。第一に、Cursor の plugin 権限モデルは enterprise deploy でどこまで細かく制御できるのか。第二に、direct write access の価値は、draft / suggestion / approval workflow と比べてどれほど大きいのか。第三に、この流れは coding agent product だけでなく、general agent tool、internal agent gateway、managed agent platform にも広がるのか。今日の1件は小さな ingest ですが、KB の大きな地図では、agent の行動範囲が workspace へ拡張する転換点として読めます。

## Important Sources

- `https://cursor.com/changelog/google-workspace-plugins`
- `https://x.com/i/status/2084376701539405904`
- `raw/x/bookmarks/bookmarks-20260804T0000Z.json`

## New / Changed Files

- `raw/x/bookmarks/bookmarks-20260804T0000Z.json`
- `raw/articles/cursor-google-workspace-plugins-x-2026-08-03.md`
- `wiki/sources/cursor-google-workspace-plugins-x-2026-08-03.md`
- `wiki/INDEX.md`
- `outputs/audit/kb-static-audit-seed-2026-08-04.md`


## 重要ソース

### Cursor - Google Workspace plugins

Source note: `wiki/sources/cursor-google-workspace-plugins-x-2026-08-03.md`

# Cursor - Google Workspace plugins

## Source Metadata
- Raw path: `../../raw/articles/cursor-google-workspace-plugins-x-2026-08-03.md`
- Raw bookmark capture: `../../raw/x/bookmarks/bookmarks-20260804T0000Z.json`
- Original URL: https://x.com/i/status/2084376701539405904
- Primary URL: https://cursor.com/changelog/google-workspace-plugins
- Author: Cursor (@cursor_ai)
- Posted: 2026-08-03T20:31:46.000Z
- Captured: 2026-08-04T00:00:17.649Z via xurl bookmarks capture
- Type: X post / official product changelog
- Evidence strength: high; the bookmark points to Cursor's own changelog entry and the changelog text is specific about the available workspace surfaces
- Public metrics at capture: 2080 likes, 122 reposts, 81 replies, 70 quotes, 321 bookmarks, 93790 impressions

## Summary
Cursor's Google Workspace plugins turn email, docs, calendar, drive, sheets, and chat into directly addressable surfaces for coding agents. The KB signal here is not just "Cursor has more integrations" but that a mainstream coding agent product is now presenting enterprise productivity apps as first-class agent tools via MCP-style access.

## Key Claims
- Cursor can read, write, and act across Google Workspace.
- The plugin set covers Gmail, Google Drive, Calendar, Docs, Sheets, and Google Chat.
- The available actions include searching, reading, drafting, sending, creating, updating, and managing workspace content and events.

## Evidence / Examples
- The X post states the broad capability claim directly.
- The official Cursor changelog enumerates each plugin and the core actions they expose.
- This sits as a productized extension of earlier Google Workspace MCP coverage in the KB.

## Evidence Quality
- Source type: X post plus official Cursor changelog
- Confidence: high
- Supports: [[../con

## 更新された概念・地図

## NotebookLM Podcast用メモ

- まず今日の全体トレンドを話してから、重要ソースを3本に絞って深掘りする。
- ソース単体の紹介で終わらせず、既存KBの概念や地図がどう更新されたかを会話に含める。
- 最後に、明日以降の調査問いを2〜3個提示する。
