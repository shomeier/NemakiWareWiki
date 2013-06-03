### NemakiWare

---


NemakiWare is a open source enterprise content management(ECM) system. It is:
* **Compliant with CMIS standard**

  Integration or replacement with other existing/future CMIS compliant software can be done easuily by the power of standard
* **NoSQL CouchDB backend** 

  Simple and easy to manage document based NoSQL database.
* **All-in-One package(Server, Client, Search engine)** 

  CMIS defines just the core of ECM. You need some peripheral components/feature, and here it is. 


"Nemaki" derives from Japanese word "寝巻き" which means night clothes and you can relax and enjoy your enterprise time as you lie on a couch in your room!

### Prerequisite for installation
* Java 1.6, Ruby 1.9.3p362, Rails 3.2.11
* CouchDB 1.0.6, Maven 3.x
* Platform: OSX 10.8.3 or CentOS 6 (Although Windows is not tested, NemakiWare is basically platform-agnostic).

### Installation
* Clone the repository
    >git@github.com:NemakiWare/NemakiWare.git
You get the folder <NemakiWare_Home>, which includes three subfolders nemakiware, nemakisolr, nemakishare.

* Install CouchDB

Mac(See [Wiki](http://wiki.apache.org/couchdb/Installing_on_OSX))
    >sudo port install couchdb

CentOS
    >sudo yum install couchdb

* Setup CouchDB (If it's not started, start it before setup)
    
    >cd <NemakiWare_Home>/nemakiware/setup
    >sh setup.sh
* Install and kick the server
    
    >cd <NemakiWare_Home>/nemakiware
    >mvn jetty:run
It will take a little time to download the dependent packages.

