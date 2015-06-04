# Data dump/load tool
## Tool
`<INSTALL_PATH>/setup/couchdb/bjornloka.jar`  

This tool dumps all data from CouchDB in JSON format and loads such data to the database.  

## Dump
`java -cp bjornloka.jar jp.aegif.nemaki.bjornloka.Dump <host_address> <db_port> <repository_id> <dump_file_path> <time_stamp_flag>`

**host_address**: defaults to `127.0.0.1`  
**db_port**: defaults to `5984`  
**repository_id**: defaults to `bedroom`  
**dump_file_path**: the path to a target file  
**time_stamp_flag**: (optional) defaults to true. If it's false, time stamp suffix is not attached to the dump file.  

So, the command will be like:  
`java -cp bjornloka.jar jp.aegif.nemaki.bjornloka.Dump 127.0.0.1 5984 bedroom ~/Desktop/dump`

## Load
`java -cp bjornloka/target/bjornloka.jar jp.aegif.nemaki.bjornloka.Load <host_address> <db_port> <repository_id> <dump_file_path> <overwrite_flag>`  

**host_address**: defaults to `127.0.0.1`  
**db_port**: defaults to `5984`  
**repository_id**: defaults to `bedroom`  
**dump_file_path**: the path of a source file to load  
**overwrite_flag**: (optional) defaults to false. If it's true, overwrite CouchDB database which has the same name as \<repository_id\>  

So, the command will be like:  
`java -cp bjornloka/target/bjornloka.jar jp.aegif.nemaki.bjornloka.Load 127.0.0.1 5984 bedroom ~/Desktop/dump true`

# Data initialization
Load initialization data using the [dump/load tool](https://github.com/aegif/NemakiWare/wiki/Maintenance(Database)#data-dumpload-tool).  

Initialization data are:  
`<INSTALL_PATH>/setup/couchdb/initial_import/bedroom_init.dump`  
`<INSTALL_PATH>/setup/couchdb/initial_import/archive_init.dump`  
# Repository initialization
`java -cp bjornloka/target/bjornloka.jar jp.aegif.nemaki.bjornloka.Load <host_address> <db_port> <repository_id> bedroom_init.dump true`
# Repository archive initialization
`java -cp bjornloka/target/bjornloka.jar jp.aegif.nemaki.bjornloka.Load <host_address> <db_port> <repository_id> archive_init.dump true`

# CouchDB UI
## Futon
`http://localhost:5984/_utils/` 