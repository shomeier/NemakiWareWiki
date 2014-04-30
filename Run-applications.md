---
##Prerequisites
* CouchDB must be installed beforehand. See [this page](https://github.com/NemakiWare/NemakiWare/wiki/Install-CouchDB).
* Java1.6+
* Ruby 1.9.3
* (Ruby gem)bundler, rake10.1.1

In production environment, Rails is installed from local gem cache.  
Especially, in Windows, we use [RailsInstaller](http://railsinstaller.org/en) to install bundler, rake, Rails itself and some other components.

## Run the CMIS server and the search engine
The CMIS server and the search engine are installed in Tomcat(`<INSTALL_PATH>/apache-tomcat-7.x.xx`).  
Run Tomcat by `<TOMCAT_PATH>/bin/startup.sh` or `<TOMCAT_PATH>/bin/startup.bat`.

## Run the client
Move to `<INSTALL_PATH>/nemakishare`, then run Rails application.  
  ```sh
$ rails s
```

* Note:Though the launching order is free, it would be desirable to run the server firstly because the client tries to get CMIS change log from the server.

## Login
Open the client URL `http://127.0.0.1:3000/nodes/` (default).
* ID: admin (default)
* Password: admin (default)