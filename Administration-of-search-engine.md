---
As a full-text search engine, NemakiWare adopts Solr4.  

## UI
By default,  
http://localhost:8983/solr

##Architecture
Solr is connected with CMIS server via CMIS interface.  
Solr retrieves delta of CMIS change log by several interval(cron). By default 30 seconds. 
  
There are two cores:  
* nemaki  
All of the tracked data are stored here.
* token  
The last read changeToken of the change log is registered in Solr, "token" core.

## Configuration of index
`<INSTALL_PATH>/nemakisolr/solr/nemaki/conf/schema.xml` defines Solr index scheme.  