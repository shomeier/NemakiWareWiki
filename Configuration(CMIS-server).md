---

## Configuration architecture
* CMIS server is based on Spring framework, and all of the configuration setting is centralized in Spring propertyConfigurator.  
* Property files can be overwritten. They are overwritten in the following order. (More below, more precedent.)  
For the detail, please see `<SOURCE_PATH>/nemakiware/src/main/webapp/WEB-INF/classes/propertyContextxml`.

  1. `<SOURCE_PATH>/nemakiware/src/main/webapp/WEB-INF/classes/nemakiware.properties` (and some other sub property files)
  2. `<SOURCE_PATH>/nemakiware/src/main/resources/custom-nemakiware.properties`  
(If NemakiWare works in production Tomcat environment:)
  3. `<INSTALL_PATH>/apache-tomcat-7.x.xx/shared/classes/app-server-couchdb.properties`
  4. `<INSTALL_PATH>/apache-tomcat-7.x.xx/shared/classes/app-server-solr.properties`
  5. `<INSTALL_PATH>/apache-tomcat-7.x.xx/shared/classes/app-server-general.properties`  
  

* For developer, `custom-nemakiware.properties` is the most important. Every customization should be put here.
* For administrator, `app-server-xxx.properties` are the most important. They take user inputs. 
* Spring context configuration XML files are also described in property files. So you can replace the back end etc. as you like.

---
* Note: You can define a new property key for your customization use, please pay attention to avoid conflict of property keys.