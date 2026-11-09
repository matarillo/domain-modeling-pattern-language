# 既知の手法との関係

この文書は、背景である。このパターンランゲージが、既知の手法のどの要素を採り、どれを条件付きで採り、どれを採らないかと、その理由を示す。

- 理由は、[pattern-language.md](pattern-language.md) の価値基準の言葉で書く。
- 採った要素も、そのまま写してはいない。パターンの本文と、[document-system.md](document-system.md)、[notation.md](notation.md)、[processes.md](processes.md) の規則が、このパターンランゲージでの形である。
- 既知の手法の原典があることは、パターンの星を上げる理由にしない（[pattern-language.md](pattern-language.md) §5）。
- 原典を確かめた範囲は、参考文献の表に示す。
- 採否の区分は、採る、一部を採る（要素の一部だけを採る）、条件付き（条件を満たすときだけ採る）、採らない、の四つである。

## 1. ワークショップの手法

### 1.1 Domain Storytelling

業務を、アクター、ワークオブジェクト、アクティビティから成る文で語り、絵文字の図にする手法 [Hofer and Schwentner 2026a]。

| 要素 | 採否 | 条件と理由 | パターン |
| --- | --- | --- | --- |
| 絵文字の図と、文の文法 | 条件付き | ワークショップの会話の表記としてだけ使う。図は保存せず、事実の流れに転記する（現在の正の一意性） | MP-32 |
| 1 文ずつ描き、読み上げ、最後に語り直して同意を得る進め方 [Hofer and Schwentner 2026a] | 採る | 合意の印を付ける前の確かめ方として（合意の見分け、判断の権限） | MP-12、MP-32 |
| モデレーターの問いかけ [Hofer and Schwentner 2026a] | 採る | 問いかけの型の目録に入れる | [processes.md](processes.md) §6 |
| 前提とした仮定を注釈に明示する | 採る | 仮定は、仮説か未決事項にする（正直さ） | MP-15 |
| スコープの軸（時点、純度）[Hofer and Schwentner 2026b] | 一部を採る | 時点（現状とあるべき姿）を文書のメタデータにする。純度（業務そのものか、システムの使い方か）を、ドメイン設計と仕様の線に使う。粒度はメタデータにしない（少ない量） | MP-03、MP-11、MP-35 |
| 条件分岐を描かず、シナリオごとに描く [Hofer 2026] | 条件付き | ワークショップの進め方。事実の流れも主な流れごとに分けて書く | MP-18 |
| 境界の候補を、ドメインエキスパートに示してもらう問い [Hofer and Schwentner 2021] | 採る | 問いかけの型の目録 | MP-19 |
| 道具のファイル形式 | 採らない | 座標を含み、テキストから再生成できない（現在の正の一意性） | — |

### 1.2 EventStorming

業務上の出来事を時系列に並べ、何が次の出来事を引き起こすかを探る手法 [Brandolini 2013]、[Brandolini 2021]。

| 要素 | 採否 | 条件と理由 | パターン |
| --- | --- | --- | --- |
| 過去形の業務上の出来事 | 採る | 手法をつなぐ背骨にする（業務上の事実を軸にしたデータモデルへの写しやすさ） | MP-18 |
| 段階的な記法（最初は出来事だけ、必要になったら足す）[Avanscoperta 2025d] | 採る | 記法の部分集合と全体を分ける考えと合う（伝わりやすさ、少ない量） | MP-28 |
| Process Modelling の文法と 4 つのルール [Brandolini 2022] | 一部を採る | 文法はワークショップで使い、連鎖を事実の流れと業務ルールに転記する。ルールのうち「すべての経路を安定した状態で終わらせる」「すべての論点に対処する」を、事実の流れと状態遷移表の完全性の検査にする（業務事故の防止） | MP-23、MP-32 |
| ホットスポット [Avanscoperta 2025a] | 採る | 未決事項の台帳に転記する（正直さ） | MP-15 |
| ポリシーを「いつも」「すぐに」で問い直す [Brandolini 2022] | 採る | 問いかけの型の目録 | [processes.md](processes.md) §6 |
| ピボタルイベント [Avanscoperta 2025b] | 条件付き | 境界の候補を探すときだけ | MP-19 |
| Big Picture の進め方 [Avanscoperta 2025a] | 条件付き | 業務全体を探るとき。大人数を前提にするので、小さな規模では Process Modelling の規模で行う | — |
| 古いシステムの作者をドメインエキスパートにする危うさ [Brandolini 2016] | 条件付き | 既存のコードから入り、ワークショップと組み合わせるときの注意 | [processes.md](processes.md) §5 |
| Software Design の制約と境界 | 条件付き | チームの中で論理モデルを作るときだけ。集約は、顧客と合意するものではない（レビュー責任との一致） | MP-21 |
| 付箋の壁を成果物として残すこと | 採らない | 原典自身が、成果物より学習が主だとしている [Avanscoperta 2025c]。正本は転記した文書にする | MP-32、AP-16 |

