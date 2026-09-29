# DX-MV-04 エージェント体制

## 役割分担（2026-09-24〜、2026-09-28更新）

**2026-09-28、ユーザー判断によりマスター（Hermes）への実行委託を終了した。** ①統括＋立案はClaude Codeが③レビューと兼任する。同日、②実装と実行もCodex CLIからChatGPT Works/Codex（デスクトップアプリケーション）へ変更した。経緯・判断は`memory/knowledge/handoff_state.md`参照。

| 役割 | 担当 | コンテキスト |
|---|---|---|
| ①統括＋立案（ユーザーと会話） | **Claude Code**（③レビューと兼任） | `agents/01_master_Hermes.md`（統括の役割定義として引き続き参照） |
| ②実装と実行（ロボット操作はユーザー） | **ChatGPT Works/Codex**（デスクトップアプリケーション） | `agents/02_executor_CodexCLI.md`（実行の役割定義として引き続き参照） |
| ③レビュー | **Claude Code** | `agents/03_reviewer_ClaudeCode.md` |

**全員、最初に`agents/00_common_context.md`と`agents/README.md`を読む。** Claude Codeは兼任のため、`agents/01_master_Hermes.md`と`agents/03_reviewer_ClaudeCode.md`の両方に従う。

**Orchestration方式（2026-09-28合意）**：Claude Codeは依頼文書（`handoff/DXMV04-H-###`）・`handoff/board.md`・`handoff/INDEX.md`の更新までを行う。ChatGPT Works/Codexへの実際の入力・送信はユーザーが手動で行い、Claude Codeはデスクトップアプリを直接操作しない。

## 連絡の場

- `handoff/`：引継ぎ文書（`DXMV04-H-###`）、台帳（`INDEX.md`）、進捗ボード（`board.md`）
- 各エージェントは`handoff/board.md`で自分の手番を確認する

## 書いてよい場所

| エージェント | 書いてよい場所 |
|---|---|
| Claude Code（①統括＋立案／③レビュー兼任） | `docs/`、`handoff/`、`agents/`、`memory/knowledge/`、`experiments/`（検算結果） |
| ChatGPT Works/Codex（実行） | `experiments/`、`handoff/`（報告のみ） |

## 運用ルール

1. 作業開始時に`git pull`し、`handoff/board.md`で自分の手番を確認する。
2. **タスクはGitHub Issue（`kozyassy/DX-MV-04`）で管理する。** 引継ぎ文書とコミットメッセージにIssue番号を併記し、対応関係を追えるようにする。
3. エージェント間の依頼・報告・判定は引継ぎ文書（`DXMV04-H-###`）で行い、作成と同時に`handoff/INDEX.md`へ1行追記する。
4. 技術ナレッジと一次証跡の正本はDX-MV-04。
5. 自分の担当の場所以外を書き換えない。
6. コミットメッセージは日本語のconventional commits（`docs:`／`feat:`／`fix:` 等）。
7. **【2026-09-29〜】`git commit`・`git push`は必ずClaude Codeが、ユーザーの明示指示（「コミットして」等）を受けて行う。** ChatGPT Works/Codexを含む他のエージェントは、ファイルの作成・編集（自分の担当場所内）までとし、コミット・pushは行わない。
   - 理由：全エージェントがPC-C上の同じgit設定（`y_kozaki`）を共有しているため、コミットの実行者（git author）だけでは実際に誰が作業したか区別できない
   - **コミットメッセージには、実際に作業を行ったエージェント（Actor）を明記する。** 例：`Actor: ChatGPT Works/Codex（D段階実施）` / `Actor: Claude Code（統括／レビュー）`。ユーザー自身が手動で作業した場合は`Actor: ユーザー（手動実施）`のように記載する
   - 過去に本ルール制定前の例外あり：コミット`e262146`（2026-09-29 17:15、H-005完了記録）はClaude Codeを経由せず直接コミットされたもの。内容は事後確認済みで問題ないが、本ルール制定のきっかけとなった
