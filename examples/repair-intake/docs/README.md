# 文書地図

## 置き場

```text
docs/
├─ README.md            文書地図：置き場、層と観点、識別子の一覧、読み手ごとの入口
├─ questions.md         未決事項の台帳
├─ product/             要求・要件
│   └─ upstream/            上流の写し（要求資料の抜粋、修理依頼書の様式。書き換えない）
├─ domain/              ドメイン設計（顧客と共有する）
│   ├─ glossary.md          用語
│   ├─ contexts.md          サブドメイン、境界づけられたコンテキスト、コンテキストマップ、受け渡しの約束
│   ├─ facts.md             業務上の事実と、事実の流れ
│   ├─ things.md            業務の対象と、その形（何から成り、何で見分けるか）
│   ├─ rules.md             業務ルール、判定と許される答え、例、ルールがない領域
│   └─ lifecycles.md        業務の状態の移り変わり（状態遷移表）
├─ spec/                仕様（外部設計）
│   └─ README.md            画面の案の配置と、画面だけの項目
└─ design/              内部設計
    └─ model/               論理モデル
        ├─ 修理受付.md          既存のコードから導いた現状（as-is）
        └─ issues.md            設計課題
AGENTS.md               AI 向けの規律（リポジトリの直下）
```

- `product/goals.md`、`product/quality.md`、`architecture/`、`decisions/`、`design/model/shared.md` は、この例題が示す範囲の外なので、ない。
- `spec/` は、画面の案の配置だけを持つ。ユースケースはまだない。

## 識別子の接頭辞

| 接頭辞 | 意味 | 定義する文書 |
| --- | --- | --- |
| `Q-` | 未決事項 | `questions.md` |
| `DR-` | 判断記録。アーキテクチャに関するもの（ADR）も同じ接頭辞を使い、種別で区別する | `decisions/` |
| `QS-` | 品質シナリオ | `product/quality.md` |
| `RULE-` | 業務ルール | `domain/rules.md` |
| `JDG-` | 判定 | `domain/rules.md` |
| `UC-` | ユースケース | `spec/` |
| `SCR-` | 画面 | `spec/` |
| `AGG-` | 集約 | `design/model/` |
| `VO-` | 値 | `design/model/` |
| `OP-` | 操作 | `design/model/` |
| `INV-` | 不変条件 | `design/model/` |
| `POL-` | 差し替えられる判断 | `design/model/` |
| `ISSUE-` | 設計課題 | `design/model/issues.md` |

- 境界づけられたコンテキスト、業務上の事実、業務の対象、業務の状態は、名前そのものを識別子として使う。名前を定義する文書は、それぞれ `domain/contexts.md`、`domain/facts.md`、`domain/things.md`、`domain/lifecycles.md` である。
- 識別子の中には、業務の領域の略称を入れる。この製品では `REPAIR`（修理受付）を使う。
- 番号は、項目を消しても再び使わない。

## 読み手ごとの入口

| 読み手 | 読む順 |
| --- | --- |
| 顧客 | `questions.md`（決めてほしいこと） → `domain/facts.md`（事実の流れ） → `domain/things.md` → `domain/rules.md` → `domain/lifecycles.md` → `spec/README.md` |
| 開発チーム | `domain/glossary.md` → `domain/contexts.md` → `domain/facts.md` → `domain/things.md` → `domain/rules.md` → `domain/lifecycles.md` → `spec/README.md` → `design/model/修理受付.md` → `design/model/issues.md` |
| 文書を書く AI | `../AGENTS.md` → この文書 → `questions.md` → `product/upstream/`（原文） |
