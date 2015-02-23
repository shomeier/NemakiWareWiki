[English](https://github.com/aegif/NemakiWare/wiki/Home)/日本語
***

リンク先が英語の場合があります。日本語化は随時進めていきます。

ユーザ向け:
* 接続先 URL
  * Web UI クライアントの URL: `http://<servername>:<port>/ui/`  
ブラウザから利用する場合はこの URL へアクセスします。
  * CMISサーバURL
  別の CMIS クライアントや CmisSync などで URL を指定する場合は以下を利用します。
    * AtomPub形式で接続 : `http://<servername>:<port>/core/atom/bedroom`
    * JSON形式で接続 : `http://<servername>:<port>/core/browser/bedroom`
* オンライントライアルサイト（ユーザ名: `admin` パスワード: ユーザ名と同じ）
  * Web UI クライアントの URL:  `http://trial.nemakiware.com:8080/ui/` 
  * CMISサーバURL(AtomPub形式で接続): `http://trial.nemakiware.com:8080/core/atom/bedroom`
  * CMISサーバURL(JSON形式で接続): `http://trial.nemakiware.com:8080/core/browser/bedroom`

システム管理者向け:
* インストール
 * [インストール前の準備](https://github.com/aegif/NemakiWare/wiki/%E3%82%A4%E3%83%B3%E3%82%B9%E3%83%88%E3%83%BC%E3%83%AB%E5%89%8D%E3%81%AE%E6%BA%96%E5%82%99)
 * [CouchDBのインストール](https://github.com/NemakiWare/NemakiWare/wiki/Install-CouchDB)
 * [NemakiWareのインストール (サーバ、全文検索エンジン、Webクライアント）](https://github.com/aegif/NemakiWare/wiki/NemakiWare%E3%81%AE%E3%82%A4%E3%83%B3%E3%82%B9%E3%83%88%E3%83%BC%E3%83%AB)
 * [NemakiWare起動方法](https://github.com/aegif/NemakiWare/wiki/NemakiWare%E8%B5%B7%E5%8B%95%E6%96%B9%E6%B3%95)
 * [インストール後の設定](https://github.com/aegif/NemakiWare/wiki/%E3%82%A4%E3%83%B3%E3%82%B9%E3%83%88%E3%83%BC%E3%83%AB%E5%BE%8C%E3%81%AE%E8%A8%AD%E5%AE%9A)
* 管理
 * [CMISサーバの管理方法](https://github.com/NemakiWare/NemakiWare/wiki/Administration-of-CMIS-server)
 * [CouchDBの管理について](https://github.com/NemakiWare/NemakiWare/wiki/Administration-of-CouchDB)
 * [CouchDBのデータ保守](https://github.com/NemakiWare/NemakiWare/wiki/Dump-or--load-with-CouchDB)
 * [全文検索エンジンの管理について](https://github.com/NemakiWare/NemakiWare/wiki/Administration-of-search-engine)
 * [クライアントの管理について](https://github.com/NemakiWare/NemakiWare/wiki/Administration-of-client)
 * [データの初期化](https://github.com/NemakiWare/NemakiWare/wiki/Data-initialization)

開発者向け:
* [開発前の準備](https://github.com/NemakiWare/NemakiWare/wiki/Prerequisites-for-development)
* [開発をはじめるには](https://github.com/NemakiWare/NemakiWare/wiki/Start-development)
* [インストーラの作成方法](https://github.com/NemakiWare/NemakiWare/wiki/Generate-an-installer)
* [CMISワークベンチについて](https://github.com/NemakiWare/NemakiWare/wiki/CMIS-Workbench%28Simple-client%29)
* [設定方法（CMISサーバ）](https://github.com/NemakiWare/NemakiWare/wiki/Configuration%28CMIS-server%29)
* [設定方法（全文検索エンジン）](https://github.com/NemakiWare/NemakiWare/wiki/Configuration%28search-engine%29)
* [設定方法（Web UI クライアント）](https://github.com/NemakiWare/NemakiWare/wiki/Configuration%28Client%29)
* [DAOを差し替えて他のDBを使うには](https://github.com/aegif/NemakiWare/wiki/Note-on-writing-another-DAO)

---
このWiki内では、パス内で次のような文字を使っています。

<table style="width:10%; border:0; font-size:1em;">
<tr><th>Variable</th><th>Description</th></tr>
<tr><td>&lt;INSTALL_PATH&gt;</td><td>インストーラのパス</td></tr>
<tr><td>&lt;TOMCAT_PATH&gt;</td><td>TOOMCATのインストールパス<br/> <br/>&lt;INSTALL_PATH&gt;/apache-tomcat-8.x.xx/ と同じ</td></tr>
<tr><td>&lt;SOURCE_PATH&gt;</td><td>ソースコードのルートパス。<br/>GitHubからクローンした場合は、NemakiWareフォルダの直下になります。</td></tr>
</table>