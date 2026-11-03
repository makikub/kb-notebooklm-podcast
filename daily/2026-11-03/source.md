# AIで実装が速くなった後、レビューをどこに置くか

2026年11月3日 JST / KB日次読み物

コード生成の速度が上がっても、何を作るか決め、なぜ安全に出せるか判断する時間は自動では短くならない。非公開KBの「Coding-Agent Cognitive Debt and Review Capacity」は、生成量が人の理解とレビュー容量を超えると、誤りだけでなく意図の欠落や判断力の低下も起こり得ると整理する。[1]

## 成果物を受け渡す

Anthropicの *The AI-native SDLC playbook*（2026年8月21日公開）は、Plan、Design、Build、Test、Deploy、Maintainを一方向の流れではなくループとして示す。重要なのは、各段階が次の人やエージェントに「コミットされた成果物」を渡すこと。意図を書いた `intent.md`、仕様と計画、コード・テスト、PRとレビュー結果、インシデント記録がその例だ。[2] 11月3日に取得したXブックマークは、この一次記事にたどり着く入口であり、投稿自体は本文の詳細を説明していない。[3]

## 速度ではなく、ゲートの設計を問う

KBの「Agent Deployment Gates and Operational Risk」は、実装前の制約、マージ前の構造チェック、デプロイ前の動作確認、人による高リスク判断、運用後の検知を別の層に分けている。[4] 例えばテストが通っていても、承認者が変更の目的や対象環境を再構成できなければ、公開判断の証拠は足りない。これはKBの整理を実務に当てはめた提案であり、Anthropic記事が効果を定量実証したという意味ではない。[1][2][4]

## まず試すこと

ひとつの変更で「意図→仕様→差分とテスト→レビューで確認したリスク→公開後に見る指標」をリンクし、レビュー時に人が理由を説明できるか確かめる。コード量やエージェント稼働数だけを成果指標にしない。[1][2][4]

## 限界

Anthropicの記事はベンダーによるプレイブックであり、全組織に同じ順序や効率が当てはまる証明ではない。レビュー容量をどう測り、どの承認ゲートが費用に見合うかは、各チームで検証が必要だ。[1][2]

## 出典

- [1] 非公開KB `wiki/maps/coding-agent-cognitive-debt-and-review-capacity.md` — 生成量・理解・レビュー容量の整理。
- [2] Anthropic, *The AI-native SDLC playbook*（2026年8月21日）— https://claude.com/resources/articles/the-ai-native-sdlc-playbook
- [3] @sivalabs の元投稿 — https://x.com/sivalabs/status/2117147655440904270
- [4] 非公開KB `wiki/maps/agent-deployment-gates-and-operational-risk.md` — 公開前後の検証・承認ゲートの整理。
