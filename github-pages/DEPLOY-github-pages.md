# GitHub Pages で辞書を公開する手順（新規リポジトリ）

`bpstar-tools` 組織に新しいリポジトリを作って、この `github-pages/` フォルダの中身を置くだけです。

## 1. リポジトリを作る

1. https://github.com/organizations/bpstar-tools/repositories/new を開く
2. **Repository name** を入力（例：`starezo-dict` や `bpsr-translate-dict`）
3. **Public** を選択（GitHub Pages無料の条件。辞書なので公開で問題なし）
4. 「Create repository」

## 2. ファイルをアップロード

**Webから（簡単）**
1. 作ったリポジトリの「Add file → Upload files」
2. この `github-pages/` フォルダの中身を**すべて**ドラッグ＆ドロップ
   （`translation-table.json` `desc-index.json` `en2ja.csv` `zh2ja.csv` `.nojekyll` `index.html` `README.md`）
   - ※ `.nojekyll` が一緒に上がっているか必ず確認（ドットファイルは見落としやすい）
3. 「Commit changes」

**gitコマンド派**
```bash
cd github-pages
git init && git add -A && git commit -m "dict"
git branch -M main
git remote add origin https://github.com/bpstar-tools/<リポジトリ名>.git
git push -u origin main
```

## 3. GitHub Pages を有効化

1. リポジトリの **Settings → Pages**
2. 「Build and deployment」→ Source: **Deploy from a branch**
3. Branch: **main** / フォルダ: **/(root)** → **Save**
4. 1〜2分で公開。ページ上部に公開URLが出ます

## 4. 辞書URLを確認

```
https://bpstar-tools.github.io/<リポジトリ名>/translation-table.json
```

ブラウザで開いてJSONが表示されればOK（`desc-index.json` は同じ場所から自動取得されます）。

## 5. 翻訳ツールに設定

- **ユーザースクリプト**：Tampermonkeyメニュー →「① 対応表URLを設定」に上記URL
- **Chrome拡張**：ポップアップの「対応表URL」に上記URL →「保存して再読み込み」

---

## 更新するとき

辞書を作り直したら（`python gen_dict.py`）、`github-pages/` の json/csv を差し替えて再アップロード（または push）。
反映はCDNキャッシュの都合で**最大10分ほど**。急ぐときはブラウザのスーパーリロードを。

> 補足：将来「xlsxをpushしたら自動で辞書を再生成」までやりたければ、GitHub Actions化もできます。必要なら言ってください。
