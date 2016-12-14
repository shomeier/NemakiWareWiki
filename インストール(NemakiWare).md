[English](https://github.com/aegif/NemakiWare/wiki/Install%28NemakiWare%29)/日本語 
***
# 必要環境
- Linux/Windows/Mac
- Java
  * NemakiWare 2.3 ： Java 7
  * NemakiWare 2.4 ： Java 8, Servlet 3.1+
- CouchDB  
  (CouchDBはあらかじめインストールしておく必要があります [こちらを参照](https://github.com/aegif/NemakiWare/wiki/%E3%82%A4%E3%83%B3%E3%82%B9%E3%83%88%E3%83%BC%E3%83%AB%28CouchDB%29))


# インストーラによるインストール
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

## 起動
- NemakiWareを起動する前に、CouchDBが起動済みが確認してください。
- 確認できたら、次のコマンドでTomcatサーバを起動するだけです。  
  `sh {TOMCAT_PATH}/bin/startup.sh`

# インストーラ同梱のTomcatを使わず、任意の場所に配置する
任意の Tomcat に配置する方法を記載します。インストーラでいったんインストールした後、必要なファイルを移動するのが楽です。以下の説明では、インストーラで入れた NemakiWare のホームを {INSTALL_HOME} 、動かしたい Tomcat の Home ディレクトリを {TOMCAT_HOME} と記載します。

## warファイルのコピー

`{INSTALL_HOME}/apache-tomcat-x.x.x/webapps`

以下にある

* ui.war
* core.war
* solr.war

を、 `{TOMCAT_HOME}/webapps` ディレクトリ以下にコピーします。

## shared/classs をコピー
`{INSTALL_HOME}/apache-tomcat-x.x.x/` にある shared ディレクトリを `{TOMCAT_HOME}/` 以下にコピーします（フォルダがなければ作成します）。

## conf/Catalina をコピーして設定
`{INSTALL_HOME}/apache-tomcat-x.x.x/conf/` にある Catalina ディレクトリを `{TOMCAT_HOME}/conf` 以下にコピーし、

`{TOMCAT_HOME}/conf/Catalina/localhost/solr.xml`

をエディタで開きます。

```
<?xml version="1.0" encoding="utf-8"?>
<Context docBase="{INSTALL_HOME}/apache-tomcat-x.x.x/webapps/solr" crossContext="true">
  <Environment name="solr/home" type="java.lang.String" value="{INSTALL_HOME}/solr" override="true"/>
</Context>
```
を
```
<?xml version="1.0" encoding="utf-8"?>
<Context docBase="{TOMCAT_HOME}/webapps/solr" crossContext="true">
  <Environment name="solr/home" type="java.lang.String" value="{INSTALL_HOME}/solr" override="true"/>
</Context>
```
に変更します（docBase属性）

なお、Environment 要素に書かれている `{INSTALL_HOME}/Solr` というパスは同梱されている Solr エンジンの場所です。これ自体は、Webアプリケーションではなく、Tomcat とは関係ありませんので、NemakiWare 自体を新しい Tomcat に配置する場合でも、インストール時のもとの場所のままにしておいても動きます。インストーラで作られた場所は最終的にすべてキレイにしておきたいと言うことであれば、この Solr ディレクトリを /opt/solr などに移動し、 solr.xml の Environment name="solr/home" の value 値を新しい場所を指し示すように書き換えることができます。

## 設定
`{TOMCAT_HOME}/conf/catalina.properties`

をエディタで開きます。

`shared.loader=`

を

`shared.loader=${catalina.base}/shared/classes`

に書き換えます。

## その他

必要であれば

`{INSTALL_HOME}/apache-tomcat-x.x.x/bin/setenv.sh` (Windowsであればsetenv.bat）

も

`{TOMCAT_HOME}/bin/`

以下にコピーしておきます。Tomcat 起動時の Java のメモリサイズなどが書かれています。

## 確認
`{TOMCAT_HOME}/bin/startup.sh`(Windowsであればstartup.bat）

をキックして起動させます。

`http://localhost:8080/ui/repo/bedroom/`

の表示を確認します、ログイン画面が表示されれば ui.war が動いていることが確認できます（サーブレットのエラーが出る場合は、Tomcatのバージョンに注意して下さい。NemakiWare 2.4 以降は Serverlet 3.1 対応のため、Tomcat 8 以降が必須となります）

admin ユーザでログインします。ログインできれば、core.war が動いていることが確認できます。

適当なファイルを置き、ファイル名で検索し、そのファイルが検索できることを確認します。検索できれば solr.war が動いていることが確認できます。


