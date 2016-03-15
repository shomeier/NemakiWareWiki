English/[日本語](https://github.com/aegif/NemakiWare/wiki/%E7%92%B0%E5%A2%83%E8%A8%AD%E5%AE%9A%28%E3%83%AA%E3%83%9D%E3%82%B8%E3%83%88%E3%83%AA%29:-%E3%82%AA%E3%83%96%E3%82%B8%E3%82%A7%E3%82%AF%E3%83%88%E3%82%BF%E3%82%A4%E3%83%97) 
***
# What is CMIS object type?
## "Class" of each "instance"(document/folder)
- In CMIS domain model, object type defines each object(document/folder)'s "class".
- Object type specify a set of object's properties.
- Object type has its own attributes besides the properties.

## CMIS basic type
- cmis:document, cmis:folder etc. are predefined in CMIS.

## Custom type
- You can add your own custom object type with additional custom properties.
- There are the inheritance system of object types.
- Any custom object type must inherits another object type(including basic type).

# View object type's detail
UI: Admin console > Type  
(TODO:image)  
- Clicking a button next to each type allows you to download the object type's definition file in JSON format.  

# Add new object type
UI: Admin console > Type  
(TODO:image)  
- Upload a definition file(JSON).
- The definition file can be edited based on a downloaded file of the inherited type.