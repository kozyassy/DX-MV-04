# DX-MV-04 エージェント体制

## 役割分担（2026-09-24〜、2026-09-28更新）

**2026-09-28、ユーザー判断によりマスター（Hermes）への実行委託を終了した。** ①統括＋立案はClaude Codeが③レビューと兼任する。経緯・判断は`memory/knowledge/handoff_state.md`参照。

| 役割 | 担当 | コンテキスト |
|---|---|---|
| ①統括＋立案（ユーザーと会話） | **Claude Code**（③レビューと兼任） | `agents/01_master_Hermes.md`（統括の役割定義として引き続き参照） |
| ②実装と実行（ロボット操作はユーザー） | **Codex CLI** | `agents/02_executor_CodexCLI.md` |
| ③レビュー | **Claude Code** | `agents/03_reviewer_ClaudeCode.md` |

**全員、最初に`agents/00_common_context.md`と`agents/README.md`を読む。** Claude Codeは兼任のため、`agents/01_master_Hermes.md`と`agents/03_reviewer_ClaudeCode.md`の両方に従う。

## 連絡の場

- `handoff/`：引継ぎ文書（`DXMV04-H-###`）、台帳（`INDEX.md`）、進捗ボード（`board.md`）
- 各エージェントは`handoff/board.md`で自分の手番を確認する

## 書いてよい場所

| エージェント | 書いてよい場所 |
|---|---|
| Claude Code（①統括＋立案／③レビュー兼任） | `docs/`、`handoff/`、`agents/`、`memory/knowledge/`、`experiments/`（検算結果） |
| Codex CLI（実行） | `experiments/`、`handoff/`（報告のみ） |

## 運用ルール

1. 作業開始時に`git pull`し、`handoff/board.md`で自分の手番を確認する。
2. **タスクはGitHub Issue（`kozyassy/DX-MV-04`）で管理する。** 引継ぎ文書とコミットメッセージにIssue番号を併記し、対応関係を追えるようにする。
3. エージェント間の依頼・報告・判定は引継ぎ文書（`DXMV04-H-###`）で行い、作成と同時に`handoff/INDEX.md`へ1行追記する。
4. 技術ナレッジと一次証跡の正本はDX-MV-04。
5. 自分の担当の場所以外を書き換えない。
6. コミットメッセージは日本語のconventional commits（`docs:`／`feat:`／`fix:` 等）。
