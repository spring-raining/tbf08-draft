---
title: GitHub+Circle CIを用いたVivliostyle+Markdownによる組版をやってみた
author:
  - MH35
---

# GitHub+Circle CIを用いたVivliostyle+Markdownによる組版をやってみた

<div class="draft-author">
MH35
</div>

## Circle CIとは

Circle CIとは、継続的インテグレーションサービスの1つであり、コミットからデプロイまでのパイプラインを作成して自動化するサービスである。このサービスは、初期費用が無料であり、簡単に試すことができるのが利点である。今回、私はそれを使うことにした。

## Circle CIのイメージ

出来合いのものを使おうとすると壁があったため(Pandocを入れる必要があったから)、自前で作ることにした。その際には、以下のパッケージのインストールは必須である[^1]。

[^1]: https://circleci.com/docs/ja/2.0/custom-images/

- git
- ssh
- tar
- gzip
- ca-certificates

その際、いろいろと試行錯誤をしてみたが、結局こんな感じの構成になった。

1. Pandocをインストールする
2. レポジトリを入れるためにCurlをインストールする
3. Node.jsをインストールする
4. gccやmakeをインストールする
5. gulpをインストールする
6. gitをインストールする
7. gnupgとlanguage-pack各種をインストールする
8. Google Chromeをインストールする

あとはDockerのイメージをビルドした上でDocker Hub上で公開すればDocker側の準備は完了である。
今回使ったイメージのレポジトリはこちら[^2]、イメージはこちら[^3]にある。

[^2]: https://github.com/mh35/builddoc_docker
[^3]: https://hub.docker.com/r/mh35jp/builddoc

## ビルドするコンテンツ

ざっくりいうと、本文・テンプレート・SCSS・フォントとビルドスクリプトから構成される。
ビルドスクリプトのGulpfileの中身はこんな感じである。

1. SCSSをコンパイルしてCSSにする
2. 画像群をコピーする
3. PandocでMarkdownをHTMLにする
4. VivliostyleでPDFに変換する

それをうまい具合にCircleCIでつなぎこめばうまくいく…はずだった。

CircleCIへのつなぎこみは.circleci/config.ymlでこのようにして行う。

```yaml
version: 2.1
jobs:
  build:
    docker:
      -
        image: 誰の/どのイメージ:イメージのタグ
    steps:
      - checkout
      -
        run:
          command: コマンド1
          name: コマンド1説明
      -
        run:
          command: コマンド2
          name: コマンド2説明
      -
        run:
          command: コマンド3
          name: コマンド3説明
      -
        store_artifacts:
          path: 成果物のパス
```

## うまくいかない

うまくいかなくて延々と挫折していた。何が原因かわからずにずっと放置せざるを得なくなっていた。

## そして締切日に原稿投げてフィードバックもらって相談していたら

締切日に原稿を送ったら、原稿が短いと言われた。だが、全く何をすればいいのかわからず、レポジトリを見てもらったら、spring-rainingさん( https://github.com/spring-raining )にフォントのパスがおかしいとの指摘をもらった。マージをして動かしたら、無事にフォントが埋め込まれたPDFができた。単純に自分のCSS/SCSSの扱いが苦手というオチだった。

## こうして出来上がったレポジトリはこちら

このレポジトリ[^4]になる。このレポジトリをcloneして、CircleCI側からレポジトリに接続すると、CircleCIがPDFをビルドしてくれる。必要なくなったらCircleCI側からデプロイ設定を解除すればよい。

[^4]: https://github.com/mh35/builddoc_content

## 教訓

CSSの挙動は勉強したほうが良さそうである。

## 今後の課題

これをいかにして実用的な本に合わせたCSSにするかなど。Vivliostyle自体の基本的な使い方である。そのあたりの勉強を始めていきたい。
