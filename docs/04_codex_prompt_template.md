# 04 Codex 実行プロンプトテンプレート

## 再利用テンプレート
以下を枝スレッドで Codex に渡してください。

`Output format` は返答全体の見せ方、`Completion report` は最後に必ず含める報告項目です。

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
- 返答全体の報告形式（例: 変更一覧、要約、確認コマンド）

Completion report
- 最後に必ず含める報告項目
```

## 初回実行で意識すること
- ブランチを切った直後の初回作業では、新規作成対象と変更対象を明示し、どこまで作るかを先に固定する。
- スコープを広げすぎないように制約を明確にし、新規ファイル追加可否を必ず書く。
- `Done when` は確認可能な条件で書き、初回作業の完了線を曖昧にしない。

## 追いコミットで意識すること
- 既存ブランチ更新であることを明示し、前回レビュー指摘の反映に絞る。
- 新規ファイル追加禁止を明示し、既存構成や文意を壊さない方針を入れる。
- 差分最小を優先し、プルリクを育てるための更新であることを前提にする。

## 難しい作業では先に計画する
複雑・曖昧な作業では、いきなり編集に入るより先に計画を出させるほうがぶれにくくなります。必要に応じて、計画・確認事項・実施順を先に整理してから編集へ進めてください。小さな修正では不要ですが、大きめの変更では `Goal / Context / Constraints / Done when` を補う手段として有効です。

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
- docs/00 の運用モデル節

Output format
- 変更ファイル一覧
- 各ファイル要約
- 実施コマンド

Completion report
- 未解決事項
- 次の小さな推奨ステップ
```
