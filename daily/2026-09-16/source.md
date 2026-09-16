<!-- generated: 2026-09-16T00:50:00Z -->
<!-- primary_topic: realtime-voice-agents-and-live-apis (agent-harness-landscape + agent-harness-control-taxonomy + harness-engineering-vendor-comparison + orchestration-patterns-faq) -->
# Keep the Line Open — Live Voice after Gemini 3.8

- Date: 2026-09-16
- Theme slug: `realtime-voice-agents-and-live-apis`
- Primary topic: composite — `wiki/maps/agent-harness-landscape.md`, `wiki/maps/agent-harness-control-taxonomy.md`, `wiki/maps/harness-engineering-vendor-comparison.md`, `wiki/maps/orchestration-patterns-faq.md`（voice / Live API / speech-to-speech 専用地図は、このランでは未確認。無い wiki パスは invent しない）
- Purpose: NotebookLM向けの対話用ソース。KBのハーネス風景／制御分類／ベンダー比較／オーケストレーションFAQを、リアルタイムの音声エージェントと、Live API として読み直す。地図の再話でも、9/15 の本番信頼核の続きでも、9/14 の倉庫NL核の再審でもない
- News angle: Google Gemini 3.8 Live と Gemini 3.8 Live Extended Thinking（2026-09-15。https://blog.google/innovation-and-ai/models-and-research/gemini-models/gemini-3-8-live-gemini-3-8-live-extended-thinking/）。見出しは、より進んだ live dialogue モデルである。音声エージェントを、より直感的で知的な会話にする、と書く。3.8 Live は規模と費用効率。会話の知と、流れる対話と、視覚接地。3.8 Live Extended Thinking は高複雑度。知を上げ、多段の推論を載せる。speech-to-speech の Live モデルである。開発者向けの同伴（https://blog.google/innovation-and-ai/technology/developers-tools/build-real-time-voice-applications-gemini-audio/）は、対話を保ったまま仕事をこなす native speech-to-speech、と書く。複雑な要求には Extended Thinking。Artificial Analysis の Speech-to-Speech で首位、と書く。製品ページは Speech to Speech Quality Index 82.6 で総合1位、τ-Voice 68.6%、Sierra の τ-Voice-banking 35.1%、Big Bench Audio 97.7%、Speech Agent Arena 2位、と書く。EVA-Bench では精度と会話品質の Pareto、と書く。無い社内ベンチは足さない。視覚入力をほぼリアルタイムで処理する。97の対応言語を自動検出し、会話の途中で切り替える、と製品は書く。開発者頁は 97+、と書く。道具と API 呼び出しを背景で実行し、会話は続ける。要求を認め、仕事が終わるあいだ話し続けられる、と書く。Extended Thinking は、推論しながら同時に話す。「Let me check that…」のような早い合図。多段の背景仕事を、進行の語りで歩く。開発者頁の Live API 価格は、音声入力 $0.005/min、音声出力 $0.018/min。脚注は、$3/1M tokens 入力、$12/1M tokens 出力からの見積り、と書く。Gemini 3.5 Transcribe は先月。85+言語。WER は streaming 4.0%、non-streaming 2.6%。自動の code-switching、custom_vocabulary 最大1,000語、smart transcription、Interactions API で最大1時間のファイル。ロールアウトは Gemini API と AI Studio。Enterprise は private preview。Search Live、Gemini Live、Workspace の Docs Live / Gmail Live / Keep Live。AI 音声には SynthID 透かし。連携は Agora、Fishjam、LangChain、LiveKit、Pipecat、Vercel、Vision Agents。Salesforce、Genspark、Lumeris を挙げる。cascaded 構成の代わりに、より細い経路、と開発者頁は書く。公式本文に無い数字は足さない。aside（短い。核にしない）: Google「AI for every language」（2026-09-15。https://blog.google/innovation-and-ai/technology/ai/ai-for-every-language/）。300+言語の里程。核にしない。Pixel Drop は今日は書かない。9/15 の本番信頼核は連続の一行まで。再審しない。X bookmarks は今ラン 0（App-Only）。無い数字は足さない

## Talking points（3〜5分）

