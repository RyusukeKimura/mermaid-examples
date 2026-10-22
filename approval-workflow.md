# 申請・承認フロー

このファイルは PR 演習の更新対象です。main では受付追加前のフローを示します。

```mermaid
flowchart LR
  A[申請] --> B{承認?}
  B -->|はい| C[実行]
  B -->|いいえ| D[差戻し]
  D --> A
```

差し戻し先は申請です。ソースは [approval-workflow.mmd](approval-workflow.mmd)。
