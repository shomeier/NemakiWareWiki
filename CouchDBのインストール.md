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
####Version 5系
CentOS へのインストールも[CouchDB の Wiki ページ](http://wiki.apache.org/couchdb/Installing_on_RHEL5)を参照して下さい。EPELリポジトリを有効にしておく必要があります。

####Version 6系
上記のやり方では上手く行きません。下記のスクリプトを参考にインストールを試みてください。

```sh
#!/bin/sh

##Installing general tools
sudo yum -y update
sudo yum -y groupinstall "Development Tools"
sudo yum -y install libicu-devel curl-devel ncurses-devel libtool libxslt fop java-1.6.0-openjdk java-1.6.0-openjdk-devel unixODBC unixODBC-devel openssl-devel

## Preparing working directory
mkdir couchdb_install
DIR=$(cd $(dirname $0); pwd)/couchdb_install
echo $DIR

##Installing Erlang
cd $DIR
wget http://www.erlang.org/download/otp_src_17.4.tar.gz
tar -zxvf otp_src_17.4.tar.gz
cd $DIR/otp_src_17.4
./configure && make
sudo make install


##Install the SpiderMonkey JS Engine
cd $DIR
wget http://ftp.mozilla.org/pub/mozilla.org/js/js185-1.0.0.tar.gz
tar -zxvf js185-1.0.0.tar.gz 
cd $DIR/js-1.8.5/js/src
./configure && make
sudo make install

##Installing CouchDB
cd $DIR
wget http://apache.osuosl.org/couchdb/source/1.6.1/apache-couchdb-1.6.1.tar.gz
tar -zxvf apache-couchdb-1.6.1.tar.gz
cd apache-couchdb-1.6.1
./configure && make
sudo make install

##Setting up CouchDB
sudo adduser --no-create-home couchdb
sudo chown -R couchdb:couchdb /usr/local/var/lib/couchdb /usr/local/var/log/couchdb /usr/local/var/run/couchdb
###Insert path so that SpiderMonkey JavaScript engine works
sudo sed -i".original" -e '25i\export LD_LIBRARY_PATH=/usr/local/lib' /usr/local/etc/rc.d/couchdb 
sudo ln -sf /usr/local/etc/rc.d/couchdb /etc/init.d/couchdb
sudo chkconfig --add couchdb
sudo chkconfig couchdb on
sudo service couchdb start

##Deleting working files
rm -rf $DIR

##Complete
echo 'CouchDB installtion completed!'
```
