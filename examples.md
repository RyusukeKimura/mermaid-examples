# Mermaid サンプル集

参考スライドのコードを収録しています。日程・数値は説明用の例です。

## 申請・承認フロー

ソース: [01-flowchart.mmd](01-flowchart.mmd) ／ 参考スライド 25 ページ

```mermaid
flowchart LR
  A[申請] --> B{承認?}
  B -->|はい| C[実行]
  B -->|いいえ| D[差戻し]
  D --> A
```

## 受付を追加したフロー

ソース: [02-flowchart-reception.mmd](02-flowchart-reception.mmd) ／ 参考スライド 4 ページ

```mermaid
flowchart LR
  A[申請] --> E[受付]
  E --> B{承認?}
  B -->|はい| C[実行]
  B -->|いいえ| D[差戻し]
  D --> A
```

## 画面とサーバー

ソース: [03-subgraph.mmd](03-subgraph.mmd) ／ 参考スライド 28 ページ

```mermaid
flowchart LR
  subgraph Front[画面]
    Web[Web]
    App[アプリ]
  end
  subgraph Back[サーバー]
    API[API] --> DB[(DB)]
  end
  Web --> API
  App --> API
```

## 問い合わせの順序

ソース: [04-sequence.mmd](04-sequence.mmd) ／ 参考スライド 29 ページ

```mermaid
sequenceDiagram
  actor U as 利用者
  participant S as サーバー
  U->>+S: 問い合わせ
  S-->>-U: 結果
  Note over U,S: 通信の順序
```

## 正常系と例外処理

ソース: [05-sequence-alt.mmd](05-sequence-alt.mmd) ／ 参考スライド 31 ページ

```mermaid
sequenceDiagram
  participant C as Client
  participant A as API
  C->>A: データ取得
  alt 見つかった
    A-->>C: 200 OK
  else 見つからない
    A-->>C: 404 Not Found
  end
```

## 会員と予約のクラス図

ソース: [06-class.mmd](06-class.mmd) ／ 参考スライド 32 ページ

```mermaid
classDiagram
  class Member {
    +String name
    +reserve() void
  }
  class Reservation
  Member "1" --> "*" Reservation : creates
```

## 予約の状態遷移

ソース: [07-state.mmd](07-state.mmd) ／ 参考スライド 34 ページ

```mermaid
stateDiagram-v2 
  state "受付" as Accepted
  state "確定" as Confirmed
  state "中止" as Canceled
  state "完了" as Completed

  [*] --> Accepted
  Accepted --> Confirmed: 承認
  Accepted --> Canceled: 取消
  Confirmed --> Completed: 実施
  Completed --> [*] 
  Canceled --> [*]
```

## 会員と予約のER図

ソース: [08-er.mmd](08-er.mmd) ／ 参考スライド 35 ページ

```mermaid
erDiagram
  MEMBER ||--o{ BOOKING : makes
  MEMBER {
    int id PK
    string email UK
  }
  BOOKING {
    int id PK
    int member_id FK
  }
```

## 制作スケジュール

ソース: [09-gantt.mmd](09-gantt.mmd) ／ 参考スライド 38 ページ

```mermaid
gantt
  dateFormat YYYY-MM-DD
  axisFormat %m/%d
  section 準備
  設計 :done, a, 2026-10-05, 3d
  section 実施
  制作 :active, b, after a, 5d
  確認 :crit, c, after b, 2d
  公開 :milestone, after c, 0d
```

## 予約体験

ソース: [10-journey.mmd](10-journey.mmd) ／ 参考スライド 40 ページ

```mermaid
journey
  title 予約体験
  section 検討
    情報を探す: 3: 利用者
    内容を比較: 4: 利用者
  section 予約
    入力する: 2: 利用者
    確定を通知: 5: 利用者, 担当者
```

## ブランチとマージ

ソース: [11-gitgraph.mmd](11-gitgraph.mmd) ／ 参考スライド 41 ページ

```mermaid
gitGraph
  commit id: "start"
  branch feature
  checkout feature
  commit id: "change"
  checkout main
  merge feature tag: "v1.0"
  commit type: HIGHLIGHT
```

## 問い合わせの内訳

ソース: [12-pie.mmd](12-pie.mmd) ／ 参考スライド 43 ページ

```mermaid
pie showData
  title 問い合わせの内訳（例）
  "操作" : 24
  "契約" : 12
  "その他" : 4
```

## 勉強会の準備

ソース: [13-mindmap.mmd](13-mindmap.mmd) ／ 参考スライド 44 ページ

```mermaid
mindmap
  root((勉強会))
    準備
      目的
      資料
    当日
      説明
      演習
    振り返り
```
