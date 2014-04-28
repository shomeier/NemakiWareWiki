---

## Configuration architecture
* Property files can be overwritten.
* The base property file is `<SOURCE_PATH>/nemakisolr/solr/conf/nemakisolr.properties`.
* In the base property file, overriding property files are defined by `override.files` key.  
The defined order is the overriding order. Property file names will be searched anywhere under the classpath.
* By default, the most important for developer is `custom-nemakiware.properties`. Every customization should be put here.
* For administrator, `app-server-xxx.properties` are the most important. They take user inputs. 

##Explanation of property
* **solr.tracking.mime.type.filter.enabled**  
If true, full-text index is created only for a document whose MIME type is in `solr.tracking.mime.type`.
* **solr.tracking.mime.type**  
Comma-separated list which defines full-text index allowable MIME types.