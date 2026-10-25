# Baystars Theme (VSCode系エディタ + Obsidian)

横浜DeNAベイスターズのチームカラー + マスコット配色（DB.スターマン / DB.キララ / チャピー BART&CHAPY）をモチーフにしたテーマ。このリポジトリで VSCode 系エディタ版と Obsidian 版の両方を管理する（同じパレット）。

## バリアント

| ラベル | 種別 | 内容 |
|---|---|---|
| Baystars Light | ライト | 白×スターマンクリーム基調、横浜ブルーアクセント |
| Baystars Dark | ダーク | 濃紺 #0B1D30（ハマスタの夜空）基調 |
| Baystars Dark Neon | ダーク | ほぼ黒の紺 #050D18 に蛍光ブルー/イエロー/ピンク |

## インストール（VSCode系）

拡張機能フォルダに `norihito.baystars-theme-1.0.0` としてコピー済み（VSCode / Cursor / Windsurf / Antigravity / Devin）。

手動で入れ直す場合：

```bash
cd ~/Projects/Dev/vscode-obsidian-theme
for e in vscode cursor windsurf antigravity devin; do
  rm -rf ~/.$e/extensions/norihito.baystars-theme-1.0.0
  rsync -a --exclude=.git ./ ~/.$e/extensions/norihito.baystars-theme-1.0.0/
done
```

エディタを再起動（または `Developer: Reload Window`）して、
`Cmd+K Cmd+T`（カラーテーマの選択）で `Baystars *` を選ぶ。

## インストール（Obsidian）

`obsidian/Baystars/` を各 vault の `.obsidian/themes/Baystars/` にコピーする。
本テーマは `@import "../Minimal/theme.css"` で **Minimal テーマに依存**するため、先に Minimal を vault にインストールしておくこと（設定 → 外観 → テーマ → 管理）。

```bash
cd ~/Projects/Dev/vscode-obsidian-theme
VAULTS=(
  "$HOME/Library/Mobile Documents/iCloud~md~obsidian/Documents"
  "$HOME/Library/Mobile Documents/iCloud~md~obsidian/Documents/30_DELTA_MailMagazine"
  "$HOME/Library/Mobile Documents/iCloud~md~obsidian/Documents/50_NPB_stats"
)
for v in "${VAULTS[@]}"; do
  rm -rf "$v/.obsidian/themes/Baystars"
  cp -R obsidian/Baystars "$v/.obsidian/themes/Baystars"
done
```

設定 → 外観 → テーマで `Baystars` を選択。ライト/ダーク両モード対応。

> **注意**: このリポジトリの `obsidian/Baystars/` が正本。各 vault 側を直接編集した場合は逆方向にコピーして正本に反映させること。

## 配色

| 色 | コード | 用途 |
|---|---|---|
| 横浜ブルー | #0055A5 | アクセント・キーワード・ステータスバー |
| 横浜ライトブルー | #0092E1 / #4FC3F7 | 関数・リンク・選択範囲 |
| スターイエロー | #FAE44E | 括弧マッチ・検索ハイライト |
| チャピーイエロー | #F9C700 / #FFD000 | バッジ・文字列・find |
| キララレッド | #E60033 / #FF4060 / #FF2E88 | エラー・diff削除・エスケープ |
| スターマンクリーム | #FDF6E3 / #EDE6D3 | 背景（Light）・本文（Dark） |
| ハマスタ濃紺 | #0B1D30 / #050D18 | 背景（Dark / Neon） |

## ファイル構成

```
package.json              … VSCode拡張機能マニフェスト（themes を3件 contribute）
themes/                   … VSCode系テーマ
  baystars-light.json     … Light
  baystars-dark.json      … Dark
  baystars-neon.json      … Dark Neon
obsidian/
  Baystars/               … Obsidianテーマ（Minimal 依存）
    manifest.json
    theme.css
```
