# 文書地図

## 置き場

```text
docs/
├─ README.md            文書地図：置き場、層と観点、識別子の一覧、読み手ごとの入口
├─ questions.md         未決事項の台帳
├─ product/             要求・要件
│   ├─ goals.md             目的、範囲、成功の観点、関わる人、優先する原則
│   ├─ quality.md           品質シナリオ
│   └─ upstream/            上流の写し（顧客の要求資料。書き換えない）
├─ domain/              ドメイン設計（顧客と共有する）
│   ├─ glossary.md          用語
│   ├─ contexts.md          サブドメイン、境界づけられたコンテキスト、コンテキストマップ、受け渡しの約束
│   ├─ facts.md             業務上の事実と、事実の流れ
│   ├─ rules.md             業務ルール、判定と許される答え、例、ルールがない領域
│   └─ lifecycles.md        業務の状態の移り変わり（状態遷移表）
└─ architecture/        アーキテクチャ設計
    └─ README.md            入口。七つの節の最小の中身
AGENTS.md               AI 向けの規律（リポジトリの直下）
```

- `decisions/`（判断記録）は、記録の線を超える最初の判断が出たときに作る。いまはない。
- `spec/`、`design/` は、機能ごとの詳細に着手するときに作る。いまはない。

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

- 境界づけられたコンテキスト、業務上の事実、業務の状態は、名前そのものを識別子として使う。名前を定義する文書は、それぞれ `domain/contexts.md`、`domain/facts.md`、`domain/lifecycles.md` である。
- 識別子の中には、業務の領域の略称を入れる。この製品では `ORDER`（受注）と `CREDIT`（与信）を使う。
- 番号は、項目を消しても再び使わない。

## 読み手ごとの入口

| 読み手 | 読む順 |
| --- | --- |
| 顧客 | `product/goals.md` → `questions.md`（決めてほしいこと） → `domain/rules.md` → `domain/lifecycles.md` |
| 開発チーム | `product/goals.md` → `domain/glossary.md` → `domain/contexts.md` → `domain/facts.md` → `domain/rules.md` → `domain/lifecycles.md` → `architecture/README.md` |
| 文書を書く AI | `../AGENTS.md` → この文書 → `questions.md` → `product/upstream/`（原文） |
