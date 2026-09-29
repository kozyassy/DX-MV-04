# DX-MV-04 進捗ボード

## 体制変更（2026-09-28）

**マスター（Hermes）への実行委託を終了し、①統括＋立案はClaude Codeが③レビューと兼任する。** 経緯は`memory/knowledge/handoff_state.md`参照。

**訂正**：`DXMV04-H-002`は「HermesがD段階をCodex CLIへ委任済み」という前提で事後記録されたが、**Hermesの不具合により実際には実行系へ送信されていなかった**（board.md上の記録のみ）。あわせて実行役をCodex CLIからChatGPT Works/Codex（デスクトップアプリケーション）に変更し、`DXMV04-H-003`として依頼を作成し直した。

**Orchestration方式（2026-09-28合意）**：Claude Codeは依頼文書・`board.md`・`INDEX.md`の更新までを行う。ChatGPT Works/Codexアプリへの実際の入力・送信はユーザーが手動で行う（Claude Codeはデスクトップアプリを直接操作しない）。

## 現在の手番

| エージェント | 状態 | 次のアクション |
|---|---|---|
| Claude Code（①統括＋立案／③レビュー兼任） | **A段階＝校正完了を確定**（2026-09-29）。`DXMV04-H-005`の命名是正も完了 | 次フェーズの立案・依頼を行う |
| ChatGPT Works/Codex（実行、デスクトップアプリ）またはユーザー | `DXMV04-H-005`完了。Project名`MV-TST00-DX-MV04`を画面・ログで確認済み | 次の依頼待ち |

## 完了済み（C段階）

- [x] C-1 プロジェクト作成
- [x] C-2 校正作業（IPC校正実行）
- [x] C-3 読取り専用確認（校正CSV作成・pose番号修正）
  - pose番号ずれ修正：pose_002～pose_023のデータをユーザー手動取得値で差し替え
  - pose_022, pose_023 は欠損（404エラー）→ ユーザーデータで補完
  - pose_020～025 はlarge rotation（9.30°～44.74°）として注記
  - 旧CSVとの差分報告済み（22点不一致、2点欠損補完、1点微差）

## 完了済み（メンテナンス）

- [x] リポジトリ内の不整合を洗い出し・修正（2026-09-28、Claude Code担当、commit `231df9c`、push済み）
  - ブランチ名誤記（`master`→`main`）を`CLAUDE.md`・`AGENTS.md`で修正
  - ハンドオフ文書を`DXMV04-H-###`命名規則に統一（`DXMV04-C3-handoff.md` → `DXMV04-H-001.md`）、`handoff/INDEX.md`を実態に同期
  - `memory/knowledge/handoff_state.md`（正本ナレッジ）が初期コミット以来停滞していたため、計画レビュー完了・役割分担確定・C段階完了の3件を追記し最新状態に同期

## 校正完了フェーズ（今次）

- [x] 校正点再調整 → 合格範囲に収まる結果（ユーザー観測、2026-09-28）
- [x] 校正結果画像確認（Mech-Vision外部パラメータ校正レポート、3項目合格） **訂正（2026-09-29、Claude Codeレビュー）：ユーザーの目視確認のみで証跡未保存。A段階判断のため`DXMV04-H-004`で証跡取得を依頼中**
- [x] ~~マスターが前回校正点メッセージ一覧表を読み、Codex CLIにD段階委任（このターン）~~ **訂正：実際には未送信だった（`DXMV04-H-002`参照）**
- [x] Claude CodeがD段階の依頼を`DXMV04-H-003`として作成、実行役をChatGPT Works/Codexに変更
- [x] **D**: ChatGPT Works/CodexがIPC校正画面から最新の校正点データを収集し、一覧表（`calibration_points_message_log.csv`）を最新データに更新（27点→29点）
- [x] **C**: 更新結果をClaude Codeがレビュー（最新校正画面との整合性、数値整合、pose対応）→ **合格**（`experiments/P0-1_camera_calibration/C_stage_review_20260929.md`）
- [x] **A**: 校正完了確定（2026-09-29、`experiments/P0-1_camera_calibration/A_stage_decision_20260929.md`）。点群誤差・外部パラメータ校正レポート3項目は良好。独立検算・新旧差比較は今後の課題として保留（ユーザー決定）
- [x] **命名是正**: Solution名`DX-MV-04`を維持し、Project名を`MV-TST00-DX-MV04`へ変更（2026-09-29、`DXMV04-H-005`、ユーザー実施・Codex確認）

## 未着手のフェーズ

- [ ] フェーズ0-①（カメラ再校正）※ 計画レビュー済み・ユーザー承認済み、次はC段階完了後に移行
- [ ] フェーズ0-②（JOB通信確認）
- [ ] フェーズ0-③（MOVコメントアウトJOB実行）
- [ ] フェーズ1（認識位置精度調査）
- [ ] フェーズ2（姿勢ばらつき課題）
- [ ] フェーズ3（実機動作・精度測定）
