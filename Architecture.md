# Components
- CMIS repository
- User interface
- Solr
- CouchDB

# Application Server
All the components except database are contained in a Tomcat server.  

# CMIS compliant
(TODO: image)  
NemakiWare is CMIS compliant and built upon [Apache Chemistry](http://chemistry.apache.org/)'s [OpenCMIS](http://chemistry.apache.org/java/opencmis.html) library.
- UI connects to the repository via CMIS
- Our custom Solr also connects to the repository via CMIS