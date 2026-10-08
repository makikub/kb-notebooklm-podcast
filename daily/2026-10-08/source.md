# 公式ドキュメントに到達することと、答えを検証することは違う

2026年10月8日｜Google Developer Knowledge API の発表を、既存KBの「証拠の強さ」と「問いから辿る経路」で読む

## 今日の一次情報

Googleは2026年10月7日、Developer Knowledge APIを利用する手段として、gcloud CLI、エージェント向けスキル、クライアントライブラリ、API Explorerを紹介した。対象はGoogle Cloud、Firebase、Androidなどの開発者向け文書。APIは検索、文書のチャンク取得、Markdown形式の文書取得、文書に基づく回答の経路を提供すると説明している。[Google Developers Blog（2026-10-07）](https://developers.googleblog.com/supercharge-your-development-with-the-google-developer-knowledge-api-ecosystem/)

記事のCLI例では `answer-query`、`documents search-chunks`、`documents describe` を区別している。またスキルの取得経路は、まず `searchDocumentChunks` で関連箇所を探し、必要に応じて `documents.get` で全文を取り、あるいは `answerQuery` で文書に基づく回答を得る構成だ。これはGoogleが提供する機能・推奨フローの説明であり、任意の質問で正答や最新性が実測されたという報告ではない。[Google Developers Blog（CLI・スキル節）](https://developers.googleblog.com/supercharge-your-development-with-the-google-developer-knowledge-api-ecosystem/)

## KBの視点：検索結果から主張までを三段階に分ける

既存KBの `wiki/maps/research-os-query-paths.md` は、問いに応じてマップ→概念→強い根拠を辿り、回答に戻す経路を定義する。`wiki/maps/evidence-quality-and-source-trust.md` は、出典の種別だけでなく**その出典がその主張をどこまで支えるか**を吟味する。これらはKBの整理であり、Google APIが自動的に実現する品質保証ではない。

この二つを今回の発表に当てはめると、運用上は次の三段階を分けたい（以下は本稿の推論）。

1. **発見**：検索チャンクで候補文書を見つける。候補の存在は、問いへの回答が完成したことを意味しない。
2. **照合**：必要な文書本文を開き、製品、対象バージョン、条件、例外、文書の更新状況を確認する。検索結果の断片だけで制約を一般化しない。
3. **回答**：どの文書のどの条件に依拠したかを残し、仕様の説明と自分の環境での動作確認を区別する。文書に記載がないことは「未確認」とする。

例えばエージェントがGoogle Cloudの設定方法を問われたなら、公式文書を取得できたという事実と、自組織の設定・権限・テストでその方法が動くという事実は別々に検査する。Googleの記事は前者の取得経路を紹介するが、後者の実測結果を提供していない。[Google Developers Blog（機能と例）](https://developers.googleblog.com/supercharge-your-development-with-the-google-developer-knowledge-api-ecosystem/) この区別はKBマップを使った運用上の推論である。

## 次に試す際の確認事項

- 検索チャンクと取得した本文が、同じ対象製品・機能・条件を指しているか。
- 回答内の各重要な主張を、読者が辿れる一次文書へ戻せるか。
- 文書の説明と、手元で実行した結果や権限設定を混同していないか。
- 検索で見つからなかった条件を「存在しない」と言い切っていないか。

**公式文書への近道は、検証を省略する近道ではない。** 取得経路を整えたうえで、主張ごとの根拠と実環境での確認を残す。

## 原典・KBとの関係

- [Google Developers Blog: Supercharge your development with the Google Developer Knowledge API ecosystem](https://developers.googleblog.com/supercharge-your-development-with-the-google-developer-knowledge-api-ecosystem/)（2026-10-07）— 提供経路、対象文書、CLIコマンド、スキルの検索→取得フローを説明する公式記事。記事中の利点は提供者の説明であり、独立した精度評価ではない。
- 非公開KB `wiki/maps/research-os-query-paths.md` — 問い→マップ→概念→根拠という調査経路。
- 非公開KB `wiki/maps/evidence-quality-and-source-trust.md` および `wiki/concepts/evidence-quality.md` — 主張単位の根拠、制限、信頼度を区別する視点。
- 三段階のチェックリストと業務上の推奨は本稿の推論であり、Googleの仕様・保証として引用していない。
