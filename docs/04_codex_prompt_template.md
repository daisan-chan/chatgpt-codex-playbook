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
- 既存構成のどの役割を壊さずに差分拡張するか

Constraints
- やってはいけないこと
- 変更サイズ・対象範囲の制約
- 言語や表記ルール
- 既存構成を置き換えず、差分拡張を優先すること

Done when
- 完了条件を検証可能な形で列挙

Target files
1. path/to/file-a.md
2. path/to/file-b.md

Minimum content
- 各ファイルに最低限入れる見出し・要素

Working approach
- 変更前に読むべき文書順
- bulky な内容をどのファイルへ分離するか
- 相互参照の方針

Output format
- 返答全体の報告形式（例: 変更一覧、要約、確認コマンド）

Completion report
- 最後に必ず含める報告項目
```

## 初回実行で意識すること
- ブランチを切った直後の初回作業では、新規作成対象と変更対象を明示し、どこまで作るかを先に固定する
- スコープを広げすぎないように制約を明確にし、新規ファイル追加可否を必ず書く
- `Done when` は確認可能な条件で書き、初回作業の完了線を曖昧にしない
- 既存文書の役割を壊さず、どの差分をどこへ入れるかを明記する

## 追いコミットで意識すること
- 既存ブランチ更新であることを明示し、前回レビュー指摘の反映に絞る
- 新規ファイル追加禁止を明示し、既存構成や文意を壊さない方針を入れる
- 差分最小を優先し、プルリクを育てるための更新であることを前提にする
- どの指摘をどのファイルへ反映するかを対応づけて書く

## playbook 更新依頼で補うとよい項目
ドキュメント運用リポジトリを更新するときは、通常の `Goal / Constraints / Done when` に加えて、次も書くとぶれにくくなります。

- 既存構成のどの役割を維持するか
- 差分拡張の対象ファイル
- 主対象外として触らないファイル
- 新規ファイルを許可するか、その上限
- README と docs 群の参照関係で崩してはいけないこと

## README / docs 更新タスクの依頼例
```md
Goal
- 既存 playbook 構成を保ちながら、README と docs の運用説明を差分拡張する。

Context
- 現状は幹 / 枝の説明が中心で、Project 指示文との接続が弱い。
- `README.md`、`docs/00_project_playbook.md`、`docs/03_chatgpt_prompt_template.md` を主対象にする。
- 既存の役割分担と番号順は維持する。

Constraints
- Markdown のみ変更する。
- 既存文書の役割を置き換えず、追記中心で対応する。
- `docs/02_project_brief_template.md` は主対象外とする。

Done when
- README に読み方と Project 情報源登録の説明がある。
- docs に追加した説明が相互参照されている。
- 差分の意図を 3 行程度で説明できる。

Target files
1. README.md
2. docs/00_project_playbook.md
3. docs/03_chatgpt_prompt_template.md

Minimum content
- README: 使い方、情報源登録、Project 指示文ガイド
- docs/00: 運用原則の追記
- docs/03: Project 指示文テンプレート
```

## 運用検証結果を反映する更新タスクの依頼例
```md
Goal
- 実運用で観察したズレを playbook に反映し、次回からの運用補助を強化する。

Context
- `docs/07_operational_validation.md` に、上位幹で詳細作業が詰まりやすい記録がたまっている。
- 既存構成を維持しつつ、原則は `docs/00`、実務ルールは `docs/01`、テンプレートは `docs/06` に反映したい。

Constraints
- Markdown のみ変更する。
- 記録そのものを大量転記せず、再利用できる運用差分に要約する。
- 新しい運用思想を大きく増やしすぎない。

Done when
- 反映先ファイルごとの役割が壊れていない。
- 観察結果から導いた変更点が説明できる。
- `docs/07` との参照関係が残っている。

Target files
1. docs/00_project_playbook.md
2. docs/01_threading_and_branching.md
3. docs/06_thread_operation_templates.md
4. docs/07_operational_validation.md

Minimum content
- docs/00: 上位原則の更新
- docs/01: 実務ルールの更新
- docs/06: 定型文の更新
- docs/07: 反映済みメモの更新
```

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
