# 安いモデルを選ぶ前に、成功した仕事の費用を測る

2026年11月4日 JST / KB日次読み物

モデルの単価を下げれば、エージェントの仕事も安くなるだろうか。答えは必ずしもそうではない。失敗してやり直す仕事、レビューに要する時間、待ち時間まで含めて、成果として完了した仕事を分母に置く必要がある。[1][2]

## 小さな実験が示したこと

Google Developers Blogが11月3日に公開した実験では、50問の自動採点コーディング課題を使い、軽量分類器が問題を振り分けた。Flash-Liteを先に使い、難しい課題を低thinkingのFlashへ送る構成は50問正答。低thinking Flashを最初から使う構成も50問正答だった。分類器そのものの精度が高くても、ルータを入れる便益は比較対象次第で変わる。[2]

さらに、出力上限を300トークンに狭めるだけでは簡単な課題の思考コストは下がらず、難しい課題のうち7問を壊したという。単純な上限は「思考量のつまみ」ではない。[2]

## KBのROIマップから見る

KBの「AI Adoption ROI and Capability Investment」は、生成速度やモデルの能力だけでROIを決めず、内部基盤・コンテキスト・品質ゲート・デリバリー指標を合わせて考える。Googleの実験をその地図に置けば、モデルルーティングは費用最適化の一部であり、検証や再作業の容量を超えてはいけない。[1][3]

まず同じ業務タスク群について、正答/完了率、API費用、検証と再試行、所要時間を測る。単体の軽量モデル、低thinkingモデル、必要ならルータ付き構成を同じ条件で比較する。これらはKBからの運用提案であり、Googleの実験による組織全般への効果証明ではない。[1][2][3]

## 限界

Googleの数値は50問・各設定1回・短い課題での実験。長いリポジトリ文脈を繰り返し送る実際のエージェントでは、キャッシュや課題分布が異なるため再現を確認する必要がある。[2]

## 出典

- [1] 非公開KB `wiki/maps/ai-adoption-roi-and-capability-investment.md` — 採用投資・ROIの整理。
- [2] Google Developers Blog, “Cost per task: Using cheap classifiers to route across Gemini models and thinking levels” (2026-11-03): https://developers.googleblog.com/cost-per-task-using-cheap-classifiers-to-route-across-gemini-models-and-thinking-levels/
- [3] 非公開KB `wiki/concepts/verification-tax.md` — 検証負担の概念。
