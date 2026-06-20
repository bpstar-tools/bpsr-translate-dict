# スタレゾ翻訳 辞書ホスティング（GitHub Pages）

スタレゾ日英中翻訳ツールが参照する辞書を配信するための静的サイトです。

## 公開URL（Pages有効化後）

```
https://bpstar-tools.github.io/<このリポジトリ名>/translation-table.json
https://bpstar-tools.github.io/<このリポジトリ名>/desc-index.json
```

このURLをユーザースクリプト/拡張の「対応表URL」に設定します（desc-index.json は同じ場所から自動取得）。

## ファイル

- `translation-table.json` … 用語対応表（en2ja / zh2ja）
- `desc-index.json` … 説明文の正規化インデックス（公式訳）
- `en2ja.csv` / `zh2ja.csv` … 用語の単方向CSV
- `.nojekyll` … GitHubのJekyll処理を無効化（全ファイルをそのまま配信）

## 更新方法

辞書を作り直したら、このリポジトリのファイルを差し替えて push（またはWebからアップロード）するだけ。
GitHub PagesはCDNキャッシュの都合で反映に最大10分ほどかかります。

> GitHub Pages は標準で `Access-Control-Allow-Origin: *` を返すため、別ドメイン（maxroll.gg等）からの取得もそのまま動作します。
