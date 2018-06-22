---
## UI
CouchDB has its user interface called "Futon".  
By default,  
http://localhost:5984/_utils/

## Databases
A CouchDB instance can have multiple "database", which is something like a table in relational databases.  
NemakiWare creates and uses the following databases:  

* main (by default, "bedroom")
* archive

Main database stores almost all the data and the query view for NemakiWare, while archive database stores archived data of deleted items.

### Note
Secure connection to CouchDB(Basic Auth, Proxy etc.) is not supported by NemakiWare at present.