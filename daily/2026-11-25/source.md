# 引用付き検索とエージェントの権限境界｜2026-11-25

## なぜ今読むか
GoogleのAgent RetrievalではManaged IngestionとSearchDocumentsがPublic Previewとして紹介された。ファイルを取り込んで引用付きで探す導線が短くなる一方、情報を誰が読み、どのツールが外部に作用できるかは別の設計課題だ。

## 一次情報から分かること
- Googleの発表はManaged Ingestion / SearchDocumentsをPublic Previewとして示す。提供状況とAPI動作の詳細は[公式記事](https://developers.googleblog.com/from-files-to-cited-answers-in-one-api-call-managed-ingestion-and-searchdocuments-in-agent-retrieval/)で確認する。
- [Google Cloudの内部Cloud Run MCP接続ガイド](https://developers.googleblog.com/en/how-to-securely-connect-internal-cloud-run-mcp-servers-to-gemini-enterprise/)は、ネットワーク到達性、Cloud Run IAM、ユーザーOAuthを別の層として説明する。設計例であって全組織に安全性を保証する評価ではない。

## 実務への読み替え（推論）
引用の表示と、引用元をそのユーザーが閲覧してよいことは同じではない。検証は①検索対象の権限継承と失効反映、②サービスとユーザーのID、③書き込みツールの操作前承認、④実行結果と監査記録に分ける。Preview導入前に異なる権限のテストアカウントで拒否系を試す。

## 未確認
Agent Retrievalの実環境での検索精度、権限継承、失効反映速度は今回測定していない。Googleの2つの文書を組み合わせた運用上の論点であり、単一の製品が全てを自動で実装すると主張しない。

## 根拠
- Google Developers Blog（2026-11-24）: https://developers.googleblog.com/from-files-to-cited-answers-in-one-api-call-managed-ingestion-and-searchdocuments-in-agent-retrieval/
- Google Cloud Blog: https://developers.googleblog.com/en/how-to-securely-connect-internal-cloud-run-mcp-servers-to-gemini-enterprise/
- KB map（private）: `wiki/maps/private-mcp-boundaries-2026-11-23.md`
