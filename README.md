# chatgpt-codex-playbook

ChatGPT や Codex を使うと、要件整理、文書作成、レビュー、実装指示など、さまざまな生成物を作れます。  
ただし実際には、「何を人が決めるのか」「何を ChatGPT に整理させるのか」「何を Codex に実行させるのか」が曖昧なままだと、運用はすぐにぶれます。  
このリポジトリは、その迷いを減らすために、役割分担、進め方、テンプレート、レビュー観点を整理しておくためのプレイブック（運用ガイド）です。

## このリポジトリについて
このリポジトリは、ChatGPT と Codex を使ったプロジェクト運用の「作業ルール」「協業手順」「再利用テンプレート」をまとめるためのドキュメント集です。実装コードではなく、進め方を揃えることを目的にします。

今回のプレイブックは、既存の幹 / 枝運用を壊さずに、**上位幹 / 中間幹 / 枝**の 3 層へ自然に拡張する前提で構成しています。情報量の多さではなく、**どの種類の判断を扱う場か**でスレッドを分けることを基本にします。

## 主な利用場面
- プロジェクト開始時に進め方や方針を整理したいとき
- ChatGPT Project に情報源を登録し、参照順つきで運用したいとき
- 上位幹 / 中間幹 / 枝のどこで判断すべきか迷うとき
- 枝スレッドで論点や作業単位を切り分けたいとき
- Codex に渡す実行プロンプトを組み立てたいとき
- 実運用で出たズレや改善点を蓄積したいとき

## 役割分担（人 / ChatGPT / Codex）
- **人**: 目的・優先順位・最終判断を行う
- **ChatGPT**: 論点整理、スレッド階層の提案、文書ドラフト、レビュー観点の明確化を支援する
- **Codex**: 明示された指示に従ってリポジトリを編集し、変更結果を報告する

## リポジトリ構成
- `AGENTS.md`: Codex 向けの編集ルール
- `docs/00_project_playbook.md`: 全体運用ルールと 3 層モデルの原則
- `docs/01_threading_and_branching.md`: 上位幹 / 中間幹 / 枝と Git ブランチ運用の実務ルール
- `docs/02_project_brief_template.md`: プロジェクト要件テンプレート
- `docs/03_chatgpt_prompt_template.md`: ChatGPT Project 指示文とスレッド開始用テンプレート
- `docs/04_codex_prompt_template.md`: Codex 実行プロンプトテンプレート
- `docs/05_review_checklist.md`: レビューとマージ判断のチェックリスト
- `docs/06_thread_operation_templates.md`: スレッド運用・移行・命名提案のテンプレート集
- `docs/07_operational_validation.md`: 実運用での観察・記録・改善の受け皿
- `.github/pull_request_template.md`: ドキュメント向けプルリクテンプレート

## 読む順番
1. `docs/00_project_playbook.md`
2. `docs/01_threading_and_branching.md`
3. `docs/02_project_brief_template.md`
4. `docs/03_chatgpt_prompt_template.md`
5. `docs/04_codex_prompt_template.md`
6. `docs/05_review_checklist.md`
7. `docs/06_thread_operation_templates.md`
8. `docs/07_operational_validation.md`
9. `AGENTS.md`
10. 必要に応じて `.github/pull_request_template.md`

この `読む順番` は、人が全体像を理解するための入口順です。ChatGPT Project の `参照順` は別用途で、応答時に ChatGPT がどの文書を優先参照するかを指定するものです。

## この Playbook の使い方
### 1. まず全体原則をそろえる
- `docs/00_project_playbook.md` で、上位幹 / 中間幹 / 枝の責務と非責務を確認する
- `docs/01_threading_and_branching.md` で、どのタイミングで中間幹や枝へ切り出すかを確認する

### 2. ChatGPT Project の情報源として登録する
このプレイブックは、**人が読むための説明**としてだけでなく、**ChatGPT Project の情報源**として登録して参照させる前提でも使えます。Project に登録することで、毎回すべてを貼り直さなくても、どの文書をどう読ませるかを Project 指示文で固定できます。

情報源として登録する際は、少なくとも次を含める運用を推奨します。
- `README.md`
- `docs/00_project_playbook.md`
- `docs/01_threading_and_branching.md`
- `docs/03_chatgpt_prompt_template.md`
- `docs/06_thread_operation_templates.md`
- `docs/07_operational_validation.md`

必要に応じて、要件整理や Codex 依頼、レビュー用に次も追加します。
- `docs/02_project_brief_template.md`
- `docs/04_codex_prompt_template.md`
- `docs/05_review_checklist.md`

### 3. Project 指示文で参照順を明示する
ChatGPT Project では、情報源を登録するだけでなく、**どの文書をどの順に参照するか**を Project 指示文で書くことが重要です。参照順が曖昧だと、ChatGPT がテンプレートだけ見て原則を読み落としたり、逆に実務ルールを見ずに抽象論へ寄ったりしやすくなります。

最小構成では、次の順を明示します。
1. `README.md` で全体像と役割を確認する
2. `docs/00_project_playbook.md` で運用原則と 3 層モデルを確認する
3. `docs/01_threading_and_branching.md` で実務ルールを確認する
4. 目的に応じて `docs/03` 〜 `docs/07` を参照する

Project 指示文の具体テンプレートは `docs/03_chatgpt_prompt_template.md` にまとめています。

### 4. スレッド開始・移行時はテンプレートを使う
- 新規スレッド開始時は `docs/03_chatgpt_prompt_template.md` の開始導線を使う
- 自己認識、戻し、誤投入補正、命名提案は `docs/06_thread_operation_templates.md` を使う
- 実運用で出たズレや例外は `docs/07_operational_validation.md` に記録する

## Project 指示文を書く人向けの最小ガイド
- **参照順を書く**: どのファイルを先に読むべきかを明記する
- **期待する介入を書く**: 枝化提案、中間幹化提案、戻し先の明示、命名変更提案をしてよいかを書く
- **開始時確認項目を書く**: 階層、親スレッド、テーマ、目的、扱う範囲、扱わない範囲、戻し先、終着点を確認させる
- **扱わないことも書く**: 勝手に実装へ飛ばない、未確定事項を断定しない、階層を越えて詳細作業を続けない
- **テンプレート誘導を書く**: 必要に応じて `docs/06_thread_operation_templates.md` を使うよう指定する

## 新しいプロジェクトを始めるときの使い方
1. `docs/02_project_brief_template.md` を使って要件を整理する
2. `docs/03_chatgpt_prompt_template.md` の Project 指示文テンプレートで ChatGPT Project を整える
3. `docs/00_project_playbook.md` に沿って、上位幹 / 中間幹 / 枝のどこで扱う判断かを決める
4. `docs/01_threading_and_branching.md` を見て、必要なら中間幹や枝を切る
5. `docs/06_thread_operation_templates.md` のテンプレートを使ってスレッド開始・移行・戻しを行う
6. `docs/04_codex_prompt_template.md` を使って Codex 実行指示を作成する
7. 小さな単位で変更し、`docs/05_review_checklist.md` でレビューする
8. 実運用で出たズレや改善候補を `docs/07_operational_validation.md` に残し、次回更新につなげる
