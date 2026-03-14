# 01 運用モデル図

この図は `docs/00_project_playbook.md` の補助図です。作業の場（ChatGPT / Codex / GitHub）と、運用の主フロー（幹スレッド → 枝スレッド → Codex 作業 → Gitブランチ → プルリク → 幹スレッドへ戻る）を分けて示します。

```mermaid
flowchart TB
    H[人]

    subgraph S1[ChatGPT]
        M[幹スレッド]
        B[枝スレッド]
    end

    subgraph S2[Codex]
        X[Codex 作業]
    end

    subgraph S3[GitHub]
        G[Gitブランチ]
        P[プルリク]
    end

    M -->|方針を渡す| B
    B -->|実行指示| X
    X -->|編集・差分提示| G
    G --> P
    P -->|レビュー結果・判断事項・次ステップを幹スレッドへ戻す| M

    H -->|方針決定| M
    H -->|必要に応じた判断・確認| B
    H -->|レビュー・承認| P
```

- ChatGPT / Codex / GitHub の3つを、作業の場として分けて配置しています。
- 幹スレッドと枝スレッドは ChatGPT 上の場として扱い、主フローは上から下へ追える構成にしています。
- 人は外側に置き、方針決定・判断確認・レビュー承認の主体として関与します。
- プルリクの結果は矢印ラベルで幹スレッドへ戻し、次の判断につなげます。
