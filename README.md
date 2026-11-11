# ドメインモデリングと文書化のパターンランゲージ

複雑な業務ルールを持つ IT システムの開発で、ドメインをモデル化し、文書にするためのパターンランゲージである。AI に文書とコードを書かせ、人が判断する開発を前提にしている。

次の三つのどの入口から入っても、同じ種類の文書が、同じ置き場に、同じ識別子で残るようにしてある。

- 整理された要求から入る
- 既存のコードから入る
- ドメインエキスパートとのワークショップから入る

## 文書

| 文書 | 中身 |
| --- | --- |
| [docs/pattern-language.md](docs/pattern-language.md) | 価値基準、大原則、36 のパターン、19 のアンチパターン |
| [docs/document-system.md](docs/document-system.md) | 文書格納体系：どの文書を、どこに、どの単位で置くか。識別子、印、判断記録、アーキテクチャ設計の置き場 |
| [docs/processes.md](docs/processes.md) | 入口ごとの手順、組み合わせ方、問いかけの型の目録 |
| [docs/notation.md](docs/notation.md) | 表記法：表、記法の部分集合と全体、論理型 |
| [docs/glossary.md](docs/glossary.md) | 用語と、区別する語 |
| [docs/related-methods.md](docs/related-methods.md) | 既知の手法との関係（採る、条件付きで採る、採らない）と参考文献 |
| [templates/](templates/) | 文書の骨組み。プロジェクトに写して使う（CC0 1.0。写すときに出典の表示は要らない） |
| [examples/order-credit/](examples/order-credit/) | 例題「受注と与信」の入力（要求資料）と、整理された要求から入る手順で書いた文書 |
| [examples/repair-intake/](examples/repair-intake/) | 例題「家電の修理受付」の入力（要求資料、帳票の様式、画面の案、いまのテーブル、AI が作った試作）と、それらを手がかりに業務の対象の形を書いた文書 |

## 読み方

| 読み手 | 読む順 |
| --- | --- |
| まず全体を知りたい人 | この README → [document-system.md](docs/document-system.md) の §1〜§3 → [pattern-language.md](docs/pattern-language.md) の §1〜§2 とパターンの一覧 |
| プロジェクトで使い始める人 | [processes.md](docs/processes.md) の自分の入口の節 → [pattern-language.md](docs/pattern-language.md) の §2.2（条件に応じて選ぶこと） → [templates/](templates/) → [document-system.md](docs/document-system.md) |
| 文書を書く AI | [templates/AGENTS.md](templates/AGENTS.md) → [document-system.md](docs/document-system.md) → [notation.md](docs/notation.md) |
| 設計の判断の理由を知りたい人 | [pattern-language.md](docs/pattern-language.md) の各パターン → [related-methods.md](docs/related-methods.md) |

## 範囲と限界

- 扱うのは、ドメインの文書の置き場と書き方、アーキテクチャ設計の置き場と最小の中身、ドメイン設計との接点である。アーキテクチャ設計の手法（技術の選び方や評価の手順）と、ドメイン駆動設計の全般の解説は扱わない。
- 戦略と組織の設計（どこに投資するか、チームをどう分けるか）は扱わない。接する所だけを、[related-methods.md](docs/related-methods.md) §5 に示す。
- パターンの確かさは、星と「確かめた範囲」で示している。星の意味は [pattern-language.md](docs/pattern-language.md) §5 にある。
- ワークショップから入る手順、画面と帳票を手がかりにする手順、既存のコードの歪みの点検表、顧客が記法の部分集合と業務の対象の形の表を読めるかどうかは、仮説である。人による試用では確かめていない。

## 関連するリポジトリ

- [fsharp-application-design](https://github.com/matarillo/fsharp-application-design)：関数型アーキテクチャの設計指針。このパターンランゲージは、文書をその設計へ写しやすくすることを、価値基準の一つにしている。
- [data-modeling-pattern-language](https://github.com/matarillo/data-modeling-pattern-language)：業務上の事実の不変性を重視するデータモデル。同じく、写しやすさを価値基準の一つにしている。
- [ddd-business-sample](https://github.com/matarillo/ddd-business-sample)、[bobs-used-bookstore-sample](https://github.com/matarillo/bobs-used-bookstore-sample)：パターンの事例として引く、公開された題材である。

## ライセンス

- 本文（`docs/`）、例題（`examples/`）、この README は [CC BY 4.0](LICENSES/CC-BY-4.0.md) で提供する。
- 雛形（`templates/`）は [CC0 1.0](LICENSES/CC0-1.0.md) で提供する。自分のプロジェクトに写して使うときに、出典の表示は要らない。
- ファイルの一覧（`publication-manifest.json`。公開するファイルごとの SHA-256 とライセンス）は [CC0 1.0](LICENSES/CC0-1.0.md) で提供する。
- 出典として挙げた第三者の著作物は、これらのライセンスの対象に含めない。
- 著作権者：Kentaro Inomata（2026 年）。告知は [LICENSE.md](LICENSE.md) にある。
