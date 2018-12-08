---
draft: false
thumbnail: "posts/hugo-create-blog/gopher-hero.svg"
tags: [Hugo]
categories: []
date: "2018-12-08"
title: "Markdownでブログを書こう with Hugo"
description: ""
outputs:
- html
- amp
---

## Hugoとは
Hugoとは、静的なhtmlを生成する事ができる静的ページジェネレータです。

<!--more-->
生成された静的なhtmlはサーバーが不要なため、高速で表示できるサイトが出来上がります。
Hugoはgo言語で作られてはいますが、goが読めなくても大丈夫です。

## Hugoのinstall方法
MacユーザーでかつLinuxコマンドを扱えることを前提としています。
その他のOS利用者は[こちら](https://gohugo.io/getting-started/installing/)で確認できます。
### Homebrewで始める場合
Home brewをインストールしている場合一発でインストールできます。

```
$ brew install hugo
$ hugo new site blog
$ cd blog
```

### Mac と Docker Compose で始める場合
ブログのディレクトを作成します。
```bash
$ mkdir blog
$ cd blog
$ hugo server
```
docker-compose.ymlを作成します。
```docker-compose.yml
version: '3'
services:
  app:
    image: cibuilds/hugo:0.52
    ports:
      - "1313:1313"
    working_dir: /blog
    command: hugo server --bind 0.0.0.0
    volumes:
      - .:/blog:cached
```
```bash
$ docker-compose run app hugo new site . --force
$ docker-compose up
```
移行は、hugoコマンドを扱う際は`docker-compose run app`を省略して記述します。
`$ hugo new posts/my-first-post.md`のコマンドの場合、
`$ docker-compose run app hugo new posts/my-first-post.md`と入力してください。

## テーマを追加する

```bash
$ git init;
$ git submodule add https://github.com/budparr/gohugo-theme-ananke.git themes/ananke
$ echo 'theme = "ananke"' >> config.toml
```

```bash
$ hugo new posts/my-first-post.md
```

[http://localhost:1313/.](http://localhost:1313/)にアクセスするとページが表示されています。

## htmlを生成
```bash
$ hugo
```
でpublicディレクトリに静的なhtmlを生成されます。

