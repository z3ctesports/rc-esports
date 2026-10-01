# Realize Summit Official Website

Realize Summitの公式Webサイトです。ダークでミニマルなブランド表現、軽量Canvas背景、ニュース／メンバーのデータ管理、フォームのフロントエンド検証を含む静的サイトです。

## 使用技術

- HTML5 / CSS3 / Vanilla JavaScript
- 外部依存はGoogle Fontsのみ
- GitHub Pages対応

## ディレクトリ構成

公開ファイルは `dist/` にまとまっています。HTML、`assets/css`、`assets/js`、`data` を含みます。

## ローカルで確認する方法

`dist` をドキュメントルートにしてローカルサーバーを起動します。

```bash
cd realize-summit/dist
python -m http.server 8080
```

ブラウザで `http://localhost:8080` を開いてください。JSONを読み込むため、HTMLファイルの直接オープンではなくローカルサーバーを使用します。

## GitHub Pages公開方法

1. このフォルダをGitHubリポジトリへpushします。
2. GitHub Actionsで `dist/` をPagesアーティファクトとしてデプロイするか、`dist/` の内容を公開ブランチのルートへ配置します。
3. 公開URLが決まったら、各HTMLの `canonical` を実URLへ変更します。

## 更新方法

- ニュース: `dist/data/news.json` に同じ形式で項目を追加します。詳細は `news-detail.html?id=ID` で表示されます。
- メンバー: `dist/data/members.json` に追加します。画像を使用する場合は `assets/images/members/` に保存し、表示ロジックを接続してください。
- SNS: `dist/data/settings.json` の各URLを変更します。
- 画像: `dist/assets/images/` の各フォルダへ配置し、該当HTMLまたはデータファイルから参照します。

## お問い合わせフォームの接続

現在は `dist/assets/js/contact.js` で入力検証まで実装しています。Formspreeを使う場合はフォームの `action` と `method="POST"` を設定し、検証成功時に `f.submit()` を呼びます。Google Apps Scriptや独自APIの場合は、同じ検証成功箇所から `fetch()` で送信してください。接続時は送信中・成功・失敗の表示とスパム対策も追加してください。
