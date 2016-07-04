Sensitive Data Exposure
====

## 概要
製品の仕様/不具合で情報漏えいする可能性がある場合に脆弱性として扱う情報について、
本資料にてまとめます。

## 脆弱性の認定可否
認証情報および、それに類する情報が漏えいしている場合、脆弱性として認定します。
これ以外の情報について、認定しません。

### 認証情報に類する情報とは
以下の情報を指します。

* アカウントの存在を推定できる情報
* 特定の人にしか送信しない URL 情報 (例： パスワードのリセット用にユーザーに送る URL など)
* CSRF トークン (ただしログインユーザーの CSRF トークンを、自身の権限で取得できるケースは除く)

## 脆弱性に対する対策が必要な個所（Scope）
次の情報がログ、メールヘッダー、HTTPヘッダーなどに出力される製品の仕様もしくは不具合で、
外部に情報が洩れる可能性がある場合には脆弱性として扱います。

* 認証情報、もしくはそれに類する情報

また、処理系のエラーメッセージ（スタックトレース etc… ）が画面に表示されるケースも同様に脆弱性として扱います。

## 脆弱性として認定しない理由
下記の情報については、直接攻撃に繋がらないと判断し、脆弱性と扱わないこととしています。
ただし、具体的な攻撃方法が明確である場合には、その限りではありません。

* データセンター内部のローカル IP アドレス
* サーバーのバナー情報や、利用しているソフトウエアに関する情報
* 不正な HTTP メソッドや、未実装の HTTP メソッド

### メールにて機密情報を送信する
メールの暗号化については、以下2点があると考えております。

1. メール本文の暗号化
2. メールの送信経路の暗号化

#### メール本文の暗号化
他のクラウドサービス等も比較致しましたが、システムメールの本文自体を暗号化することは普及が進んでおらず、
2016 年現在は弊社では対応する予定はございません。
このため脆弱性としては、認定いたしません。

#### メールの送信経路の暗号化
こちらは既知の問題として対応時期を検討しております。
但し、すべてのお客様に対して暗号化通信を強制する仕様は実装できないため、
送信経路が暗号化されていない点については、脆弱性として認定いたしません。

## 参考資料

* [OWASP Top 10 for 2013 A6 – Sensitive Data Exposure](http://owasptop10.googlecode.com/files/OWASP%20Top%2010%20-%202013.pdf)
* [エラーメッセージからの情報暴露](https://www.ipa.go.jp/security/awareness/vendor/programmingv1/b09_03.html)