### 1.3 具体例によるルールモデリング（Example Mapping、BDD）

ルールを具体例で確かめ、答えの出ない点を質問として残す手法 [Wynne 2015]、[Cucumber 2026b]。

| 要素 | 採否 | 条件と理由 | パターン |
| --- | --- | --- | --- |
| ルール・例・質問の組 [Wynne 2015] | 採る | 業務ルールの基本の形にする（テストへの接続、合意の見分け） | MP-27 |
| 質問カード [Wynne 2015] | 採る | 未決事項の台帳へ | MP-15 |
| 新しい機能の開発を始める直前に、少人数で行う [Cucumber 2026c] | 採る | 詳細は使う直前に決める（少ない量） | MP-30 |
| 発見と定式化を分ける [Wynne 2015]、[Cucumber 2026b] | 採る | 記法の部分集合は場の中で一緒に読み、定式化した記述は「自分ならこう書いたか」で確かめる（合意の見分け） | MP-12、MP-28 |
| 会話は記録より、記録は自動化より大事である [Cucumber 2026e] | 採る | ワークショップから入るときの順序 | MP-32 |
| 技術を前提にしない例を作る [Cucumber 2026d] | 採る | 問いかけの型の目録 | [processes.md](processes.md) §6 |
| 帰結を問う [Smart 2019] | 採る | 問いかけの型の目録 | [processes.md](processes.md) §6 |
| Gherkin [Cucumber 2026a] | 条件付き | 例を自動テストにするときだけ。顧客が読む正本にはしない（伝わりやすさ、現在の正の一意性） | MP-14 |

### 1.4 コンテキストマップと境界の約束

境界づけられたコンテキストのあいだの関係と、受け渡しを描く手法 [Evans 2015]、[Brandolini 2009]。

| 要素 | 採否 | 条件と理由 | パターン |
| --- | --- | --- | --- |
| 問いごとの小さなマップ [Brandolini 2009] | 採る | `contexts.md` は表を正本にし、図は表から描く | MP-20 |
| 関係のパターンの名前 [Evans 2015]、[DDD Crew 2020a] | 採る | 名前は顧客に伝わりにくいので、平易な説明を添える（伝わりやすさ） | MP-20 |
| 不確かな箇所の印 [Brandolini 2009] | 採る | 未決事項にする | MP-15 |
| Bounded Context Canvas [Tune et al. 2024] | 条件付き | `contexts.md` の列を確かめる表として | MP-20 |
| Domain Message Flow [DDD Crew 2020b] | 条件付き | コンテキストをまたぐ事実の流れを表で書くとき | MP-18 |
| Context Mapper の言語 [Context Mapper 2026a] | 条件付き | 道具で検証したいときだけ | — |
| Consumer-Driven Contracts [Robinson 2006] | 条件付き | 送り手と受け手が別々に変わっていくとき | MP-20 |
| 関係の種類を、チームどうしの関係としても読む [DDD Crew 2020a] | 一部を採る | `contexts.md` には、関係の種類をドメイン設計の関係としてだけ書き、チームのことは書き足さない。チームどうしの関係は、関係の種類と、境界どうしの対応の表の受け持つチームの欄を突き合わせて読み取る（レビュー責任との一致） | MP-05 |

## 2. モデルの記述の手法

### 2.1 概念モデルと戦術的な DDD

| 要素 | 採否 | 条件と理由 | パターン |
| --- | --- | --- | --- |
| 集約 [Evans 2015]、[Vernon 2011a] | 採る | 論理モデルに置く。顧客と共有しない（レビュー責任との一致） | MP-03、MP-21 |
| 小さな集約、識別子で参照する [Vernon 2011a] | 採る | 論理モデルの規則 | — |
| 境界の外は結果整合にする [Vernon 2011b] | 条件付き | 結果整合にするかは、アーキテクチャ設計で決める。一つのアプリケーションと一つのデータベースで作るなら、境界をまたいで一つのトランザクションで確定してよい（関数型アーキテクチャへの写しやすさ、業務上の事実を軸にしたデータモデルへの写しやすさ） | MP-05 |
| 「それは誰の仕事か」と問う [Vernon 2011b] | 採る | 何と何を同時に正しく保つかを、業務ルールとして聞き出す | MP-21 |
| 整合性の境界は、ドメインエキスパートとの協働で決める [Wlaschin 2024 §5.8] | 一部を採る | 業務上の整合の要求を業務の言葉で聞くことは採る。集約の境界そのものはチームが決める | MP-21 |
| Aggregate Design Canvas [DDD Crew 2022] | 条件付き | 論理モデルの集約で、書く項目を確かめる表として | — |
| 不変条件と是正の方針を対で書く [DDD Crew 2022] | 採る | 強制レベルが「強制」でない不変条件に、是正の扱いを添える（保証の見分け） | MP-13 |

