---

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