[English](https://github.com/aegif/NemakiWare/wiki/Home)/日本語
***

リンク先が英語の場合があります。日本語化は随時進めていきます。

ユーザ向け:
* [NemakiWareへのアクセスとログイン](https://github.com/aegif/NemakiWare/wiki/NemakiWare%E3%81%B8%E3%81%AE%E6%8E%A5%E7%B6%9A)

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
 * [ログの出力](https://github.com/aegif/NemakiWare/wiki/%E3%83%AD%E3%82%B0%E3%81%AE%E5%87%BA%E5%8A%9B)

開発者向け:
* [開発前の準備](https://github.com/NemakiWare/NemakiWare/wiki/Prerequisites-for-development)
* [開発をはじめるには](https://github.com/NemakiWare/NemakiWare/wiki/Start-development)
* [インストーラの作成方法](https://github.com/NemakiWare/NemakiWare/wiki/Generate-an-installer)
* [簡易クライアント CMIS Workbench について](https://github.com/aegif/NemakiWare/wiki/CMIS-Workbench%EF%BC%88%E7%B0%A1%E6%98%93%E3%82%AF%E3%83%A9%E3%82%A4%E3%82%A2%E3%83%B3%E3%83%88%EF%BC%89)
* [設定方法（CMISサーバ）](https://github.com/NemakiWare/NemakiWare/wiki/Configuration%28CMIS-server%29)
* [設定方法（全文検索エンジン）](https://github.com/NemakiWare/NemakiWare/wiki/Configuration%28search-engine%29)
* [設定方法（Web UI クライアント）](https://github.com/NemakiWare/NemakiWare/wiki/Configuration%28Client%29)
* [DAOを差し替えて他のDBを使うには](https://github.com/aegif/NemakiWare/wiki/Note-on-writing-another-DAO)
* [CMIS APIの利用](https://github.com/aegif/NemakiWare/wiki/CMIS-API-%E3%81%AE%E5%88%A9%E7%94%A8)

---
このWiki内では、パス内で次のような文字を使っています。

<table style="width:10%; border:0; font-size:1em;">
<tr><th>Variable</th><th>Description</th></tr>
<tr><td>&lt;INSTALL_PATH&gt;</td><td>インストーラのパス</td></tr>
<tr><td>&lt;TOMCAT_PATH&gt;</td><td>TOOMCATのインストールパス<br/> <br/>&lt;INSTALL_PATH&gt;/apache-tomcat-8.x.xx/ と同じ</td></tr>
<tr><td>&lt;SOURCE_PATH&gt;</td><td>ソースコードのルートパス。<br/>GitHubからクローンした場合は、NemakiWareフォルダの直下になります。</td></tr>
</table>