### 2.2 状態とライフサイクル

| 要素 | 採否 | 条件と理由 | パターン |
| --- | --- | --- | --- |
| 状態遷移表 [ISTQB 2024] | 採る | `lifecycles.md` の正本の形。無効な遷移が空のマスとして見える（正直さ、業務事故の防止） | MP-23 |
| 状態遷移図 | 条件付き | 状態遷移表から描けるものだけ | — |
| 待ち状態を探す問い [statecharts.dev n.d.c] | 採る | 問いかけの型の目録 | [processes.md](processes.md) §6 |
| 終端の状態と、放置されたものの終わらせ方 [Chassaing 2021] | 採る | 状態遷移表に必ず書く | MP-23 |
| Decider（判断と状態の計算を分ける）[Chassaing 2021] | 条件付き | 論理モデルを関数型の設計に写すときの対応として（関数型アーキテクチャへの写しやすさ） | MP-28 |
| 状態ごとに別の型にする [Wlaschin 2013]、[Wlaschin 2018] | 採る | 記法で、状態の選択肢を `OR` で並べる | MP-28、AP-14 |
| 複合状態と並行領域 [statecharts.dev n.d.a] | 採らない | 意味が複雑になる。まず、コンテキストごとに状態遷移表を分ける（伝わりやすさ） | — |

### 2.3 意思決定と業務規則（DMN、決定表）

| 要素 | 採否 | 条件と理由 | パターン |
| --- | --- | --- | --- |
| 判定、問い、許される答え [Taylor 2023b] | 採る | 許される答えを一度だけ定義し、状態遷移と受け渡しの約束から引く（関数型アーキテクチャへの写しやすさ） | MP-22 |
| 依存であって、順序ではない [Taylor 2023a] | 採る | 判定は入力への依存で書き、手順は事実の流れに書く | MP-22 |
| 決定表、ヒットポリシー [OMG 2024]、[Vanthienen 2012a] | 採る | 既定は Unique。組み合わせの数で抜けと重なりを数える（業務事故の防止） | MP-22 |
| 業務ルールを宣言的な文で書き、例外を別のルールにする [Business Rules Group 2003] | 採る | ルールを手順に埋め込まない | MP-21 |
| 方針の文を具体例で突く問い [Ross 2024] | 採る | 問いかけの型の目録 | [processes.md](processes.md) §6 |
| ロジックの詳しさを段階で選ぶ [Taylor 2023c] | 採る | 最初は骨子と自然言語で書き、厳密な式は使う直前に書く（少ない量） | MP-30 |
| 知識源（ルールの出所）[Taylor 2023b] | 採る | ルールに出所と決定者を書く（判断の権限） | MP-12 |
| 決定要求ダイアグラム [OMG 2024] | 条件付き | 判定が別の判定に依存するときだけ。テキストの表で書く | MP-22 |
| Specification パターン [Evans and Fowler 1997] | 条件付き | 論理モデルで、差し替えられる判断として | — |

### 2.4 責任中心の設計（責務駆動設計）

| 要素 | 採否 | 条件と理由 | パターン |
| --- | --- | --- | --- |
| 責務の種類（知る、行う、決める）[Wirfs-Brock 2006] | 条件付き | 「決める」責務を、判定の置き場を考える手がかりにする | MP-22 |
| 変動点を書く技法 [Wirfs-Brock 2010] | 条件付き | 論理モデルで、差し替えられる判断を見つけるとき | — |
| CRC カードとセッション | 採らない | チームの設計の技法で、ドメインエキスパートとの協働の手法ではない（レビュー責任との一致） | — |

### 2.5 テキストの記法

| 要素 | 採否 | 条件と理由 | パターン |
| --- | --- | --- | --- |
| ドメインを AND と OR で書く記法 [Wlaschin 2024 §2.4] | 採る | 記法の部分集合と全体の元にする | MP-28 |
| 業務の概念を表すためのミニ言語 [kawasima 2021] | 採る | 記法の全体の元にする | MP-28 |
| 型を顧客向けの文書にする（コードがそのまま設計書になる）[Wlaschin 2024 ch.5] | 採らない | 実装技術に依存する。顧客が型を読めることは、確かめられていない（伝わりやすさ、合意の見分け） | MP-28 |

