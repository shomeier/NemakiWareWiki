English/[日本語](https://github.com/aegif/NemakiWare/wiki/%E7%92%B0%E5%A2%83%E8%A8%AD%E5%AE%9A%28%E3%83%AA%E3%83%9D%E3%82%B8%E3%83%88%E3%83%AA%29:-%E3%83%97%E3%83%AD%E3%83%91%E3%83%86%E3%82%A3)
***
# Change properties
Add properties to be overwritten into:  
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
  Properties in this file are the most important and overwritten frequently.  
  
- [nemakiware-capability.properties](https://github.com/aegif/NemakiWare/blob/master/core/src/main/webapp/WEB-INF/classes/nemakiware-capability.properties)  
  Defines CMIS capability. Some item can be configurable, though, basically you should **NOT** change this.  
- [nemakiware-basetype.properties](https://github.com/aegif/NemakiWare/blob/master/core/src/main/webapp/WEB-INF/classes/nemakiware-basetype.properties)  
  Defines CMIS object type's attributes following CMIS specification. Basically you should **NOT** change this.  
- [nemakiware-property.properties](https://github.com/aegif/NemakiWare/blob/master/core/src/main/webapp/WEB-INF/classes/nemakiware-property.properties)  
  Defines CMIS property's attributes following CMIS specification. Basically you should **NOT** change this.  

# Dynamic configuration
The above list of property fils define **static** properties.  
Almost all of these can be overwritten by CouchDB configuration **on the fly**, except for CouchDB settings and some repository info metadata.  
Dynamic property within CouchDB takes precedence over static properties.  

# Important properties
## Preview
LibreOffice or OpenOffice must be preinstalled.  
`capability.extended.preview=true`  
and  
  
Linux  
`jodconverter.officehome=/opt/libreoffice4.4`  
Mac    
`jodconverter.officehome=/Applications/LibreOffice.app/Contents`  
Windows  
TODO


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