---

## Architecture 
* `<INSTALL_PATH>/setup/couchdb/bjornloka` is an maven project for dump/load of CouchDB.
* In this project, there are simple Java applications with main method for dump/load.

##Initial Data
Official dump files for initialization are in `<INSTALL_PATH>/setup/couchdb/initial_import`.

##Procedure
###Dump
Run `jp.aegif.nemaki.bjornloka.Dump` with the following arguments.  

Parameters(in this order):

<table>
<tr><th>Argument</th><th>Description</th></tr>
<tr><td>host</td><td>CouchDB host<br/>ex. 127.0.0.1</td></tr>
<tr><td>port</td><td>CouchDB port<br/>ex. 5984</td></tr>
<tr><td>repositoryId</td><td>Target CouchDB database name<br/>ex. bedroom</td></tr>
<tr><td>filePath</td><td>Full path of dump destination file<br/>By default, timestamp will be attached to this filePath.</td></tr>
<tr><td>omitTimestamp<br/>(optional)</td><td>If this boolean flag is true, a dump file name has no attached timestamp.</td></tr>
</table>

###Load
Run `jp.aegif.nemaki.bjornloka.Load` with the following arguments.  

Parameters(in this order):

<table>
<tr><th>Argument</th><th>Description</th></tr>
<tr><td>host</td><td>CouchDB host<br/>ex. 127.0.0.1</td></tr>
<tr><td>port</td><td>CouchDB port<br/>ex. 5984</td></tr>
<tr><td>repositoryId</td><td>Target CouchDB database name<br/>ex. bedroom</td></tr>
<tr><td>filePath</td><td>Full path of a file to be loaded<br/></td></tr>
<tr><td>force<br/>(optional)</td><td>When the target repository already exists, if this boolean flag is true, delete and recreate the repository with loaded data.</td></tr>
</table>

###Interactive Setup
You can also all load dump files required for NemakiWare at the same time in the interactive mode on the terminal.  
Run `jp.aegif.nemaki.bjornloka.Setup`.  
Of course it works with no arguments, it can also take the following arguments in this order.

<table>
<tr><th>Argument</th><th>Description</th></tr>
<tr><td>host</td><td>CouchDB host<br/>ex. 127.0.0.1</td></tr>
<tr><td>port</td><td>CouchDB port<br/>ex. 5984</td></tr>
<tr><td>mainRepositoryId</td><td>Target CouchDB database name(main)<br/>ex. bedroom</td></tr>
<tr><td>archvieRepositoryId</td><td>Target CouchDB database name(main)<br/>ex. archive</td></tr>
<tr><td>mainFilePath</td><td>Full path of a file to be loaded in the main repository<br/></td></tr>
<tr><td>archiveFilePath</td><td>Full path of a file to be loaded in the archive repository<br/></td></tr>
</table>
