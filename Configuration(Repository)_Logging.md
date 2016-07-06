English/[日本語](https://github.com/aegif/NemakiWare/wiki/%E7%92%B0%E5%A2%83%E8%A8%AD%E5%AE%9A%28%E3%83%AA%E3%83%9D%E3%82%B8%E3%83%88%E3%83%AA%29:-%E3%83%97%E3%83%AD%E3%83%91%E3%83%86%E3%82%A3)
***
# Logging configration
After 2.4 onward, default logger outputs JSON format logs, especially with some CMIS specific tweaks.  
Configuration file is [here](https://github.com/aegif/NemakiWare/blob/topic_log/core/src/main/webapp/WEB-INF/classes/log-json-config.json).  

# How to
- The file has the two parts: _global_ and _method_.  
- _global_ works as the default value and its configuration are inherited to each method and fill the missing field.  
- Even when an individual method configuration  does not exist, _global_ configuration will be used so that in almost all cases method specific configuration will not be required.  
For example,  
```
"jp.aegif.nemaki.cmis.service.ObjectService.getObjectByPath":{
			"input":{
				"path":{"type":"simple"}
			}
},
```
has neither _setting_ nor _output_ field, but they are using _global_ default values.  
And you will find some CMIS method names are not on the file!  

## setting
- **uuid**: _boolean_ log record's UUID  
- **name**: _enum_('simple' or 'full') method name.  
- **time**: _boolean_ process time  
- **logTime**: _boolean_ process time (including logging itself)  

## input
- **<method argument name>**: 
  argument name is defined with jp.aegif.nemaki.util.spring.aspect.log.LogParam annotation.
  For CMIS service methods, the names are based on the CMIS specification.
  - **type**: _enum_('simple' or 'full') At present only 'simple' is supported. 'full' outputs toString().
  - **properties**:  {<CMIS Property ID>: _boolean_, ...} format
  - **list**:  
    - **num**: _boolean_  display the number of list items  
    - **item**: _boolean_ display the items itself