1. 9/15 は、点検を空けたあと残る点検が門を相続するかだった。今日は、会話を止めずに、道具と長い思考が同じ Live 回線に乗るかである。リードは Gemini 3.8 Live と Live API である。本番信頼の再話ではない。300+言語の再審でもない。
2. KBの問いは「声で話せるか」ではない。問いは、speech-to-speech と背景の道具と進行の語りが、同じハーネス面に乗るかである。地図は、性能はモデルだけでなく周囲の系、と書く。
3. 公式が支えるのは、native speech-to-speech、視覚接地、97言語の途中切替、背景の道具／API、Extended Thinking の同時発話、Live API の分単価、SynthID である。無いレイテンシ秒は足さない。
4. 文字起こしの WER と、Live の分単価と、Speech-to-Speech の首位は、同じ「音声」ではない。層を混ぜない。
5. 300+言語は短い aside。Pixel Drop は書かない。9/15 は連続の一行。X は 0。無い voice 専用地図は invent しない。主題は動かさない。

## 今日の読み方

knowledge-base-llm のハーネス風景は、性能がモデル単体ではなく、行動前の案内、行動後の修正、セッションをまたぐ継続、自律の制御、役割の分離で決まる、と書く。制御の分類は、「ガードレール」一語を捨て、いつ効くか（前／途中／後）と、どう効くか（決定的か、推論的か）を分けよ、と書く。ベンダー比較は、質は周囲の系である、と書く。検証はループに埋めよ。オーケストレーションFAQは、親が分解し、検証だけを割ることがあり、バスは親の指示ではない、と書く。voice / Live API / speech-to-speech の専用地図は、このランでは未確認である。無い wiki パスを invent しない。今日は、検証できた四枚を、リアルタイム音声と Live API の複合として読む。

9/15 の読み物は、点検を空けたあと残る点検が門を相続するかだった。その列は今日の核ではない。一行の連続に留める。Perplexity × Astra の本番信頼は、再審しない。今日読むのは、会話が流れているあいだ、道具と長い思考が同じ回線に乗るかである。

Google は 9/15、「Introducing Gemini 3.8 Live and 3.8 Live Extended Thinking」を出した。Tom Ouyang と Malini Jaganathan（Gemini Audio Team）が書く。ほぼリアルタイムの推論を、音声エージェントへ載せる、と書く。3.8 Live は規模と費用効率。会話の知と、流れる対話と、視覚接地。3.8 Live Extended Thinking は高複雑度。知を上げ、多段の推論を載せる。開発者と企業には、本番向け音声エージェントの部品、と書く。Gemini アプリ、Workspace、Search での発話も、より流れ、協働する、と書く。

同じ日の開発者同伴は、Alisa Fortin と Thor Schaeff が書く。Gemini API と Google AI Studio で、リアルタイムの voice-first を組む、と書く。3.8 Live は native speech-to-speech の一段。対話を保ったまま仕事をこなす。複雑な要求には Extended Thinking。Artificial Analysis の Speech-to-Speech で首位、と書く。製品ページは点数を置く。Speech to Speech Quality Index 82.6 で総合1位。τ-Voice 68.6%。Sierra の τ-Voice-banking 35.1%。Big Bench Audio 97.7%。Speech Agent Arena は2位。EVA-Bench は精度と会話品質の Pareto。Live API on Gemini Enterprise Agent Platform で走らせた、と注がある。点数表を今日の核にしない。公式が置いた数字として残す。無い社内ベンチは足さない。

視覚入力をほぼリアルタイムで処理し、会話を豊かに接地する、と書く。97の対応言語を自動検出し、会話の途中で切り替える、と製品は書く。開発者頁は 97+、と書く。97 と 97+ を、同じ「97」に潰さない。道具と API を背景で実行し、会話は続ける。要求を認め、仕事が終わるあいだ話し続けられる、と書く。開発者頁は、非同期の関数呼び出し、視覚文脈、英数字の精度、多言語、増分の内容更新、と並べる。Extended Thinking は、設定できる思考を背景に置き、本線では応答するか進行を語る。「Let me check that…」のような早い合図。スケッチとほぼリアルタイムの声から React 部品を組む例、予約と非同期関数を会話を切らずに運ぶ例を、製品は示す。cascaded 構成の代わりに、より細い経路、と開発者頁は書く。

Live API の価格は、音声入力 $0.005/min、音声出力 $0.018/min。脚注は、$3/1M tokens 入力、$12/1M tokens 出力からの見積り、と書く。無い同時接続数は足さない。Gemini 3.5 Transcribe は先月。85+言語。WER は streaming 4.0%、non-streaming 2.6%。自動の code-switching。custom_vocabulary は最大1,000語。smart transcription。Interactions API で最大1時間のファイル。タイムスタンプと話者ラベル。Live の speech-to-speech と、文字起こしの WER は、同じ「音声」ではない。

