---

##NemakiShare
NemakiWare provides CMIS client called "NemakiShare".  
This name implies the concept of collaboration.

##Main feature  
* Basic CRUD user interface
* Collaborative "Site" 
* Administrator console

###Basic CRUD
* Navigation in the folder hierarchy
* Detailed information window on each document/folder
* Action button on a document/folder
* Breadcrumb

###Site
In reality, a site is a folder.  
The folder is managed by permissions, and those who have permissions are considered as site's members.  

In navigation UI, "recently modified items" column is displayed to the site's members.  

###Administration console
* User/Group(CRUD)  
* Archive  
Administrator can view and restore archived items.  
* Solr  
Administrator can initialize and reindex Solr.

##Site architecture
The "recently modified items" are retrieved from CMIS change log.  
To subscribe the change log, NemakiShare stores in its SQLite3 database:  
* the last changeToken
* old change logs (not to go to get them again)

Subscription of the change log is executed by cron([rufus-scheduler](https://github.com/jmettraux/rufus-scheduler)).

###Initializing the stored change log
> rake db:migrate:reset