[English](https://github.com/aegif/NemakiWare/wiki/Install%28NemakiWare%29)/日本語 
***
# 必要環境
- Linux/Windows/Mac
- Java 1.6+
- CouchDB  
  (CouchDBは自分でインストールする必要があります)

# インストーラ
- インストーラは全プラットフォームで動作します。
- インストーラは[IzPack](http://izpack.org/)を利用して作成されています。

## 最新版インストーラのダウンロード
[https://github.com/aegif/NemakiWare/releases](https://github.com/aegif/NemakiWare/releases)

## インストーラの実行
- GUI  
  `java -Dfile.coding=UTF-8 -jar <installer_file>`  
- CUI  
  `java -jar <installer_file> -console`  
 
## 注意
  - **NemakiWareのインストール前に、CouchDBをインストール・起動しておいてください。**  
  - インストーラの各項目はスキップ可能です。たとえば:  
    - CouchDBだけ再び初期化できます。
    - WARファイルやTomcatサーバだけアップデートできます。

# 起動
- NemakiWareを起動する前に、CouchDBが起動済みが確認してください。
- 確認できたら、次のコマンドでTomcatサーバを起動するだけです。  
  `sh <TOMCAT_PATH>/bin/startup.sh`