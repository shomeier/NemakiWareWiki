# Change properties
Add properties to be overwrote into:  
`<TOMCAT_PATH>/shared/classes/app-server-core.properties`

# List of properties
In the source code, properties are managed by the Spring context file [propertyContext.xml](https://github.com/aegif/NemakiWare/blob/master/core/src/main/webapp/WEB-INF/classes/propertyContext.xml).  

```
<list>
  <value>classpath:nemakiware.properties</value>
  <value>classpath:nemakiware-capability.properties</value>
  ...
  <value>classpath*:app-server-core.properties</value>
</list>
```
These properties files are loaded in this order, so the latter overwrites the former.  

However, the first following files don't overlap each other.  
All the default properties are described here:
- [**nemakiware.properties**](https://github.com/aegif/NemakiWare/blob/master/core/src/main/webapp/WEB-INF/classes/nemakiware.properties)  
  Properties in this file are the most important and overwrote frequently.  
  
- [nemakiware-capability.properties](https://github.com/aegif/NemakiWare/blob/master/core/src/main/webapp/WEB-INF/classes/nemakiware-capability.properties)  
  Defines CMIS capability. Some item can be configurable, though, basically you should **NOT** change this.  
- [nemakiware-basetype.properties](https://github.com/aegif/NemakiWare/blob/master/core/src/main/webapp/WEB-INF/classes/nemakiware-basetype.properties)  
  Defines CMIS object type's attributes following CMIS specification. Basically you should **NOT** change this.  
- [nemakiware-property.properties](https://github.com/aegif/NemakiWare/blob/master/core/src/main/webapp/WEB-INF/classes/nemakiware-property.properties)  
  Defines CMIS property's attributes following CMIS specification. Basically you should **NOT** change this.  

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
## Other