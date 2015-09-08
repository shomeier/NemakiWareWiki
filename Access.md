English/[日本語](https://github.com/aegif/NemakiWare/wiki/%E3%82%A2%E3%82%AF%E3%82%BB%E3%82%B9)
***
#Default credentials
- ID: admin
- PWD: admin

# Access URL
`localhost:8080` may vary depending on your configuration.
## UI
`http://localhost:8080/ui/repo/<repository_name>/login`

Default installed:
* `http://localhost:8080/ui/repo/bedroom/login`
* `http://localhost:8080/ui/repo/bedroom2/login`

## CMIS repository
There is some protocol to connect to the repository.  
- AtomPub  
`http://localhost:8080/core/atom/bedroom`
- WebServices  
`http://localhost:8080/core/services/bedroom`

# Using OpenCMIS Workbench
[CMIS Workbench](https://chemistry.apache.org/java/developing/tools/dev-tools-workbench.html), provided by [Apache Chemistry](http://chemistry.apache.org/), is a simple GUI client with comprehensive test tools.  
It is useful when:
- NemakiWare UI displays some error
- you are debugging
- no web user interface is required and it's enough to look into the repository.