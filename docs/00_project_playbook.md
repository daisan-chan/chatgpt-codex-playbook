# 00 Project Playbook

## Purpose（目的）
ChatGPT と Codex を使ったドキュメント中心の開発運用を、再現可能な手順として揃えることを目的とします。

## Scope（対象範囲）
- 作業の進め方
- スレッド運用とブランチ運用の対応
- 指示テンプレートとレビュー手順

## Non-goals（対象外）
- プロダクト実装の設計詳細
- 技術スタック固有のベストプラクティス集
- 自動化基盤（CI/CD）構築

## Operating Model（運用モデル）
- **main thread**: 方針決定、優先順位、最終合意を扱う
- **branch thread**: 個別タスクの具体化と実行指示を扱う
- **Git branch / PR**: 変更の実体を管理し、レビュー可能にする

## Responsibility Split（責任分担）
- **Human**: 目的設定、意思決定、承認
- **ChatGPT**: 論点整理、文書ドラフト、レビュー支援
- **Codex**: 指示に基づく編集、差分提示、作業報告

## Standard Lifecycle（標準ライフサイクル）
1. **start**: main thread で目的・制約・完了条件を定義
2. **branch discussion**: branch thread で対象変更を小さく分割
3. **Codex execution**: Codex が指示どおりに編集・確認
4. **review**: チェックリストで整合性と過不足を確認
5. **PR**: GitHub で差分をレビューし、必要修正を反映
6. **report back**: main thread に結果・判断事項・次ステップを戻す

## Maintenance Principles（保守原則）
- 小さく安全な変更を優先する
- 既存ルールとの整合を優先し、重複記述を避ける
- テンプレートは実運用で使える最小構成を維持する
- 方針変更時は README と関連ドキュメントを同時更新する
