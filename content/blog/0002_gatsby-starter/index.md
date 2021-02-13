---
title: Gatsby ブログ作成
date: "2021-02-13T13:43:23+09:00"
description: "Gatsby と GitHub Pages でここ作った時のメモです。"
---

Gatsby と GitHub Pages でここ作った時のメモです。

# 前提

- Node.js インストール
- Git インストール
- GitHub アカウント取得

# 手順

## Gatsby CLI インストール

```shell
npm install -g gatsby-cli
```
https://www.gatsbyjs.com/docs/tutorial/part-zero/#using-the-gatsby-cli

## Starter からサイト作成

[Gatsby Starters](https://www.gatsbyjs.com/starters)

初期状態から作るのは大変そうなのでとりあえずスターターを使います。
[gatsby-starter-blog](https://www.gatsbyjs.com/starters/gatsbyjs/gatsby-starter-blog/) を利用させてもらいました。

```shell
gatsby new gatsby-starter-blog https://github.com/gatsbyjs/gatsby-starter-blog
```

設定ファイルの値を変更したり、サンプルの記事を削除してコミット。

## GiHub Pages 作成

https://docs.github.com/ja/github/working-with-github-pages/creating-a-github-pages-site#creating-your-site

https://www.gatsbyjs.com/docs/how-to/previews-deploys-hosting/how-gatsby-works-with-github-pages/

### リポジトリ作成

GitHub に新しいリポジトリを作って、スターターから作ったサイトをプッシュ。

### gh-pages インストール

```shell
npm install gh-pages --save-dev
```

### gh-pages 設定

gatsby-config.js に追記

```js:gatsby-config.js
module.exports = {
  pathPrefix: "/リポジトリ名",
  ...
```

package.json に追記
```js:package.json
{
  "scripts": {
    ...
    "deploy": "gatsby build --prefix-paths && gh-pages -d public"
  }
}
```

### デプロイ

```shell
npm run deploy
```

これで `ユーザー名.github.io/リポジトリ名/` にサイトが表示されるはずです。
