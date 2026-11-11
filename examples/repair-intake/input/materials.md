# 修理受付の業務の資料（例題の入力）

この文書は、例題のために作った架空の資料である。家電の修理を受け付ける会社が、受付の業務をシステムにしたい。要求資料に、修理依頼書の様式、画面の案、いまのシステムのテーブル、AI のプロトタイピングツールが作った試作とスキーマが付いてきた、という想定である。

## 1. 要求資料（抜粋）

- お客様は、修理依頼書を店頭か郵送で出す。
- 修理依頼書には「見積だけ」と「修理を依頼」の欄があり、どちらかに印を付ける。
- 「見積だけ」のときは、症状を見て見積の金額を連絡するだけで、修理はしない。製品はそのままお客様に返す。
- 「修理を依頼」のときは、修理して、お客様に返送する。修理の代金を請求する。返送先は、依頼書に書かれた住所とする。
- お客様の登録（お名前、住所、電話番号）は、受付担当者が行う。住所が変わったら、お客様の登録を直す。
- 修理が終わったら、修理担当者が終わったことを記録する。

## 2. 修理依頼書の様式（空の様式）

| 欄 | 書く人 |
| --- | --- |
| 「見積だけ」「修理を依頼」の印 | お客様 |
| お名前、電話番号 | お客様 |
| 製品の種類、型番、購入日 | お客様 |
| 症状 | お客様 |
| 返送先の住所 | お客様 |
| 受付日、受付印 | 受付担当者 |
| 見積の金額 | 修理担当者 |

## 3. 画面の案（受付担当者の「修理依頼の一覧」）

| 受付番号 | お客様名 | 製品 | 状況 | 前回の修理からの日数 |
| --- | --- | --- | --- | --- |
| 1201 | 山田 | 洗濯機 A-100 | 修理中 | 412 |

- 画面の上に、受付番号、お客様名で探す検索の欄がある。

## 4. いまのシステムのテーブル（既存のコード）

```sql
CREATE TABLE repair_requests (
  id              INTEGER PRIMARY KEY,
  request_type    CHAR(1) NOT NULL,   -- 'E' = 見積だけ, 'R' = 修理を依頼
  customer_id     INTEGER NOT NULL,
  product_model   VARCHAR(40) NOT NULL,
  symptom         TEXT NOT NULL,
  return_address  VARCHAR(200),       -- NULL を許す
  estimate_amount INTEGER,            -- NULL を許す
  repaired_at     TIMESTAMP,          -- NULL を許す
  updated_at      TIMESTAMP NOT NULL,
  is_deleted      BOOLEAN NOT NULL DEFAULT FALSE
);
```

- 受付のコードは、`request_type` が 'R' のときだけ、`return_address` を必須にしている。

## 5. AI のプロトタイピングツールが作った試作とスキーマ

担当者が、画面の案（§3）をツールに見せて「この画面が動くようにして」と頼んだ。ツールは画面を作り、次のテーブルを作った。

```sql
CREATE TABLE repair_list_rows (
  id                    SERIAL PRIMARY KEY,
  receipt_no            INTEGER,
  customer_name         TEXT,
  product               TEXT,
  status                TEXT,
  days_since_last_repair INTEGER
);
```
