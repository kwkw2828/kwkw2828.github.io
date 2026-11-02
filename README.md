# kwkw2828.github.io

自作ソフトウェアを日本語で紹介・配布する、GitHub Pages 用のサイトです。

公開先: <https://kwkw2828.github.io/>

## GitHub Pages の設定

リポジトリの **Settings → Pages → Build and deployment** で、次のように設定します。

- Source: **Deploy from a branch**
- Branch: 公開するブランチ（例: `main`）
- Folder: **/ (root)**

設定したブランチへ変更をプッシュすると、GitHub Pages が Jekyll でビルドして公開します。
この構成では独自の GitHub Actions ワークフローや `.nojekyll` は不要です。

## サイトの編集

- `_config.yml`: サイト名、説明、公開 URL など
- `index.md`: トップページ
- `software/index.html`: ソフトウェア一覧（自動生成）
- `_layouts/`: 共通レイアウトとソフト紹介用レイアウト
- `assets/css/style.css`: 表示スタイル
- `404.html`: 存在しないページにアクセスしたときの案内

ルートで公開するため、`baseurl` は空文字のままにします。
`README.md`、`AGENTS.md`、`_trash/` などは公開対象から除外しています。

## ソフトウェアを追加する

`_software/` フォルダーを作成し、ソフトごとに Markdown ファイルを追加します。
例えば `_software/my-app.md` を次の内容で作成すると、`/software/my-app/` に紹介ページが生成され、一覧にも自動で掲載されます。

```markdown
---
title: ソフトの名前
description: ソフトの概要を一文で記載します。
download_url: https://github.com/kwkw2828/my-app/releases/latest
source_url: https://github.com/kwkw2828/my-app
---

## 概要

ソフトの機能を紹介します。

## 動作環境

対応 OS や必要な実行環境を記載します。

## 使い方

インストール方法や基本的な操作を記載します。

## 利用条件・ライセンス

配布するソフトの利用条件やライセンスを記載します。
```

上記の URL は記載例です。実際の配布先に変更してください。
`download_url` と `source_url` は任意で、不要なら行ごと削除できます。
サイト内の配布ファイルを指定する場合は `/downloads/my-app.zip` のようなサイトルートからのパスを使います。
ファイル名は半角英数字とハイフンを推奨します。一覧はタイトル順に表示されます。
トップページの準備中の案内も、初回公開時に更新してください。

## ローカルで確認する

Ruby と Bundler を用意した環境で、リポジトリのルートから実行します。

```sh
bundle install
bundle exec jekyll serve
```

ブラウザーで <http://localhost:4000/> を開きます。
`_config.yml` を変更した場合はサーバーを再起動してください。
Windows では RubyInstaller の Ruby+Devkit など、gem のビルドが可能な環境を用意してください。

公開用のビルドのみを確認する場合:

```sh
bundle exec jekyll build
```
