---
title: Web出版の未来とCSS組版
author:
  - 村上真雄
---

# Web出版の未来とCSS組版

JAGAT（日本印刷技術協会）のPAGE2020のオープンイベント[「XMLパブリッシング交流会—ウェブ出版と日本語組版の未来](https://kokucheese.com/event/index/589362/)」(2020年2月7日)で、[『ウェブ出版と日本語組版の未来とCSS組版Vivliostyle』](http://bit.ly/page2020xpub)という話をしたのですが、そのテーマでもう少し書こうと思います。

## 〈Web出版〉とは何でしょう？

いま多くの人にとって、紙に印刷されたテキストよりもWeb上のテキストを読んでいることのほうが多いと思います。Webで何かを公開（publish＝出版）することは〈Web出版〉と言えるので、印刷出版よりもWeb出版が優勢になっていくのは必然でしょう。

そうは言ってもこの技術同人誌が紙の本として作られているように、紙の本のニーズもまだまだあります。そうすると、紙以外の出版はWebの技術でできるのだから、紙の出版も同じくWebの技術でできるようになると便利だよね、ということでCSS組版にもつながります。

Webの技術ですべての出版ができるようになったら、すべての出版がWeb出版に収斂していく、そして読み手の好みやニーズに応じて様々なメディア形式にオンデマンドで出力できるようになる、という未来が想像できます。

## Web出版 vs 印刷出版

### 紙とWebの違い：「紙は難解な内容を長文で論じるのに向くメディア」

紙の本のニーズが簡単になくならない理由に、そのメディアの特性がWebとは違うということもあります。まとまった量のコンテンツを売買するのに都合がよくて、そのような長めのコンテンツをじっくり読ませやすいメディアの特性があります。

[片手間で教える文章講座2　「ユニバーサル日本語」の構成（紙とWebの違い）｜安田峰俊｜note](https://note.com/meirojin/n/n5c422e085c3d) というネット記事で、「紙媒体とWeb媒体は『視認性』が違う」、「紙はWebよりも難解な内容を、より深く長く論じることに向いたメディア」と論じられています。紙媒体向けとWeb媒体向けで文章の書き方も変わり、Web媒体では「段落あたりの文字数は、おおむね紙媒体の半分〜3分の2以下」がよいことなど、いろいろ勉強になります。そしてその「紙とWebの違い」とされることに、組版スタイルの違いも関係があるようです。

段落の区切りが紙媒体では行頭の1文字下げだけなのに対して、Web媒体では、

> 改行ごとに1行の空白が挟まれる場合も多い。これは、Web記事は紙媒体の記事よりも段落ごとに読者の思考が中断しやすいことを意味している。画像の挿入が記事を分断する形でおこなわれることが多い点も、この傾向に拍車をかける。
> 
> なので、Web記事は難解な内容を長文で論じるのにはあまり向いていない。

なるほど、たしかに。

### 紙とWebのUI・組版スタイルの違い

段落区切りばかりでなく、紙とWebはいろいろ違います：

- ページめくり / スクロール
- 固定ページサイズに文字数・行数で版面設計 / 可変ページ(画面)サイズ
- 行末を揃える / 行末を揃えない
- 段落区切りは段落先頭の字下げ / 段落間のアキ

それから、日本語の本や雑誌は理工系を除くと縦書きが主流なのに対して、Webは圧倒的に横書きです。[CSS Writing Modes Level 3](https://www.w3.org/TR/css-writing-modes-3/) がW3C勧告になって、Webでの縦書きは標準的に使えるものになりましたが、それが使われる場面は限定的でしょう。

紙とWebでそれぞれに向く出版コンテンツが違うのは、UI（ページ／スクロール）と組版スタイルの影響があるといえそうです。紙のページ（固定のサイズでページめくり）とWebページ（可変サイズでスクロール）の違いがまずあって、それぞれに適した組版スタイルとして今の状態になっているのでしょう。

いまのWebページの主流のUIと組版スタイルは、現状のブラウザで使えるWeb標準技術の制約も関係しています。Webブラウザ上で本のページのように読めるようにするページネーションのしくみが標準化されていないことが問題です。Web標準が進化することで変わってくる可能性があるでしょう。

## EPUB・電子書籍

EPUBは、Web標準技術（HTMLやCSS）を使った電子書籍フォーマットです。EPUB 3.0 (2011年) で、縦書き（CSS Writing Modes）やルビ（HTMLのruby要素）など日本語組版に必要な機能が標準になって、それからこの世界標準フォーマットでの日本語電子書籍が普及することになりました。まさにWeb標準が進化したことで実現したことです。

電子書籍閲覧アプリには、たいていWebブラウザエンジンが使われています。HTML+CSSのコンテンツを表示するものなので、当然ですね。CSSでの縦書きの標準化が進んだのは、日本語電子書籍での縦書きのニーズからです。

しかし、Webブラウザではページネーションのしくみが標準化されていないために、電子書籍閲覧アプリでのページネーションは、何らかの代わりの方法で実装されていて、ページのレイアウトの機能は貧弱です。

今のEPUBは、Web標準技術が使われているとはいっても、現状はWebとはかなり別の世界です。ページネーションが必要なこと、EPUBコンテンツは普通のHTMLではなくXML構文（XHTML形式）にする必要があったり、XMLファイルでメタデータやパッケージ内容を記述する必要があるなど。


## Web出版物の標準化 (W3C Web Publications) はどうなってる？

出版の将来の標準として今のEPUBよりもよりWebと親和性の高いものにしようという〈Web出版物〉標準化の動きがあります。[Web Publications (W3C Working Group Note 13 August 2019)](https://www.w3.org/TR/wpub/) がそれです。Web上の出版物（1個以上のHTML文書とその他のリソースで構成され、目次があって、順番に読むことができるなど）の標準の仕様を作り、またそれをパッケージ化（1つのファイルにまとめる）した形式を定義して、それが将来のEPUB（EPUB 4.0）にもなるだろうというものでしたが、しかしこの文書のステータスの記述を見ると、ちょっと残念な状態であることが書かれています:

> Due to the lack of practical business cases for Web Publications, and the consequent lack of commitment to implement the technology, the Publishing Working Group has chosen to publish this document as a Note and focus on other areas of interest, including developing the manifest format as a separate specification.

（Web出版の実際的なビジネスケースが不足し、その結果、技術を実装するというコミットメントが不足しているため、出版ワーキンググループはこのドキュメントをノートとして発行し、別の仕様としてマニフェスト形式を開発するなど、関心のある他の分野に焦点を当てることを選択しました。）

その別の仕様として開発が進んでいる出版物マニフェスト仕様が [Publication Manifest (W3C 勧告候補)](https://www.w3.org/TR/pub-manifest/) です。出版物の内容とメタ情報を JSON-LD 形式で記述するものになっています。こちらはW3C 勧告候補というステータスになっているので、使うことができそうです。マニフェストの役割は、EPUBでいえば [EPUB Packages](https://www.w3.org/publishing/epub3/epub-packages.html) 仕様で定義されているEPUBパッケージ文書（拡張子 .opf のXMLファイル）に相当します。

W3CでのWeb出版物の標準化が目指していたものの全体像は、[Web Publications Use Cases and Requirements](https://www.w3.org/TR/pwp-ucr/) にあります。そこにある多くのユースケースと要件は、Webで実現されるべき将来の出版の標準として楽しみだったのですが、その標準化が「技術を実装するというコミットメントが不足」で止まっていて、残念。

### Web出版物でのページネーションの要求

Web出版物の要件としては、ページネーションについても書かれています（ただし必須ではありません）: [4.4 Movement](https://www.w3.org/TR/pwp-ucr/#movement)

> Req. 26: It should be possible to see the Web Publication in a “paginated” view. When a user agent renders a Web Publication in a paginated layout, it must lay out each document in the default reading order sequentially, with the last page of a resource being followed by the first page of the subsequent one.

（要件26: Webページを「ページ分割された」ビューで表示できるようにする必要があります。ユーザーエージェントがページ分割されたレイアウトでWebパブリケーションをレンダリングする場合、リソースの最後のページに後続の最初のページが続くように、各ドキュメントをデフォルトの読み取り順序で順番にレイアウトする必要があります。）

それからページネーションとスクロール方式を切り替えられるべきともあります。いつでもページネーションがよいわけでないので当然でしょう。

### "WebBook" というよりシンプルな代替仕様案

Web Publications 標準化については当初から、ブラウザへの実装が期待できない、仕様が複雑すぎ、せっかく普及した EPUB3 との互換性がなくなる、などの批判がW3C内からもあり、それに代わるものとして [WebBook Level 1 (Unofficial Proposal Draft, 2 February 2018)](http://glazman.org/e0/webbook.html) という仕様案が提案されていました。これも Unofficial Proposal Draft の状態から進んでいないですが、現在のブラウザで実現できて、JSONのマニフェストも不要でHTMLだけで記述できるシンプルな仕様、EPUB3と互換性を持たせることも可能ということで、Web出版物のようなものを実現するのに参考になります。

### Vivliostyle でのWeb出版物のサポート

Vivliostyle プロジェクトの目標のひとつに将来のWeb出版物の標準をサポートしたいということがありました。その標準化が今後どうなるかはさておき、これまで提案されている関連仕様ドラフトでも有用なものは取り入れていきたいです。

約1年前の [Vivliostyle version 2019.1.101 リリース](https://vivliostyle.org/ja/blog/2019/02/27/vivliostyle-2019.1.101-released/) から、部分的にWeb出版物関連の機能を実装しています。このリリースノートにある次の項目です：

- 目次（Table of Contents, TOC）ナビゲーションが有効になりました
- Web 出版物および同様の複数 HTML 文書をサポート

Web Publications のマニフェストを利用できるほか、マニフェストが指定されていない場合には、目次要素（`<nav role="doc-toc">` など）からリンクされた(X)HTML 文書がロードされるというところは、"WebBook" 仕様案を取り入れています。


## CSS組版（CSS Print）とWebのページネーションの標準化

CSS組版で本が作れるようになったのはそんなに新しいことではありません。YesLogic社の [Prince](https://www.princexml.com/) というCSS組版ソフトウェアが最初にリリースされたのは2003年で、Håkon Wium Lie と Bert Bos によるCSSの入門書 [“Cascading Style Sheet – designing for the Web” (3rd edition)](https://www.amazon.com/dp/B003XNTT80/) が、それで組版されて出版されたのが2005年です。

![Håkon Wium Lie & Bert Bos “Cascading Style Sheet – designing for the Web” (3rd edition) Addison-Wesley, 2005](https://www.w3.org/Style/LieBos3e/LieBos3e-small2.png)

Vivliostyle はWebブラウザベースのCSS組版エンジンですが、それより前にすでに、Webブラウザを使わない独自開発の組版エンジンでPDFを出力することができるCSS組版ソフトウェアが、Princeをはじめとして、いくつか存在していたのです。私が Vivliostyle の前に開発に携わっていたアンテナハウス社の [Antenna House Formatter](http://www.antenna.co.jp/AHF/) もそのひとつです。

### CSS組版の仕様

Vivliostyle を含め、CSS組版ソフトウェアはWebブラウザには実装されていないページメディア向けのCSS仕様を実装しています。CSS Paged Media、CSS Generated Content for Paged Media (GCPM))、CSS Page Floats が主なものです。これらはまだ標準が完成していないドラフト仕様です。

- **CSS Paged Media**
  - [**CSS Paged Media Level 3**](https://drafts.csswg.org/css-page-3/)
  - [Proposals for the future of CSS Paged Media (Level 4), Editor's Draft](https://drafts.csswg.org/css-page-4/)
- **CSS Generated Content for Paged Media (GCPM)**
  - [**CSS Generated Content for Paged Media Level 3**](https://drafts.csswg.org/css-gcpm-3/)
  - [CSS Generated Content for Paged Media Level 4, Editor's Draft](https://drafts.csswg.org/css-gcpm-4/)
  - [WHATWG CSS Books, Living Idea](https://books.idea.whatwg.org/)
- **CSS Page Floats**
  - [**CSS Page Floats**](https://drafts.csswg.org/css-page-floats/)
  - [WHATWG CSS Figures, Living Idea](https://figures.idea.whatwg.org/)

この中で [**CSS Paged Media Level 3**](https://drafts.csswg.org/css-page-3/) がもっとも基本的ですが、それが "Level 3" であるのは、[CSS Level 2](https://www.w3.org/TR/CSS2/) にもより基本的な [Paged media](https://www.w3.org/TR/CSS2/page.html#the-page) の仕様があったからです。

### CSS Paged Media 関連仕様の分裂：2013年ごろの話

CSS Paged Media Level 3 仕様は、1999年に最初のW3Cドラフト仕様が出て、それから仕様策定が進んで2004年にはW3C勧告候補 [CSS3 Paged Media Module, W3C Candidate Recommendation 25 February 2004](https://www.w3.org/TR/2004/CR-css3-page-20040225/) に1度なっていたのに、それからWorking Draftに戻って、2006年により高度な仕様は Generated Content for Paged Media (GCPM) 仕様になって、それからいろいろ仕様が変わりながら、[Prince](https://www.princexml.com/) や [Antenna House Formatter](http://www.antenna.co.jp/AHF/) でドラフト仕様の不完全な実装と独自拡張が進むという状況になります。

2013年まで、W3C CSSWG での CSS Paged Media と関連仕様（GCPM と Page Floats）策定の中心人物は、CSS仕様のもともとの提唱者である Håkon Wium Lie 氏（当時 Opera CTO）でした。しかし彼は、W3C CSSWG での仕様の標準化を断念して、今の最新HTML仕様を策定している [WHATWG](https://whatwg.org/) で "Living Standard" として仕様策定を進めようとします。それが、[WHATWG CSS Books](https://books.idea.whatwg.org/) と [WHATWG CSS Figures](https://figures.idea.whatwg.org/) です。当初 "Living Standard" だったのが、今は "Living Idea" に変わって、その最終更新は2017年で止まっています。

W3C CSSWG のほうでは、その分裂のあと、"Living Idea" のアイデアも一部取り入れて [CSS Generated Content for Paged Media Level 3](https://drafts.csswg.org/css-gcpm-3/) や [CSS Page Floats](https://drafts.csswg.org/css-page-floats/) がいくらか進んだ（CSS Page Floats は Vivliostyle の Johannes Wilm がエディターを担当して、その仕様が Vivliostyle に実装された）のですが、その後また停滞してます。

### 今は忘れられている "Level 4" の提案：Proposals for the future of CSS Paged Media

これも2013年ごろにあったCSSWG内での動きとして、CSS Paged Media Level 3 仕様はいろいろダメなので、もっと良い "Level 4" を作ろうという提案がありました。[Proposals for the future of CSS Paged Media (Level 4), Editor's Draft](https://drafts.csswg.org/css-page-4/) です。

> This module describes an extension of the page model that partitions a flow into pages. It adds to Paged Media Level 3 features introduced by other modules like CSS Regions or CSS Exclusions and Shapes: content flows, exclusions, more powerful headers and footers, etc. It does not deprecate nor obsolete Paged Media Level 3 but is designed to live gracefully with it.

（このモジュールでは、フローをページに分割するページモデルの拡張について説明します。Paged Media Level 3 に CSS Regions、CSS Exclusions and Shapes などのモジュールによって導入される、複数のコンテンツフロー、除外、より強力なヘッダーとフッターなど。Paged Media Level 3を非推奨にしたり廃止したりするものではなくて、うまく共存できるように設計されています。）

そして、この提案と関連して、[CSS Generated Content for Paged Media Level 4, Editor's Draft](https://drafts.csswg.org/css-gcpm-4/) の提案がされます。

私はこの "Level 4" 仕様の標準化が進むのも期待してました。また、そのような将来の標準となるものを実現したいということも Vivliostyle プロジェクトの構想につながっています。

### Paged Media "Level 4" と EPUB Adaptive Layout と Vivliostyle

2015年に Vivliostyle の開発を開始するとき、ベースとしてPeter Sorotokin氏による [EPUB Adaptive Layout implementation](https://github.com/sorotokin/adaptive-layout) を利用することにしました。この [EPUB Adaptive Layout](http://idpf.org/epub/pgt/) 仕様は CSS Paged Media "Level 4" で構想されているものと機能的には近いものです。

Vivliostyle はその実装をベースにして、Paged Media Level 3 と関連仕様の実装を加え、そしてさらに今後標準化されていくだろう "Level 4" に対応していく（機能が近い EPUB Adaptive Layout 実装がベースなのでできるはず）、という計画なのです。

### 最近の動き：W3C Workshop on CSS Print と CSS Print Community Group

2020年2月13日に、プラハにて [W3C Workshop on CSS Print](https://wiki.csswg.org/planning/print-workshop-2020) が開催されました。Vivliostyle からの参加は見送りましたが、世界のCSS Print（「CSS組版」とほぼ同じ）の関係者たちが集まって盛況だったようです。参加者たちのポジションペーパーや発表資料が公開されています。たいへん参考になります：

- https://wiki.csswg.org/planning/print-workshop-2020

また、このW3C Workshopの議論から、[CSS Print Community Group](https://www.w3.org/community/cssprint/) が作られることになりました。W3C CSSWG だけではブラウザベンダーからの積極的なサポートがない CSS Print 関連仕様はなかなか進まない。そこで CSS Print 関連仕様を議論するための W3C Community Group（Working Groupよりもゆるい集まりで、W3Cメンバー以外でも参加できる）を作られて、CSSWG で CSS Print に関連する仕様のエディターであるDave Cramer氏とRachel Andrew氏が議長になって、メンバー募集中です。興味ある方いかがでしょうか？

- https://www.w3.org/community/cssprint/

このように、この数年停滞していたCSS組版関連の標準化が、また動き出そうとしています。まずは CSS Paged Media Level 3 と関連仕様（GCPM と Page Floats）が完成に向かうこと、そうして、今は忘れられている "Level 4" の議論や、Webでのページネーションの標準化ということもまたはじまることをと期待します。

### Vivliostyle の開発を進めて、未来のWeb出版の標準を作ろう

Vivliostyle はもともと新しい標準を作ることにコミットしながら開発を進めていくというプロジェクトです。仕様の議論や実装を進められる開発者たちを増やしたいので、どうぞよろしくお願いします！