ロールアウトは今日から、と書く。開発者は Gemini API と AI Studio。企業は Gemini Enterprise の private preview。Customer Experience 向けは近日。3.8 Live は Search Live。3.8 Live Extended Thinking は Gemini Live。Workspace は、Docs が Google AI Pro / Ultra、Gmail と Keep が全 Google AI 加入、と書く。Docs Live、Gmail Live、Keep Live。AI 製品が出す音声には、SynthID の透かし。知覚できない透かしを音声へ織る、と書く。連携は Agora、Fishjam、LangChain、LiveKit、Pipecat、Vercel、Vision Agents。Salesforce、Genspark、Lumeris を挙げる。メディアストリーミングの基盤は、連携側が後ろで持つ、と書く。

薄い行だけ置く。Google「AI for every language」は 9/15。技術と製品が 300+言語の日常を支える、という里程。核にしない。Live の 97 と、会社全体の 300+ は、同じ「言語」ではない。Pixel Drop は今日は書かない。9/15 の本番信頼は、連続の一行である。再審しない。X bookmarks は今ラン 0。公式本文に無い数字は足さない。無い voice 専用地図を、あるように書かない。

今日の問いは「声で話せるか」ではない。「会話を止めずに、道具と長い思考は同じ Live 回線に乗るか」である。

## 1. speech-to-speech は、連結した耳と口ではない

開発者頁は、native speech-to-speech、と書く。対話を保ったまま仕事をこなす。cascaded 構成の代わりに、より細い経路、と書く。製品頁は、ほぼリアルタイムの推論を音声エージェントへ載せる、と書く。同じ「声」でも、耳（文字起こし）と脳（テキスト推論）と口（音声合成）を直列に繋ぐことと、一つの Live モデルが声のまま仕事することは、層が違う。

KBのハーネス風景は、性能がモデル単体ではなく周囲の系、と書く。今日の公式が固定するのは、native の Live モデルと、Live API という製品入口である。cascaded の遅延秒は、本文に無い。無い秒を invent しない。欠けを名指す。

なぜ効くか:
- 文字起こしと合成を足したものを Live と呼ぶと、回線が三つに割れる
- cascaded を「古いだけ」にすると、失敗の形が消える
- native を能力点にすると、ハーネス面が点数表になる

今日の角:
Gemini 3.5 Transcribe は、専用の speech-to-text である。85+言語。WER 4.0% / 2.6%。Live の部品ではない、とは公式は書かない。別モデルとして並べる。同じ「音声スイート」である。同じ回線ではない。今日残すのは、speech-to-speech は連結ではない、である。

対話の種:
「今日の声は、native か。連結か。」

## 2. 長い思考と会話は、同じ回線に乗る

3.8 Live Extended Thinking は、高複雑度の仕事向けである。推論しながら同時に話す、と製品は書く。早い合図は、「Let me check that…」。進行の語りは、多段の背景仕事を歩く。開発者頁は、設定できる思考を背景に置き、本線では応答するか進行を語る、と書く。会話を流したまま、複雑な仕事をこなす、と両頁が書く。

KBの制御分類は、いつ効くかを分けよ、と書く。思考は途中で効く制御になりうる。語りは、途中の観測でもある。決定的な停止ではない。公式は、思考の秒数も、いつ語りが始まるかも、書かない。無い秒を invent しない。

なぜ効くか:
- 長い思考を沈黙にすると、回線が切れたように聞こえる
- 進行の語りを答えにすると、途中経過が確定になる
- 「Let me check that…」を能力点にすると、合図が通知表になる

今日の角:
Gemini 3.8 Live は規模と費用効率。Extended Thinking は高複雑度。同じ Live 面である。同じ仕事ではない。点数表の 82.6 と 68.6% と 35.1% と 97.7% は、後者の頁が置く数字である。今日の核は首位ではない。会話が流れているあいだ、思考が同じ回線に残るか、である。

対話の種:
「今日残るのは、思考か。会話か。」

## 3. 道具は後ろで動き、声は止めない

公式は短い。道具と API 呼び出しを背景で実行し、会話は続ける。要求を認め、仕事が終わるあいだ話し続けられる、と書く。開発者頁は、非同期の関数呼び出し、と名付ける。音声応答をストリームしたまま、API と道具を背景で実行する。予約と非同期関数を、会話を切らずに運ぶ例を、製品は示す。

KBのオーケストレーションFAQは、親が分解し、結果を集め、次を決める、と書く。バスは、親が指示する流れではない。事象を公開し、購読者が拾う流れである。今日の公式は、背景の道具と、本線の声を並べる。誰が次を決めるかは、本文が置かない。無い親を invent しない。無いバスを invent しない。欠けを名指す。

