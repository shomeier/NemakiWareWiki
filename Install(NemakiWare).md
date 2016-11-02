English/[日本語](https://github.com/aegif/NemakiWare/wiki/%E3%82%A4%E3%83%B3%E3%82%B9%E3%83%88%E3%83%BC%E3%83%AB%28NemakiWare%29) 
***
# Prerequisites
* Linux/Windows/Mac
* Java 1.7+ ( Nemakiware 2.4 or later require Java 8+）
* CouchDB<br>
  (You must install by yourself CouchDB. [See](Install(CouchDB)))

# Installer
- Installer runs on multi-platform.  
- Installer is build using [IzPack](http://izpack.org/). 

## Download the latest installer  
[https://github.com/aegif/NemakiWare/releases](https://github.com/aegif/NemakiWare/releases)

## Run the installer
  - GUI  
    Simply click the execution file, or `java -jar <installer_file>`  
  - CUI  
    `java -jar <installer_file> -console`  
 
## Note
  - **You must install and start CouchDB before this installation.**  
  - Each item in the installer can be skipped. For example:  
    - You can reinitialize only CouchDB.  
    - You can update only war files + tomcat server.  

# Start up
- Make sure you have already run CouchDB before starting NemakiWare
- Then, all you need to do is just run the tomcat server  
  `sh <TOMCAT_PATH>/bin/startup.sh`