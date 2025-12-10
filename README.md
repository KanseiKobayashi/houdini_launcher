# houdiniLauncher
# 🎨 Houdini Launcher - README

Houdini Launcher は、Houdini 起動前に環境変数やプロジェクトを設定し、  
ワンクリックで Houdini を起動できる PySide6 ベースの GUI ツールです。

exe 化されているため、**Python や PySide6 がインストールされていない環境でも動作**します。

---

## 📌 主な機能

- **Houdini バージョンの自動検出**  
  `C:\Program Files\Side Effects Software\Houdini XX.X.XXX` からフォルダ名を解析して取得

- **HIP ファイル履歴選択（増やせる）**

- **HIP フォルダ設定（自動でセット）**

- **PYTHONPATH の設定（任意）**

- **HIP ファイルから対応バージョンを自動選択（履歴ベース）**

- 設定の保存 / 読み込み（自動）

- Launcher 終了後も Houdini が閉じない独立プロセス起動

---

## 🚀 使い方

### ① 起動
HoudiniLauncher.exe

### ② 設定項目

- **HIP ファイル**  
  - コンボボックスで履歴から選択  
  - 「参照」ボタンで .hip / .hipnc を選択  
  - 選んだ .hip のフォルダは自動で **HIP Folder** に設定  
  - 過去に使用した HIP なら対応 Houdini バージョンも自動入力

- **Houdini Version**  
  - PC にインストール済み Houdini を自動検出  
  - フォルダ名から数字部分のみ（例：`20.5.522`）を抽出

- **HIP Folder**  
  - 参照ボタンでフォルダ選択  
  - デフォルトは  
    ```
    C:/Users/<user>/Documents/houdini_projects
    ```

- **PYTHONPATH（任意）**  
  - 追加したい Python モジュールパスをセット  
  - 「参照」ボタンでフォルダ選択可能

### ③ Houdini 起動

`Houdini を起動` を押すと、以下の環境変数をセットして Houdini を起動します：

- `HIP`
- `PYTHONPATH`
- `HFS`
- `HOUDINI_USER_PREF_DIR`

---

## 💾 保存される設定（JSON）

exe と同じフォルダに  
`houdini_launcher_history.json` として保存されます。

### JSON 形式

```json
{
    "hip_history": {
        "C:/projects/test.hip": "20.5.522",
        "D:/Work/shot01.hipnc": "19.5.493"
    }
}
```
key: HIP ファイル（絶対パス）

value: その HIP 使用時の Houdini バージョン

次回起動時に自動で復元されます。

## ⚠ 注意事項
Houdini が指定パスに存在しない場合は起動できません

Windows 専用ツールです

.hip ファイルが存在しない場合はバージョン自動選択は行われません

