# 03 Codex Prompt Template

## 再利用テンプレート
以下を branch thread で Codex に渡してください。

```md
Goal
- この作業で達成したいことを 1〜3 行で記載

Context
- 背景
- 前提
- 参照すべきドキュメント

Constraints
- やってはいけないこと
- 変更サイズ・対象範囲の制約
- 言語や表記ルール

Done when
- 完了条件を検証可能な形で列挙

Target files
1. path/to/file-a.md
2. path/to/file-b.md

Minimum content
- 各ファイルに最低限入れる見出し・要素

Output format
- 変更結果の報告形式（例: 変更一覧、要約、確認コマンド）

Completion report
- 最後に必ず含める報告項目
```

## 短い記入例
```md
Goal
README と docs/00 の用語を統一する。

Context
- 用語の揺れがレビュー指摘になっている。
- docs/00_project_playbook.md を正とする。

Constraints
- Markdown のみ変更。
- 新規ファイル作成禁止。
- 差分は 2 ファイル以内。

Done when
- README と docs/00 の用語が一致している。
- 変更理由を 3 行以内で説明できる。

Target files
1. README.md
2. docs/00_project_playbook.md

Minimum content
- README の役割分担節
- docs/00 の Operating Model 節

Output format
- 変更ファイル一覧
- 各ファイル要約
- 実施コマンド

Completion report
- 未解決事項
- 次の小さな推奨ステップ
```
