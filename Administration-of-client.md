---
##Architecture
CMIS client connects to CMIS server via CMIS interface.
It is written in [Play 2 framework](https://www.playframework.com/) using Java language.

##Main feature  
* Basic CRUD user interface
* Document management specific interface
* Administrator console

###Basic CRUD
* Navigation in the folder hierarchy
* Detailed information window on each document/folder
* Action button on a document/folder
* Breadcrumb

###Document management specific 
* Check out / check in
* Access control
* Preview

###Administration console
* User/Group(CRUD)  
* Solr  
Administrator can initialize and rebuild Solr index.
* Object type  
Administrator can download and upload a json file to create a new object type.