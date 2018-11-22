```
  層: アプリケーション
  タイトル: 3-of4　マルチシグネチャー・エスクロー
  Author: Yuki Aoki <ayukiyhs at gmail.com>
  Created: 2018-11-17
```

## 概要

これは2-of-3 マルチシグネチャー・エスクローを拡張し、利用者とプラットフォーム運営者が共に、より非中央集権的で応用がきく方法で資金を制御できるようにします。

## 動機

2-of-3　マルチシグネチャー・エスクローは、暗号通貨で何かを購入するとき、安全かつ有用な解決法です。
しかし、実運用上、プラットフォーム運営者は利用料を徴収したり、追加でルールを適用したいと考えるかもしれません。

この方式は2-of-3 マルチシグネチャー・エスクローを拡張します。利用者だけでなく運営者も資金を管理できるような方法を提供します。
これにより、例えば、運営者は利用者の資金の所有権を奪うことなく手数料を支払わせることができ、加えて、いくつかのルールを適用することもできます。

## 定義

* 売り手 - エスクロー・プラットフォーム上でオンラインショップを開いています。
* 買い手 - 売り手から何か商品を買おうとしています。
* 運営者 - エスクロー・プラットフォームを運営している個人もしくは組織。
* プラットフォーム・サーバー - 運営者によって運営され、利用者の注文を管理するオンライン状態のコンピュータ

それぞれ秘密鍵を所有しています。

## 仕様

1. 買い手がエスクロー・プラットフォーム上で「買う」ボタンをクリックします。
2. 売り手と買い手の公開鍵を収集します。
3. 3-of-4 マルチシグP2SH(SegWitを利用するならばP2WSH)アドレスを生成します。以下の公開鍵が登録されています。
  - 買い手
  - 売り手
  - プラットフォーム・サーバー
  - 運営者
4. 買い手は価格とブロックチェーン手数料とプラットフォーム利用料を含めた金額をマルチシグアドレスに預け入れる。
5. 売り手は預け入れを確認したら、商品を買い手に送付できる。
6. 買い手はプラットフォーム・サーバーに商品が到着したことを通知する。
7. プラットフォーム・サーバーはトランザクションを生成し署名する。
  * プラットフォーム・サーバーがもつ秘密鍵で署名されている。
  * 出力(vout)は売り手のアドレスと、プラットフォーム利用料プールである
8. 売り手と買い手はトランザクションに署名する。
9. トランザクションを発信する。

もし売り手が商品を送らない、もしくは、売り手と買い手が、例えば、ブロックチェーンの扱い方がわからないなどの理由で、トランザクションに署名できない場合、運営者は介入し、運営者の秘密鍵で取引を巻き戻すことができる。

たとえ、よく訓練された利用者がトランザクションを編集し、手数料の支払いを拒否しようとしても無駄である。なぜなら既にプラットフォームサーバーが署名しているからである。



## Implementation

In development

## See also

[Add the draft of Deep Link Payment Protocol spec](https://github.com/bitcoincashorg/bitcoincash.org/pull/145)

## Acknowledgement

## Documentation History

* 2018-11-22 Created repository and moved from gists
* 2018-11-20 Made public and moved to my gists.
* 2018-11-17 Initial

## Copyright

Copyright (c) 2018 Yuki Aoki
All rights reserved