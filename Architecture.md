English/日本語 
***
# Components
## CMIS repository
- CMIS functionalities
- Additional API
  - User/Group, Archive etc.  

## CouchDB
- NoSQL database
- NemakiWare creates two "tables" in CouchDB
  - `bedroom`: main database to store all the available nodes  
  - `archive`: archive database to store all the deleted nodes  

## User interface

## Solr
- Full text search engine for both metadata and content
- Connects to the repository at certain intervals (every 30sec by default).  

# Application Server
All the components except database are contained in a Tomcat server.  

# CMIS compliant
(TODO: image)  
NemakiWare is CMIS compliant and built upon [Apache Chemistry](http://chemistry.apache.org/)'s [OpenCMIS](http://chemistry.apache.org/java/opencmis.html) library.
- UI connects to the repository via CMIS
- Our custom Solr also connects to the repository via CMIS