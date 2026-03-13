# chatgpt-codex-playbook

## このリポジトリの目的
このリポジトリは、ChatGPT と Codex を使ったプロジェクト運用の「作業ルール」「協業手順」「再利用テンプレート」をまとめるためのドキュメント集です。実装コードではなく、進め方を揃えることを目的にします。

## 想定利用者
- プロジェクト方針を決める人（Human）
- 要件整理・文章化を支援する人（ChatGPT 利用者）
- 指示に基づきファイル変更を行う人（Codex 利用者）

## 役割分担（Human / ChatGPT / Codex）
- **Human**: 目的・優先順位・最終判断を行う
- **ChatGPT**: 論点整理、仕様の草案化、レビュー観点の明確化を支援する
- **Codex**: 明示された指示に従ってリポジトリを編集し、変更結果を報告する

## リポジトリマップ
- `AGENTS.md`: Codex 向けの編集ルール
- `docs/00_project_playbook.md`: 全体運用ルール
- `docs/01_project_brief_template.md`: プロジェクト要件テンプレート
- `docs/02_threading_and_branching.md`: スレッド運用と Git ブランチ運用
- `docs/03_codex_prompt_template.md`: Codex 実行プロンプトテンプレート
- `docs/04_review_checklist.md`: レビューとマージ判断のチェックリスト
- `.github/pull_request_template.md`: ドキュメント向け PR テンプレート

## 推奨の読み順
1. `docs/00_project_playbook.md`
2. `docs/02_threading_and_branching.md`
3. `AGENTS.md`
4. `docs/03_codex_prompt_template.md`
5. `docs/04_review_checklist.md`
6. 必要に応じて `docs/01_project_brief_template.md`

## 新しいプロジェクト開始時の使い方
1. `docs/01_project_brief_template.md` を使って要件を整理する
2. `docs/00_project_playbook.md` に沿って進行方針を確定する
3. `docs/03_codex_prompt_template.md` を使って Codex 実行指示を作成する
4. 小さな単位で変更し、`docs/04_review_checklist.md` でレビューする
5. `.github/pull_request_template.md` で PR を作成し、main スレッドへ結果を戻す
