# Prerequisites
* Linux/Windows/Mac
* Java 1.6+
* CouchDB<br>
  (You must install by yourself CouchDB)

# Installer
Installer runs on multi-platform.  

## Download the latest installer  
[https://github.com/aegif/NemakiWare/releases](https://github.com/aegif/NemakiWare/releases)

## Run the installer
  - GUI  
    Simply click the execution file, or `java -jar <installer_file>`  
  - CUI  
    `java -jar <installer_file> -console`  
  - Installer is build using [IzPack](http://izpack.org/).  

## Note
  - **You must install and start CouchDB before this installation.**  
  - Each item in the installer can be skipped. For example:  
    - You can reinitialize only CouchDB.  
    - You can update only war files + tomcat server.  

# Start up
- Make sure you have already run CouchDB before starting NemakiWare
- Then, all you need to do is just run the tomcat server  
  `sh <TOMCAT_PATH>/bin/startup.sh`