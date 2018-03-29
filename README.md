# poem-free-server

PuzzleOfEmpiresの対戦コード戦の中継を行うサーバのフリーバージョンです。

## 使い方

※ scalaで作成されているので、java8及びsbtのインストールが必要です。

cloneして、
```
sbt run
```
で、起動します。

また、Appleの仕様上SSL(https)で通信をしなければならないので、
NginxなどをSSLアクセラレータとしてフロントに設置してください。

### 設定ファイルの項目

apollon-server/conf/application.conf が設定ファイルです。
基本的に変更する可能性があるのは２点です。

```
play.crypto.secret="changeme"
```
changemeの所を適当なランダム文字列に変更してください。
環境変数で、APPLICATION_SECRETにセットするほうがより安全です。

```
permitClients = ["3.0.0", "3.0.1"]
```
受け入れるクライアントのバージョンを指定してください。
"3.0.0"はキャッシュ版、"3.0.1"はフルパッケージ版のバージョン番号です。
デバッグ時にチェックをOFFにする場合は、空リストにしてください。

## SBTコマンド

### run

サーバー起動

### runClient

テスト用httpクライアント起動
Infoクラスをインスタンス化できるので、curlなどでテストするより便利です。
