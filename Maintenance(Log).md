# Production environment
At the moment, the logs of all the applications(repository, UI, Solr) are put into tomcat `catalina.out`.

# Repository
## Default logger
### Highly configurable
You can configure the properties in the ordinary way.  
See [this link](https://github.com/aegif/NemakiWare/wiki/Configuration%28Repository%29:-Property).  

Log properties are found in the log section in [nemakiware.properties](https://github.com/aegif/NemakiWare/blob/master/core/src/main/webapp/WEB-INF/classes/nemakiware.properties).

Example:  
- target methods  
  Default to "CMIS" API
- log4j setting file  
  A custom setting file other than log4j.xml can be specified by Spring framework.
- whether to return a value or not  
etc.