なぜ効くか:
- 背景の道具を、本線の答えにすると、未完了が確定になる
- 非同期を「止まらない」一語にすると、失敗の戻り場所が消える
- 連携基盤（LiveKit や Pipecat）を Live モデルにすると、ストリーミングが能力点になる

今日の角:
ベンダー比較は、質は周囲の系である、と書く。今日の周囲は、Live API と、メディアストリーミングの連携である。Agora、Fishjam、LangChain、LiveKit、Pipecat、Vercel、Vision Agents。公式が書くのは、基盤は後ろで持つ、開発者は体験に集中できる、である。同じ「Voice agent」ではない。モデルと、API と、ストリーミング基盤は、層が違う。9/11 の管理 API 核は、今日は出さない。

対話の種:
「今日動くのは、声か。後ろの道具か。」

## 4. 視覚接地と97言語は、同じ Live 面の別入口である

製品は、視覚入力をほぼリアルタイムで処理し、会話を豊かに接地する、と書く。97の対応言語を自動検出し、会話の途中で切り替える、と書く。開発者頁は、視覚文脈と、97+言語と、アクセントの一貫、と書く。英数字の精度。確認コード、請求番号、技術データを正しく読む。オンボーディングを視覚で案内する例、チェスを視覚で指す例を、製品は示す。

同じ Live 面である。同じ入口ではない。見ることは、言語を切り替えることではない。97 と 97+ は、公式の書き分けである。無い「正確に97」を invent しない。300+言語の里程は、会社全体の aside である。Live の 97 を、300+ で上書きしない。

なぜ効くか:
- 視覚接地を多言語に潰すと、カメラが翻訳機になる
- 97 を 300+ に足すと、Live 面が会社の里程になる
- 英数字の精度を WER にすると、確認コードが文字起こしの点数になる

今日の角:
制御分類は、範囲を重ねよ、と書く。文脈（視覚）と、実行（途中切替）と、安全（透かし）は、同じ「Live」でも軸が違う。SynthID は、AI 製品が出す音声へ、知覚できない透かしを織る。誤情報を防ぐ助け、と書く。接地と、言語切替と、透かしを、同じ「信頼」にしない。9/15 の本番信頼は、今日は出さない。

対話の種:
「今日接地するのは、映像か。言語か。透かしか。」

## 5. 分単価と WER は、同じ「音声」ではない

Live API は、音声入力 $0.005/min、音声出力 $0.018/min。脚注は、$3/1M tokens 入力、$12/1M tokens 出力からの見積り、と書く。3.8 Live は費用効率、と製品は書く。Speech Agent Arena 2位のあと、費用対効果、と続ける。Extended Thinking は、競争力のある価格、と書く。分単価と、トークン見積りは、同じ頁の二つの表し方である。同じ測定ではない。

Gemini 3.5 Transcribe は先月。85+言語。WER は streaming 4.0%、non-streaming 2.6%。低遅延の文字起こし。caption、コールセンター、リアルタイムの音声分析、と開発者頁は書く。Live の speech-to-speech 点数と、Transcribe の WER は、同じ「うまさ」ではない。無いレイテンシ秒は足さない。無い同時接続数は足さない。

なぜ効くか:
- 分単価を能力点にすると、価格が首位の代わりになる
- WER を Live の会話品質にすると、文字起こしが対話になる
- 脚注のトークン見積りを、分単価の確定にすると、見積りが表価になる

今日の角:
PASS には、公式が本文で置いた数字だけを使う。82.6、68.6%、35.1%、97.7%、2位、$0.005、$0.018、$3、$12、97、97+、85+、4.0%、2.6%、1,000語、1時間。公式ページに無い測定は足さない。スイートの隣（3.5 Live Translate の 70+言語、3.1 Flash TTS、Lyria 3.5）は、開発者頁の一覧である。核に載せない。

対話の種:
「今日測るのは、分単価か。WER か。首位か。」

## 6. aside は核にしない — 欠けた地図は invent しない

「AI for every language」は 9/15 の里程である。技術と製品が 300+言語の日常を支える。核にしない。Live の 97 と、会社全体の 300+ は、同じ「言語」ではない。無い共通運用を invent しない。Pixel Drop は今日は書かない。書かないことを、あるように書かない。

9/15 の本番信頼は、連続の一行である。再審しない。点検を空けた話と、回線を切らない声は、同じ「止めない」に見える。同じ核ではない。昨日の核を今日の aside にしない。昨日の aside を今日の核にしない。

voice / Live API / speech-to-speech の専用地図は、このランでは未確認である。knowledge-base-llm はこのポッドキャスト側から開けなかった。無い wiki パスを invent しない。検証できたのは、ハーネス風景、制御分類、ベンダー比較、オーケストレーションFAQ である。無いソースノートを、あるように書かない。X bookmarks は今ラン 0。

