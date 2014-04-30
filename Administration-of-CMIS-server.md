---
## RepositoryInfo

## Capability

## ObjectType

## Permission
Default permission settings are defined in  
* `<SOURCE_PATH>/nemakiware/src/main/webapp/WEB-INF/classes/permission.yml`  
Define all kinds of permission in NemakiWare
* `<SOURCE_PATH>/nemakiware/src/main/webapp/WEB-INF/classes/permission-mapping.yml`
Define the allowable CMIS action for a permission.  
See [Spec 2.1.12.3.2](http://docs.oasis-open.org/cmis/CMIS/v1.1/os/CMIS-v1.1-os.html#x1-7700012)

### How to modify permission settings?
* permission.yml  
It is referenced by `permission.definition` property key.
* permission-mapping.yml  
It is referenced by `permission.mapping.definition` property key.  

These keys are can be defined anywhere in CMIS server(or Tomcat)'s class path.  
Referenced settings files must be in CMIS server(or Tomcat)'s class path.  
 
You can create custom permission setting files, then 
* declare keys in `app-server-general.propertes` in Tomcat, or  
* declare keys in `custom-nemakiwre.properties` in source code