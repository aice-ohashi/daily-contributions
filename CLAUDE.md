# CLAUDE.md

## Project Overview

GitHub Actions を使って毎日自動でコミットを行い、コントリビューショングラフ（草）を維持するリポジトリ。

## Structure

- `.github/workflows/daily-commit.yml` - 日次自動コミットワークフロー（UTC 00:00 / JST 09:00）
- `contributions.txt` - タイムスタンプ追記ファイル（ワークフローが毎日1行追加）

## Workflow

- **スケジュール**: `0 0,3,6 * * *`（UTC 00:00/03:00/06:00 に冗長実行、日付ベースで重複コミット防止）
- **手動実行**: `gh workflow run daily-commit.yml`
- **コミットメッセージ形式**: `chore: daily contribution YYYY-MM-DD`
- **Git ユーザー**: `github-actions[bot]`

## Conventions

- コミットメッセージは英語、ドキュメントは日本語
- ワークフローは変更がない場合コミットをスキップする