なぜ効くか:
- 300+ を厚くすると、里程が主題になる
- Pixel を足すと、端末が主題になる
- 昨日の信頼を今日の証拠にすると、顧客文が Live の代わりになる
- 無い voice 地図を invent すると、無い編纂を足す

今日の角:
9/15 は、残る点検が門を相続するかを先に名指す話だった。今日は、会話を止めずに道具と長い思考が同じ回線に乗るかを先に名指す話である。連続である。同じ核ではない。本番信頼も、倉庫NLも、今日は出さない。

対話の種:
「欠けているのは、レイテンシか。専用地図か。ソースノートか。」

## なぜリアルタイム音声エージェントと Live API が部品になるか

- 同じ「声」でも、native speech-to-speech と、連結した cascaded は、回線が違う
- 同じ「Live」でも、規模向けの 3.8 Live と、高複雑度の Extended Thinking は、仕事が違う
- 同じ「止めない」でも、背景の道具と、本線の進行の語りは、層が違う
- 同じ「言語」でも、Live の 97 と、会社の 300+ は、入口が違う
- 同じ「音声」でも、分単価と、WER と、Speech-to-Speech の首位は、支えが違う

KBの言葉では、ハーネスは周囲の系であり、制御はいつ効くかとどう効くかを分け、質はモデルだけではない。オーケストレーションは、親と検証とバスの所在を先に名指す。Google の 3.8 Live 公式は、native speech-to-speech と、視覚接地と、97言語の途中切替と、背景の道具／API と、同時発話の Extended Thinking と、Live API の分単価と、SynthID を、一次で固定する。300+言語を aside に留め、Pixel を書かず、9/15 を一行に残し、無い voice 専用地図を空欄のまま残す。

## トレードオフ

native を厚くすると、今日の公式が「cascaded を捨てよ」チェックリストに固定される。点数表を核にすると、82.6 が主題になる。長い思考を沈黙にすると、回線が切れたように聞こえる。進行の語りを答えにすると、途中経過が確定になる。背景の道具を本線の答えにすると、未完了が確定になる。97 を 300+ に足すと、Live 面が会社の里程になる。分単価を能力点にすると、価格が首位の代わりになる。WER を会話品質にすると、文字起こしが対話になる。300+ を核にすると、里程が主題になる。9/15 の本番信頼を今日の核にすると、Live が点検間隔の続きになる。無い voice 地図を invent すると、無い編纂を足す。

だから今日の使い方は、地図を増やすことではない。回線を開けたまま、native と連結を分け、思考と会話を同じ回線に残し、道具を後ろに置き、視覚と97言語と透かしを入口で分け、分単価と WER と首位を混ぜない。本番信頼の再話にも、倉庫NLの再話にも、コーディネータの再話にもしない。

## 実務のとりはじめ

大きな基盤は要らない。今日からできる最小セット:
- 最初の一文は「会話を止めずに、道具と長い思考は同じ回線に乗るか」である。声で話せるか、から入らない
- native speech-to-speech と、cascaded の連結を、同じ「Live」に潰さない
- 3.8 Live と、Extended Thinking を、同じ「賢い声」にしない
- 背景の道具と、本線の進行の語りを、同じ「止めない」にしない
- 視覚接地と、97言語の途中切替と、SynthID を、同じ「信頼」にしない
- 分単価と、WER と、Speech-to-Speech の首位を、同じ「音声」にしない
- 97 と 97+ と 300+ を、同じ「言語数」にしない
- PASS には、公式が本文で置いた数字だけを使う。82.6、68.6%、35.1%、97.7%、$0.005、$0.018、4.0%、2.6%
- 300+言語の里程は、一行のまま核に載せない
- Pixel Drop は書かない
- 欠けた voice 専用地図を名指す。無い wiki パスを補わない
- 公式ページに無い測定は、足さない。あるのは公式 URL の本文である

9/15 は残る点検が門を相続するかを先に名指す話、今日は会話を止めずに道具と長い思考が同じ回線に乗るかを先に名指す話である。Gemini 3.8 Live の公式ページは、リアルタイム音声エージェントが Live API の入口になった、という日になる。

## 次に考えるとよさそうな問い

- 今日の声は、native か。連結か？
- 今日残るのは、思考か。会話か？
- 今日動くのは、声か。後ろの道具か？
- 今日接地するのは、映像か。言語か。透かしか？
- 今日測るのは、分単価か。WER か。首位か？
- 欠けているのは、レイテンシか。専用地図か。ソースノートか？
