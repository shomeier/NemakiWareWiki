# Change properties
`<TOMCAT_PATH>/shared/classes/app-server-core.properties`

# List of properties
(TODO: link)

#Referenced setting files
Some setting files are designated by a property.  
They are specified by name (not by path) and loaded by the class loader.  
You can change it to your own custom file put under, for example, `<TOMCAT_PATH>/shared/classes`.  
Original setting files are in `<SOUCE_PATH>/core/src/main/webapp/WEB-INF/classes`.  
## Permission
- `permission.yml`  
  Defines all kinds of permission(cmis:read, cmis:write, etc.)  
- `permission-mapping.yml`  
  Defines the mapping between an CMIS action(e.g.`canDelete.Object`) and required permissions to execute it  
## Log
-   
## Other