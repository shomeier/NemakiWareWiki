[English](https://github.com/aegif/NemakiWare/wiki/Install-CouchDB)/日本語
***

NemakiWare は [Apache CouchDB](http://couchdb.apache.org/) をバックエンドのデータベースして採用しています。NemakiWareのインストールの前に、CouchDBをインストールしておく必要があります（NemakiWare のインストーラでは CouchDB はインストールされません）

##CouchDB インストール TIPS
###インストーラ
[CouchDBの公式サイト](http://couchdb.apache.org/)からパッケージインストーラをダウンロードできます。  
現在 Mac 版、Windows 版のパッケージインストーラがあります。

###Mac
HomeBrew か MacPorts を利用してインストールする場合、[CouchDB の Wiki ページ](http://wiki.apache.org/couchdb/Installing_on_OSX)を参照下さい。

###Ubuntu
Ubuntu へのインストールは [CouchDB の Wiki ページ](http://wiki.apache.org/couchdb/Installing_on_Ubuntu)を参照下さい。  

また、Ubuntuに関しては[ここ](https://github.com/bdossantos/puppet-module-couchdb) にある Vagrant のプロジェクトが参考になります。  VMを precise64 から quantal64 に変更することで 12.10 へ NemakiWare をインストールするための最小要件を満たします。

```sh
config.vm.box = "quantal64"
config.vm.box_url = "https://github.com/downloads/roderik/VagrantQuantal64Box/quantal64.box"
```
(Thanks to [jlank](https://github.com/jlank))

###CentOS
CentOS へのインストールも[CouchDB の Wiki ページ](http://wiki.apache.org/couchdb/Installing_on_RHEL5)を参照して下さい。EPELリポジトリを有効にしておく必要があります。