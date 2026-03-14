# chatgpt-codex-playbook

ChatGPT や Codex を使うと、要件整理、文書作成、レビュー、実装指示など、さまざまな生成物を作れます。  
ただし実際には、「何を人が決めるのか」「何を ChatGPT に整理させるのか」「何を Codex に実行させるのか」が曖昧なままだと、運用はすぐにぶれます。  
このリポジトリは、その迷いを減らすために、役割分担、進め方、テンプレート、レビュー観点を整理しておくための プレイブック（運用ガイド）です。

## このリポジトリについて
このリポジトリは、ChatGPT と Codex を使ったプロジェクト運用の「作業ルール」「協業手順」「再利用テンプレート」をまとめるためのドキュメント集です。実装コードではなく、進め方を揃えることを目的にします。

## 主な利用場面
- プロジェクト開始時に進め方や方針を整理したいとき
- 枝スレッドで論点や作業単位を切り分けたいとき
- Codex に渡す実行プロンプトを組み立てたいとき
- 生成物をレビューし、プルリクにまとめたいとき

## 役割分担（人 / ChatGPT / Codex）
- **人**: 目的・優先順位・最終判断を行う
- **ChatGPT**: 論点整理、仕様の草案化、レビュー観点の明確化を支援する
- **Codex**: 明示された指示に従ってリポジトリを編集し、変更結果を報告する

## リポジトリ構成
- `AGENTS.md`: Codex 向けの編集ルール
- `docs/00_project_playbook.md`: 全体運用ルール
- `docs/01_threading_and_branching.md`: スレッド運用と Gitブランチ運用
- `docs/02_project_brief_template.md`: プロジェクト要件テンプレート
- `docs/03_chatgpt_prompt_template.md`: ChatGPT で概要整理するためのプロンプトテンプレート
- `docs/04_codex_prompt_template.md`: Codex 実行プロンプトテンプレート
- `docs/05_review_checklist.md`: レビューとマージ判断のチェックリスト
- `.github/pull_request_template.md`: ドキュメント向けプルリクテンプレート

## 読む順番
1. `docs/00_project_playbook.md`
2. `docs/01_threading_and_branching.md`
3. `docs/02_project_brief_template.md`
4. `docs/03_chatgpt_prompt_template.md`
5. `docs/04_codex_prompt_template.md`
6. `docs/05_review_checklist.md`
7. `AGENTS.md`
8. 必要に応じて `.github/pull_request_template.md`

## 新しいプロジェクトを始めるときの使い方
1. `docs/02_project_brief_template.md` を使って要件を整理する
2. `docs/03_chatgpt_prompt_template.md` を使って概要整理を進める
3. `docs/00_project_playbook.md` に沿って進行方針を確定する
4. `docs/04_codex_prompt_template.md` を使って Codex 実行指示を作成する
5. 小さな単位で変更し、`docs/05_review_checklist.md` でレビューする
6. `.github/pull_request_template.md` でプルリクを作成し、幹スレッドへ結果を戻す
