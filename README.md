# ms-tastingroom.github.io

M's Tasting Room「Birth Year Vintage Selection」公開ページ（GitHub Pages）。

## 構成

- `index.html`: 公開フロントページ（表示時に `bottles.json` を `fetch` して描画）
- `bottles.json`: ボトルデータの正本（JSON）
- `admin/index.html`: データ編集用の管理画面（GitHub REST API 経由で `bottles.json` を更新コミット）

## ローカルでの確認方法

`index.html` および `admin/index.html` は `fetch` を使用して `bottles.json` を読み込むため、HTMLファイルを直接開く `file://` プロトコルでは動作しません。
ローカルで表示・動作確認を行う際は、VS Code の **Live Server** 拡張機能や Python の簡易 HTTP サーバーなどを経由して開いてください。

```bash
# Python 3 の簡易サーバーを使う場合の例
python3 -m http.server 8000
```

起動後、ブラウザで以下にアクセスして確認できます。

- 公開ページ: `http://localhost:8000/`
- 管理画面: `http://localhost:8000/admin/`

## 管理画面（/admin/）での保存とトークンについて

管理画面から変更を保存するには、GitHub の **Fine-grained Personal Access Token** が必要です（初回入力時にブラウザの `localStorage` にのみ保存されます）。

- **Resource owner**: `ms-tastingroom`
- **Repository access**: Only select repositories → `ms-tastingroom.github.io`
- **Repository permissions**: `Contents` = **Read and write**
