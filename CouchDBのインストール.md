[English](https://github.com/aegif/NemakiWare/wiki/Install-CouchDB)/日本語
***

NemakiWare は [Apache CouchDB](http://couchdb.apache.org/) をバックエンドのデータベースして採用しています。NemakiWareのインストールの前に、CouchDBをインストールしておく必要があります（NemakiWare のインストーラでは CouchDB はインストールされません）

##CouchDB インストール TIPS
###パッケージ
[CouchDBの公式サイト](http://couchdb.apache.org/)からパッケージインストーラをダウンロードできます。  
現在 Mac 版と Windows 版があります

###Mac
If you want to use HomeBrew or MacPorts, see [Wiki](http://wiki.apache.org/couchdb/Installing_on_OSX).

###Ubuntu
See [Wiki](http://wiki.apache.org/couchdb/Installing_on_Ubuntu).  

[This Vagrant project](https://github.com/bdossantos/puppet-module-couchdb) would be also helpful.  
To change the VM from precise64 to quantal64 locally to meet the 12.10 minimum requirement for NemakiWare,
```sh
config.vm.box = "quantal64"
config.vm.box_url = "https://github.com/downloads/roderik/VagrantQuantal64Box/quantal64.box"
```
(Thanks to [jlank](https://github.com/jlank))

###CentOS
See [Wiki](http://wiki.apache.org/couchdb/Installing_on_RHEL5).  
You must enable EPEL repositories.