# Memory

## Active projects

| Name | Working premise |
|---|---|
| **DX-MV-04** | On-Hand。ロボットに取り付けたカメラを動かし、①様々な撮影アングル・距離での3D Matchingワーク位置認識の誤差量調査（ロボットの既知位置を基準に相対位置を厳密に記録）、②ロボット目標位置（ロボット座標系へ変換した把持目標位置）における誤差量の評価・改善、の2フェーズを扱う。 |
| **DX-MV-03** | On-Handフェーズの計画・立案。DX-MV-04が実行を継承。 |
| **DX-MV-02** | Off-Hand。カメラ座標系だけを基準に、3D Matchingによるワーク位置認識の正誤分離・再現性・精度を向上させる（本プロジェクトの対象外。前提知識の参照元）。 |

→ 詳細: `memory/knowledge/handoff_state.md`

## Agent roles（2026-09-24〜、2026-09-28更新）

**DX-MV-04の作業は当初3つのAIエージェントで分担していた：①統括＋立案＝マスター（Hermes）、②実装と実行＝Codex CLI（ロボット操作はユーザー）、③レビュー＝Claude Code。**

**2026-09-28、ユーザー判断によりマスター（Hermes）への実行委託を終了し、①統括＋立案はClaude Codeが③レビューと兼任する。** ②実装と実行＝Codex CLI（ロボット操作はユーザー）は変更なし。経緯・判断は`memory/knowledge/handoff_state.md`参照。体制・連絡方法・書いてよい場所は`agents/README.md`、共通の前提は`agents/00_common_context.md`。

- **このフォルダで起動したClaude Codeは①統括＋立案／③レビューの兼任役である。** 作業を始める前に`agents/00_common_context.md`、`agents/01_master_Hermes.md`（統括の内容）、`agents/03_reviewer_ClaudeCode.md`（レビューの内容）に従う。
- エージェント間の依頼・報告は`handoff/`の引継ぎ文書（`DXMV04-H-###`）で行い、手番は`handoff/board.md`で確認する。
- 技術ナレッジと一次証跡の正本はDX-MV-04（非公開リポジトリ）。

## Knowledge store

**DX-MV-04のナレッジ（判断・確定事項・運用ルール）の正本は `memory/knowledge/` である**（DX-MV-02と同じ方式）。

- **最初に読む: `memory/knowledge/handoff_state.md`**（最新状態・未決事項）
- 索引と運用ルール: `memory/knowledge/README.md`
- **一次証跡（Run結果・画面・ロボット姿勢ログ等）は `experiments/` に置く。** `memory/knowledge/` は解釈と判断を置く場所。
- **知見を得たらその場で該当ファイルを更新する。撤回・訂正は消さずに「撤回（→H-###）」と明記する**（過去の誤結論を次のセッションが拾い直すのを防ぐため）。

## Project boundary

- **DX-MV-02側で確立したカメラ座標系での認識精度に関する知見**（ワークのZ軸曖昧性、want/must評価基準、Mech-Vision操作手順、`.vis`の読み方等）**は前提として参照する。重複調査・再確認はしない。** 参照時はDX-MV-02側のファイルパス（`C:\Users\y_kozaki\Git_Repo\DX-MV-02\memory\knowledge\`配下）を明記し、内容を複製しない。
- **カメラはロボットに取り付けられた状態で動かす。** ロボットの既知位置（ジョイント角・TCP位置等）を基準に、カメラ移動の相対位置・姿勢を厳密に記録することが本プロジェクトの中核。
- **①アングル・距離の誤差量調査ではカメラ座標系での認識評価、②ロボット目標位置の誤差評価ではロボット座標変換後の精度評価を扱う。** どちらのフェーズ・どちらの座標系のデータかを、記録の際に常に明示する。
- **Mech-Visionの自動化はPS1方式（Win32 API直接クリック）を主軸とする。** トークン消費を抑え、高速に繰り返し試験を回すことを優先する。例外処理にのみRDP越しのComputer-useを使用する。
- Git変更の整理と検証が完了し、push可能な段階になったらユーザーへ明示する（リモート：`github.com/kozyassy/DX-MV-04`、ブランチ`main`）。

## Investigation preference

- Mech-Vision関連の設定方法・機能・表示条件を調べる場合は、DX-MV-02と同じ方針（公式マニュアル確認を先行、実画面探索は曖昧な場合のみ、`パラメータ調整レベル`切替は事前確認後のみ）を踏襲する。
- ロボット（DX100／MotoPlus等）関連の設定・動作確認も同様に、まず公式マニュアル・既存資料（DX-MV-01の関連ドキュメント等）を確認してから実機検証に進む。実機検証を先行させない。