## 3. 文書化とアーキテクチャの記述

| 要素 | 採否 | 条件と理由 | パターン |
| --- | --- | --- | --- |
| arc42 の節 [Hruschka and Starke n.d.] | 一部を採る | アーキテクチャ設計の七つの節が、arc42 の節と多く対応する。節の構成は arc42 に置き換えず、このパターンランゲージの七つの節にする | MP-04 |
| C4 モデルのシステムコンテキスト図、コンテナ図 [Brown n.d.a]、[Brown n.d.b] | 条件付き | アーキテクチャ設計のシステムコンテキストと論理アーキテクチャの図の水準として。図はテキストの定義で書く | MP-04 |
| ADR [Nygard 2011]、MADR [ADR 2024] | 一部を採る | 判断記録の最小の形式の参考にする。記録は ADR に限らず、業務の判断も含める（判断記録の呼び分け）。記録するのは、線を超える判断だけにする | MP-07、MP-08 |
| 特性テスト [Feathers 2016] | 採る | 既存のコードを直す前に、挙動をテストで固定する | MP-33 |

## 4. 価値基準に関わるリポジトリ

このパターンランゲージは、次の二つとの写しやすさを、価値基準に含めている（[pattern-language.md](pattern-language.md) §1）。

| リポジトリ | 何か | このパターンランゲージとの関係 |
| --- | --- | --- |
| [fsharp-application-design](https://github.com/matarillo/fsharp-application-design) | 関数型アーキテクチャの設計指針 | 判断の結果を値で返す、拒否の理由を型にする、読み・判断・書き出しを分ける、という指針に写せるよう、判定と許される答え（MP-22）、取りうる形の列挙（MP-28）を書く |
| [data-modeling-pattern-language](https://github.com/matarillo/data-modeling-pattern-language) | 業務上の事実の不変性を重視するデータモデルのパターンランゲージ | 業務上の事実の分類、取消と訂正を新しい事実で表すこと、事実から状態を導くこと、時間の軸を分けること、事実の所有者と境界の間の約束に写せるよう、事実の背骨（MP-18）と受け渡しの約束（MP-20）を書く |

- **対立**：判断記録の扱いで、fsharp-application-design の文書方針と対立する。
  - fsharp-application-design は、文書方針（`[fsharp-application-design@59e827c docs/README.md]` §4）で、判断ごとの記録を標準の成果物にせず、人の明示の指示なしに AI が ADR を作ることを禁じている。
  - このパターンランゲージは、判断記録を標準の扱いにする。ただし、記録するのは、決定者が記録を求めた、線を超える判断だけにする（MP-07）。AI は、人が下した判断を書き起こしてよいが、自分の判断を記録にしない。
  - 二つは、記録の量を絞り、AI の判断を記録に紛れ込ませない点で近いが、同じではない。
- 例として、次の公開された題材を引く。
  - [ddd-business-sample](https://github.com/matarillo/ddd-business-sample)：整理された要求から書いた文書とモデルの例（版 `70819ae`）。
  - [bobs-used-bookstore-sample](https://github.com/matarillo/bobs-used-bookstore-sample)：既存のコードから導いた文書の例（版 `de81fc8` など）。

## 5. 戦略と組織の設計

Architecture for Flow は、Wardley Mapping による事業戦略、DDD によるソフトウェアの設計、Team Topologies によるチームの組織を一つにまとめ、変更が速く流れるようにシステムとチームを形づくる方法である [Kaiser 2025b]。このパターンランゲージは、戦略と組織の設計を扱わない。次の表は、その方法の要素のうち、文書の体系と接するものの採否である。

- 中身は、原著者の寄稿 [Kaiser 2023] と、キャンバスの解説 [Kaiser 2025a] で確かめた。
- 邦訳 [Kaiser 2026] の目次は、支援のサブドメインを「補助」、境界づけられたコンテキストを「境界付き文脈」と訳している。

| 要素 | 採否 | 条件と理由 | パターン |
| --- | --- | --- | --- |
| 利用者とそのニーズから始める。顧客やチームの望みを、利用者のニーズとして書かない [Wardley 2018a]、[Wardley 2018c]、[Kaiser 2025a] | 採る | `product/goals.md` の関わる人に、利用者がこのシステムでしたいことを書く（伝わりやすさ） | [document-system.md](document-system.md) §4.2 |
| サブドメインの型（中核、支援、汎用）と進化の段階で、投資と、作るか既製の製品や外部のサービスで賄うかを決める [Kaiser 2023]、[Wardley 2018b] | 一部を採る | 作るか賄うかの決定だけを、範囲の決定として `product/goals.md` に置き、論理モデルを足すかの条件に使う。型や段階から、文書の厚さを直接は決めない。文書への当てはめは、筆者の判断である（少ない量と、運用の持続性） | [pattern-language.md](pattern-language.md) §2.2 |
| 価値の連鎖の要素ごとに適切な手法を使い、全体に一つの手法を当てない [Wardley 2018c] | 一部を採る | 既製の製品や外部のサービスで賄うコンテキストには、論理モデルを作らない。受け渡しの約束は落とさない。同じ資料は、外に任せても、要素の間のつなぎ目の複雑さは消えないと述べる（少ない量と、運用の持続性。業務事故の防止） | [document-system.md](document-system.md) §4.3、§12 |
| 一つのコンテキストを一つのチームだけが持ち、一つのチームは複数を持てる [Kaiser 2023] | 採る | 境界どうしの対応の表の、受け持つチームの欄の書き方（判断の権限） | MP-05 |
| チームに受け持たせる量を認知負荷で決め、変化が多く不確かなコンテキストほど重く見る | 採らない | 変化の多さと不確かさは [Kaiser 2023] にある。それをチームの受け持つ量に結ぶことは、Architecture for Flow の原著者の講演や対談で確かめた。チームの受け持ちの決め方は組織の設計で、このパターンランゲージの扱う範囲の外である | — |
| コンテキストを、所有の境界だけでなく、物理的な境界にもする（Architecture for Flow の原著者の講演や対談で確かめた） | 条件付き | 物理的な境界にするかは、境界どうしの対応の表で選ぶ。一つのアプリケーションと一つのデータベースで作るなら、分けなくてよい（関数型アーキテクチャへの写しやすさ、業務上の事実を軸にしたデータモデルへの写しやすさ） | MP-05 |
| 現状の評価と、思い描く状況の設計を、協働して反復的に進める [Kaiser 2025a]。進化を一歩ずつ描く [Team Topologies 2025b]。一括で置き換えず、段階的に移す（Architecture for Flow の原著者の講演や対談で確かめた） | 一部を採る | 思い描く全体の姿は話してよいが、文書に書くのは次の段階だけで、ブランチに書く。段階の順序は計画の道具に置く（現在の正の一意性） | MP-35 |
| Wardley Map [Wardley 2018a]、Architecture for Flow Canvas [Kaiser 2025a] | 採らない | 戦略と組織の設計の手法で、このパターンランゲージの扱う範囲の外。その作成物を、このパターンランゲージの文書にしない（少ない量と、運用の持続性） | — |
| チームの種類とインタラクションモード [Team Topologies 2025a] | 採らない | 組織の設計で、このパターンランゲージの扱う範囲の外 | — |

- チームが扱える複雑さには限りがある、というチームの認知負荷の考え [Team Topologies 2025a] は、文書の量を、読み、保守する人の力量に合わせる価値基準（少ない量と、運用の持続性）に近い。ただし、認知負荷はチームが受け持つ範囲の話で、文書の量の話ではない。
- システムの構造は、設計した組織の通信の構造を写す [Conway 1968]。境界どうしの対応の表が、受け持つチームの欄を持つ背景である。

## 参考文献

確かめた範囲は、原典のどこまでを読んだかである。「書誌」は、書誌情報だけを確かめたことを表す。

| キー | 著者 | 題名 | 年 | 種類 | URL | 確かめた範囲 |
| --- | --- | --- | --- | --- | --- | --- |
| ADR 2024 | ADR GitHub organization | MADR（Markdown Architectural Decision Records）4.0.0 | 2024 | web | https://adr.github.io/madr/ | 現行の版、対象 |
| Avanscoperta 2025a | Avanscoperta | EventStorming | 2025 | web | https://www.avanscoperta.it/en/eventstorming/ | 全文 |
| Avanscoperta 2025b | Avanscoperta | Pivotal Events | 2025 | web | https://www.avanscoperta.it/en/eventstorming/pivotal-events/ | 全文 |
| Avanscoperta 2025c | Avanscoperta | Antipattern: Deliverable Obsession | 2025 | web | https://www.eventstorming.com/patterns/deliverable-obsesssion/ | 全文 |
| Avanscoperta 2025d | Avanscoperta | Pattern: Incremental Notation | 2025 | web | https://www.eventstorming.com/patterns/incremental-notation/ | 全文 |
| Brandolini 2009 | Alberto Brandolini | Strategic Domain Driven Design with Context Mapping | 2009 | article | https://www.infoq.com/articles/ddd-contextmapping/ | 全文 |
| Brandolini 2013 | Alberto Brandolini | Introducing Event Storming | 2013 | blog | http://ziobrando.blogspot.com/2013/11/introducing-event-storming.html | 全文 |
| Brandolini 2016 | Alberto Brandolini | The rise and fall of the Dungeon Master | 2016 | blog | https://medium.com/@ziobrando/the-rise-and-fall-of-the-dungeon-master-c2d511eed12f | 全文 |
| Brandolini 2021 | Alberto Brandolini | Introducing EventStorming（公式サンプル） | 2021 | book | https://leanpub.com/introducing_eventstorming/sample.pdf | サンプルの範囲 |
| Brandolini 2022 | Alberto Brandolini | Collaborative Process Modelling with EventStorming | 2022 | blog | https://medium.com/@ziobrando/collaborative-process-modelling-with-eventstorming-17ed363650c0 | 全文 |
| Brown n.d.a | Simon Brown | C4 model: System Context diagram | — | web | https://c4model.com/diagrams/system-context | 全文 |
| Brown n.d.b | Simon Brown | C4 model: Container diagram | — | web | https://c4model.com/diagrams/container | 全文 |
| Business Rules Group 2003 | Business Rules Group | The Business Rules Manifesto, Version 2.0 | 2003 | spec | https://www.businessrulesgroup.org/brmanifesto.htm | 全文 |
| Chassaing 2021 | Jérémie Chassaing | Functional Event Sourcing Decider | 2021 | blog | https://thinkbeforecoding.com/post/2021/12/17/functional-event-sourcing-decider | 全文 |
| Context Mapper 2026a | Context Mapper | Context Mapper: Welcome | 2026 | tool-doc | https://contextmapper.org/docs/home/ | 全文 |
| Conway 1968 | Melvin E. Conway | How Do Committees Invent? | 1968 | paper | https://www.melconway.com/Home/Committees_Paper.html | 全文 |
| Cucumber 2026a | Cucumber Open Source Project | Gherkin Reference | 2026 | tool-doc | https://cucumber.io/docs/gherkin/reference/ | 全文 |
| Cucumber 2026b | Cucumber Open Source Project | Behaviour-Driven Development | 2026 | tool-doc | https://cucumber.io/docs/bdd/ | 全文 |
| Cucumber 2026c | Cucumber Open Source Project | Discovery workshop | 2026 | tool-doc | https://cucumber.io/docs/bdd/discovery-workshop/ | 全文 |
| Cucumber 2026d | Cucumber Open Source Project | Examples | 2026 | tool-doc | https://cucumber.io/docs/bdd/examples/ | 全文 |
| Cucumber 2026e | Cucumber Open Source Project | Myths about BDD | 2026 | tool-doc | https://cucumber.io/docs/bdd/myths/ | 全文 |
| DDD Crew 2020a | DDD Crew | Context Mapping | 2020 | web | https://github.com/ddd-crew/context-mapping | 全文 |
| DDD Crew 2020b | DDD Crew | Domain Message Flow Modelling | 2020 | web | https://github.com/ddd-crew/domain-message-flow-modelling | 全文 |
| DDD Crew 2022 | DDD Crew | Aggregate Design Canvas | 2022 | web | https://github.com/ddd-crew/aggregate-design-canvas | 全文 |
| Evans 2015 | Eric Evans | Domain-Driven Design Reference: Definitions and Pattern Summaries | 2015 | book | https://www.domainlanguage.com/wp-content/uploads/2016/05/DDD_Reference_2015-03.pdf | 全文 |
| Evans and Fowler 1997 | Eric Evans、Martin Fowler | Specifications | 1997 | paper | https://martinfowler.com/apsupp/spec.pdf | 全文 |
| Feathers 2016 | Michael Feathers | Characterization Testing | 2016 | blog | https://michaelfeathers.silvrback.com/characterization-testing | 全文 |
| Hofer 2026 | Stefan Hofer | How to Model Repeating Activities | 2026 | web | https://domainstorytelling.org/articles/how-to-model-loops/ | 全文 |
| Hofer and Schwentner 2021 | Stefan Hofer、Henning Schwentner | How to Find Boundaries for Modules, Microservices, or Bounded Contexts | 2021 | article | https://www.informit.com/articles/article.aspx?p=3124864 | 全文 |
| Hofer and Schwentner 2026a | Stefan Hofer、Henning Schwentner | Domain Storytelling — Quick-Start Guide | 2026 | web | https://domainstorytelling.org/quick-start-guide | 全文 |
| Hofer and Schwentner 2026b | Stefan Hofer、Henning Schwentner | Requirements with Domain Storytelling | 2026 | web | https://domainstorytelling.org/requirements | 全文 |
| Hruschka and Starke n.d. | Peter Hruschka、Gernot Starke | arc42 | — | web | https://docs.arc42.org/home/ | 節の名前 |
| ISTQB 2024 | ISTQB | Certified Tester Foundation Level Syllabus v4.0.1（4.2.4 State Transition Testing） | 2024 | spec | https://www.istqb.org/wp-content/uploads/2024/11/ISTQB_CTFL_Syllabus_v4.0.1.pdf | 該当の節 |
| Kaiser 2023 | Susanne Kaiser | Adaptive, Socio-Technical Systems with Architecture for Flow: Wardley Maps, DDD, and Team Topologies | 2023 | article | https://www.infoq.com/articles/adaptive-socio-technical-systems-flow/ | 全文 |
| Kaiser 2025a | Susanne Kaiser | The Architecture for Flow Canvas | 2025 | web | https://architectureforflow.com/canvas/ | 全文 |
| Kaiser 2025b | Susanne Kaiser | Architecture for Flow: Adaptive Systems with Domain-Driven Design, Wardley Mapping, and Team Topologies | 2025 | book | https://architectureforflow.com/ | 書誌、目次、序文（出版社のプレビュー）。本文は確かめていない |
| Kaiser 2026 | Susanne Kaiser（著）、角征典（訳） | フロー指向アーキテクチャ | 2026 | book | https://www.ohmsha.co.jp/book/9784274235634.html | 書誌、詳細目次。発売予定日は 2026-11-17（2026-11-09 に確かめた） |
| kawasima 2021 | kawasima | ドメイン記述ミニ言語 | 2021 | web | https://scrapbox.io/kawasima/%E3%83%89%E3%83%A1%E3%82%A4%E3%83%B3%E8%A8%98%E8%BF%B0%E3%83%9F%E3%83%8B%E8%A8%80%E8%AA%9E | 冒頭と記法の要素 |
| Nygard 2011 | Michael Nygard | Documenting Architecture Decisions | 2011 | blog | https://cognitect.com/blog/2011/11/15/documenting-architecture-decisions | 全文 |
| OMG 2024 | Object Management Group | Decision Model and Notation (DMN) Version 1.5 | 2024 | spec | https://www.omg.org/spec/DMN/1.5/PDF | 決定要求ダイアグラム、ヒットポリシーの章 |
| Robinson 2006 | Ian Robinson | Consumer-Driven Contracts: A Service Evolution Pattern | 2006 | article | https://martinfowler.com/articles/consumerDrivenContracts.html | 全文 |
| Ross 2024 | Ronald G. Ross | The Five Basic Skills of Discovering and Expressing Rules | 2024 | article | https://brcommunity.com/articles.php?id=c138 | 全文 |
| Smart 2019 | John Ferguson Smart | Feature Mapping – a lightweight requirements discovery practice | 2019 | blog | https://johnfergusonsmart.com/feature-mapping-a-lightweight-requirements-discovery-practice-for-agile-teams/ | 全文 |
| statecharts.dev n.d.a | statecharts.dev | What is a statechart? | — | web | https://statecharts.dev/what-is-a-statechart.html | 全文 |
| statecharts.dev n.d.c | statecharts.dev | All states are explored | — | web | https://statecharts.dev/benefit-all-states-explored.html | 全文 |
| Taylor 2023a | James Taylor | Decision Modeling: Finding and modeling decisions | 2023 | blog | https://community.ibm.com/community/user/blogs/james-taylor/2023/11/29/decision-modeling-finding-and-modeling-decisions | 全文 |
| Taylor 2023b | James Taylor | Decision Modeling: Decision Requirements | 2023 | blog | https://community.ibm.com/community/user/blogs/james-taylor/2023/11/08/decision-modeling-decision-requirements | 全文 |
| Taylor 2023c | James Taylor | Decision Modeling: Decision Logic | 2023 | blog | https://community.ibm.com/community/user/blogs/james-taylor/2023/11/16/decision-modeling-decision-logic | 全文 |
| Team Topologies 2025a | Team Topologies | Key concepts and practices for applying a Team Topologies approach to team-of-teams org design | 2025 | web | https://teamtopologies.com/key-concepts | 全文 |
| Team Topologies 2025b | Team Topologies | Team Interaction Modeling with Team Topologies | 2025 | web | https://teamtopologies.com/key-concepts-content/team-interaction-modeling-with-team-topologies | 全文 |
| Tune et al. 2024 | Nick Tune ほか | The Bounded Context Canvas | 2024 | web | https://github.com/ddd-crew/bounded-context-canvas | 全文 |
| Vanthienen 2012a | Jan Vanthienen | The History of Modeling Decisions using Tables (Part 3) | 2012 | article | https://www.brcommunity.com/articles.php?id=b652 | 全文 |
| Vernon 2011a | Vaughn Vernon | Effective Aggregate Design Part I: Modeling a Single Aggregate | 2011 | paper | https://www.dddcommunity.org/wp-content/uploads/files/pdf_articles/Vernon_2011_1.pdf | 全文 |
| Vernon 2011b | Vaughn Vernon | Effective Aggregate Design Part II: Making Aggregates Work Together | 2011 | paper | https://www.dddcommunity.org/wp-content/uploads/files/pdf_articles/Vernon_2011_2.pdf | 全文 |
| Wardley 2018a | Simon Wardley | Wardley Maps, Chapter 2: Finding a path | 2018 | book | https://medium.com/wardleymaps/finding-a-path-cdb1249078c0 | 章の全文 |
| Wardley 2018b | Simon Wardley | Wardley Maps, Chapter 3: Exploring the map | 2018 | book | https://medium.com/wardleymaps/exploring-the-map-ad0266fad59b | 章の全文 |
| Wardley 2018c | Simon Wardley | Wardley Maps, Chapter 4: Doctrine | 2018 | book | https://medium.com/wardleymaps/doctrine-8bb0015688e5 | 章の全文 |
| Wirfs-Brock 2006 | Rebecca Wirfs-Brock | A Brief Tour of Responsibility-Driven Design | 2006 | slides | https://www.wirfs-brock.com/PDFs/A_Brief-Tour-of-RDD.pdf | 全文 |
| Wirfs-Brock 2010 | Rebecca Wirfs-Brock | Understanding Design Complexity | 2010 | slides | https://wirfs-brock.com/PDFs/UnderstandingDesignComplexity.pdf | 全文 |
| Wlaschin 2013 | Scott Wlaschin | Designing with types: Making state explicit | 2013 | blog | https://fsharpforfunandprofit.com/posts/designing-with-types-representing-states/ | 全文 |
| Wlaschin 2018 | Scott Wlaschin | Domain Modeling Made Functional | 2018 | book | https://pragprog.com/titles/swdddf/domain-modeling-made-functional/ | 書誌 |
| Wlaschin 2024 | Scott Wlaschin（著）、猪股健太郎（訳） | 関数型ドメインモデリング | 2024 | book | https://tatsu-zine.com/books/domain-modeling-made-functional | 本文。節の番号はこの訳書による |
| Wynne 2015 | Matt Wynne | Introducing Example Mapping | 2015 | blog | https://cucumber.io/blog/bdd/example-mapping-introduction/ | 全文 |

### 原著者の講演と対談の記録

Architecture for Flow [Kaiser 2025b] の原著者の講演と対談の記録である。本文で「Architecture for Flow の原著者の講演や対談で確かめた」とした考えは、これらで確かめた。本文では、出典として引かない。

| キー | 著者 | 題名 | 年 | 種類 | URL | 確かめた範囲 |
| --- | --- | --- | --- | --- | --- | --- |
| Kaiser 2022 | Susanne Kaiser | Architecture for Flow w/ Wardley Mapping, DDD, and Team Topologies（QCon Plus の講演） | 2022 | talk | https://www.infoq.com/presentations/ddd-wardley-mapping-team-topology/ | 書き起こしの全文 |
| Kaiser and Humble 2022 | Susanne Kaiser、Charles Humble | Joining the Dots Between Wardley Mapping, Domain Driven Design and Team Topologies | 2022 | podcast | https://blog.container-solutions.com/susanne-kaiser-wardley-mapping-domain-driven-design-team-topologies | 書き起こしの全文 |
| Kaiser and Reisz 2022 | Susanne Kaiser、Wes Reisz | Susanne Kaiser on DDD, Wardley Mapping, and Team Topologies | 2022 | podcast | https://www.infoq.com/podcasts/ddd-wardley-mapping-team-topologies/ | 書き起こしの全文 |
| Kaiser and Suryawirawan 2022 | Susanne Kaiser、Henry Suryawirawan | Adaptive Systems with Wardley Mapping, Domain-Driven Design, and Team Topologies | 2022 | podcast | https://techleadjournal.dev/episodes/86/ | 書き起こしの全文 |
| Kaiser 2025c | Susanne Kaiser | Evolving a Legacy System w/ Architecture for Flow（講演のスライド） | 2025 | slides | https://susannekaiser.net/conferences/slides/codecrafts-2025.pdf | スライドの文字 |
| Kaiser and Lewis 2026 | Susanne Kaiser、James Lewis | GOTO Book Club: Architecture for Flow | 2026 | podcast | https://gotopia.tech/episodes/424/architecture-for-flow | 書き起こしの全文 |
