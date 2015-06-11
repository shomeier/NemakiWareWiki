English/[日本語](https://github.com/aegif/NemakiWare/wiki/%E3%82%A4%E3%83%B3%E3%82%B9%E3%83%88%E3%83%BC%E3%83%AB%28CouchDB%29)
***
NemakiWare use [CouchDB](http://couchdb.apache.org/) as its back end, so first of all you must install CouchDB by yourself.  
NemakiWare installer does not install CouchDB.

##CouchDB installation TIPS
###Package installer
The most comfortable way is to download a CouchDB package installer from [Official Page](http://couchdb.apache.org/).  

You can also install it by your package system.

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
However, EPEL repository may be stale at present.

In order to install CouchDB and some dependencies from source code, we provide the script:  
[Link](https://github.com/aegif/NemakiWare/blob/master/setup/couchdb/couchdb_install_centos6.sh)  
