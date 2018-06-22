---
As a full-text search engine, NemakiWare uses Solr4.  

## UI

By default,  
- Tomcat<br>
http://localhost:8080/solr
- Development<br>
http://localhost:8983/solr

## Architecture

Solr is connected with CMIS server via CMIS interface retrieveing delta of CMIS change log by several interval.  
The interval can be set by cron (by default 30 seconds).
  
There are two cores:  
* nemaki  
All of the tracked data are stored here.
* token  
The last read changeToken of the change log is registered in Solr, "token" core.

## Configuration of index

`<INSTALL_PATH>/nemakisolr/solr/nemaki/conf/schema.xml` defines Solr index scheme.

## Initialization and Reindex
### API  
Accessing the following URL executes full reindexing.  
The last changeToken is also initialized.  
`http://localhost:8983/solr/admin/cores?core=nemaki&action=init`

Accessing the following URL executes full reindexing from the last changeToken.  
`http://localhost:8983/solr/admin/cores?core=nemaki&action=index&tracking=FULL`

### UI  
If you are an administrator, you can see the buttons for search engine administration on the top header of UI.
