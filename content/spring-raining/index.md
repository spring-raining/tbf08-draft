---
title: ViolaのこれからとVivliostyle Pub
author:
  - spring-raining
---

こんにちははじめまして、はるさめ（spring-raining）です。今回は、将来公開予定の **Vivliostyle Pub** （仮称）について紹介したいと思います。

Vivliostyle Pubは、Vivliostyleを使ったWebアプリケーションです。Vivliostyle Pubを使うことで、ブラウザ上でHTMLとCSSによる原稿の執筆から組版、PDFの出力までを実現することができます。このアイディアは以前私が公開したWebアプリの [**Viola**](https://viola.pub/) を継承したもので、今後はVivliostyle Pubの開発に注力し将来的にViolaからの移行先とする予定です。

## Violaについて

![](images/viola.png)

ViolaはHTMLとCSSを使って印刷可能な原稿を制作しPDFで出力できる、CSS組版に特化したオンラインディタです。元々私がVivliostyleを知ったときに、より多くの人がVivliostyleを使ったCSS組版を実現できるよう、個人サービスとして公開しました。また、私が現Vivliostyle Foundationのメンバーと交流するきっかけにもなったプロダクトです。2017年中盤から開発を始め、2018年1月にエディタ機能のみを限定公開し、2018年9月にアカウント機能やプロジェクト管理機能を追加して正式に公開しました。

しかし、私の生活環境が変わってしまい、Violaに注力できる時間が減ってしまったことにより、それ以降Violaの更新が止まっている状態でした。利用状況の変化に伴いViolaの運用サーバもオーバースペック気味になっていき、毎月のAWS費用が重荷になっていました。個人サービスのよくある末路ですね…

この状況をVivliostyle Foundationのメンバーと相談し、Violaの開発や運営をVivliostyle Foundationに委譲する形で、新しいWebサービスを再始動させることにしました。

## Vivliostyle Pubの変更点

Violaの後継となるVivliostyle Pubは、ただ単に名前が変わるだけではありません。Violaからの変更点について、現時点で計画している内容を紹介します。

### GitHubとの連携

ViolaではGitHubとGoogleアカウントを認証基盤として使っていましたが、プロジェクトデータはViolaの内部で保存していました。Vivliostyle Pubは、よりGitHubとの連携を強化し、Vivliostyle PubのプロジェクトがそのままGitHubのリポジトリとして保存されるようになります。そのため、Vivliostyle Pubの利用には **GitHubアカウントが必要になる** 予定です。この変更で、よりエンジニアフレンドリーになり、他サービスやCIとの連携も容易になります。

一方で、現時点ではVivliostyle PubはGitHubを使ったことのない非技術者のユーザーにとって、敷居が高くなることが予想されます。長期的には、より幅広いユーザーへのサポートが必要になるでしょう。

### Vivliostyle Flavored Markdown (VFM)

akabekoさんの記事にもある通り、現状問題となっているMarkdownの表現力の低さを補うべく、VFMという新しいMarkdown方言をVivliostyle Pubのエコシステムとして採用する予定です。「V」とはついているものの、Vivliostyle専用の文法が追加されるわけではなく、あくまで書籍制作のために必要な機能を強化するという位置づけで、HTMLへの互換を前提とした用途の広い言語となることを目標としています。もちろん、VFMの仕様や実装はオープンソースです。

### 発表の場としてのVivliostyle Pub

初回のリリースでは公開とまではいかないかもしれませんが、Vivliostyle PubではプロジェクトのWeb公開機能も搭載予定です。このプラットフォームで公開される文章は、必然的にVivliostyleにより印刷可能な形式に変換できるので、将来はVivliostyle Pubが技術書の公表の場になるかもしれません！

ただ公開できるだけではGitHub Pagesと機能的な差は無いので、Vivliostyle Viewerを活用し、紙や電子書籍とWebのプラットフォームをシームレスに繋ぐ独自の場となることを目指しています。

### One more thing...?

Vivliostyle Pubには、文章執筆・制作までの道のりの中で解決すべき課題がまだ残されています。中でも、技術同人誌制作のハードルの一つ「入稿」も、課題となるテーマです。もしオフラインの印刷会社と連携し、Web上で入稿までの手続きが完了すれば、同人誌制作のハードルは一気に下がることでしょう。

あるいはCSSによる組版自体がハードルになるかもしれません。CSSのテンプレート機能は、Violaでは機能自体は用意したものの活用できていませんでした。Vivliostyle Pubではこれを本格的に実装する予定です。

これらはまだアイディア段階ですが、Vivliostyle Foundationは多方面でVivliostyle Pubの発展を検討しています。

## まとめ

あれこれと将来を展望を語ってしまいましたが、Vivliostyle Pubの開発はまだまだこれからです。正直に言うと、これら全てを現在の（私を含めた）開発リソースだけで実現することはとても大変でしょう… Vivliostyleコミュニティはいつでもどなたでも開発への参加を歓迎します。Vivliostyle PubをCSS組版の未来にしてください！
