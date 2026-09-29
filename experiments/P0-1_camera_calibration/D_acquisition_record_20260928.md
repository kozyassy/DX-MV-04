# D段階 最新校正点データ取得記録

- 取得日時: 2026-09-28 17:15:41～17:17:45 JST（各PNGの更新時刻）
- 取得元: IPC `192.168.250.20` のMech-Vision 2.1.2「キャリブレーション (Eye in Hand)」画面
- 表示箇所: 「画像と位置姿勢一覧」で各poseを選択した際に、画面下部の「メッセージ」欄へ表示される校正ボード情報
- 操作方法: PC-C上の既存RDP接続を前面へ復元し、各poseを読取り専用で選択
- 取得対象: 画面に存在した29点（`pose_000`～`pose_031`。`pose_005`、`pose_008`、`pose_021`は画面上に存在しない）
- 更新先: `calibration_points_message_log.csv`
- 更新前原本: `calibration_points_message_log_pre_D_20260928.csv`
- 画面証跡: `D_latest_pose_<pose番号>_20260928.png`
- 派生確認画像: `D_messages_sheet_01_20260928.png`～`D_messages_sheet_05_20260928.png`

## 転記ルール

- 画面表示の数値をそのままCSVの対応列へ転記した。
- 回転量が大きい `pose_020`、`pose_022`～`pose_026`、`pose_028`、`pose_029`は、既存CSVと同じ表現で `notes=large rotation` とした。
- CSV更新後に、行数、pose ID、数値型、誤差上限、画面証跡の有無を機械的に検証する。

## 更新前後の構成差

- 更新前: 27点、`pose_000`～`pose_026`の連番。
- 更新後: 29点。
- 削除されたID: `pose_005`、`pose_008`、`pose_021`。
- 追加されたID: `pose_027`～`pose_031`。
- `pose_026`は同一IDだが全値が変化しており、最新画面では約60度の回転を持つ点になっている。
