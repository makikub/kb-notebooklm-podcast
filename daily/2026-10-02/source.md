# ブラウザが使えるだけでは任せられない：エージェントの承認を三つに分ける

2026年10月2日｜OpenAIのAgents API computer useとKBの承認・デプロイゲートの整理

## 新しい操作面
OpenAIはAgents API向けのcomputer useを公式ドキュメントで案内している。エージェントはOpenAIホストのブラウザでサイトを操作できる。利用側アプリケーションはブラウザセッションを作成し、イベントを追い、サイトへのアクセス要求や必要なサインインを扱い、最後に結果を検証する。これは9月10日に公表されたAgents APIの管理された実行環境に、ブラウザ操作を加えるものだ。[OpenAI: Computer use](https://developers.openai.com/api/docs/guides/agents-api/tools/computer-use) / [OpenAI: Agents API overview](https://developers.openai.com/api/docs/guides/agents-api/overview)

## 三つのゲート
**①接続先の承認。** ガイドは新しいサイト（origin）ごとにアプリがアクセス要求を受け、承認・拒否・キャンセルを返す流れを示す。これは「そのサイトに行ってよいか」の判断だ。[公式ガイド](https://developers.openai.com/api/docs/guides/agents-api/tools/computer-use)

**②個別操作の承認。** サイトへのアクセスを承認しても、その中で行われる購入、送信、設定変更まで自動承認されたとみなすべきではない。アプリは操作の種類・対象・取り消しやすさを見て、別の人間確認または実行制限を設計する必要がある。これは公式ガイドのorigin承認フローと、KBの「Approval Policy Patterns and Escalation」を突き合わせた**編集上の提案**であり、OpenAIがすべてのサイト上の行動を自動で個別審査すると主張するものではない。[公式ガイド](https://developers.openai.com/api/docs/guides/agents-api/tools/computer-use)

**③結果の検証。** ガイドはエージェントのターン終了後に結果を検証し、保存されたブラウザ操作をレビューする段取りを記す。画面上で「完了」と見えたことと、注文・投稿・設定変更が目的どおり反映されたことは別。更新した対象を読み戻すことが実務上のゲートになる。[公式ガイド](https://developers.openai.com/api/docs/guides/agents-api/tools/computer-use)

## 導入時の小さな設計
まず読み取り専用の公開サイトを対象にし、接続先を限定する。サインインが必要なサイトでは認証フローをアプリとユーザーの管理下に置く。書き込みを許す場合は対象と操作を狭め、不可逆な操作は別途承認する。結果は当該サイトで読み戻し、失敗したときは「未確認」と記録する。この順序はKBのデプロイゲート・マップ（事前構造、実行前検証、人間へのエスカレーション、実行後観測）をブラウザ操作に適用した**推論**だ。

## 分かっていないこと
このガイドだけでは、全サイトでの成功率や個別操作を自動で止める保証は読み取れない。アクセス承認を万能な安全装置として扱わず、サイトとアクションごとのテストで確認したい。

## 原典・編集根拠
- [OpenAI: Agents API — Computer use](https://developers.openai.com/api/docs/guides/agents-api/tools/computer-use)（2026年10月2日閲覧）
- [OpenAI: Agents API overview](https://developers.openai.com/api/docs/guides/agents-api/overview)
- 非公開KB内の「Approval Policy Patterns and Escalation」「Agent Deployment Gates and Operational Risk」から構成上の視点を採用。記事は単独で理解できるよう要点を本文に記載。
