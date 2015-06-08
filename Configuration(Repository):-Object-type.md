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
- Any object type must inherits another object type(including basic type).

# View object type's detail
UI: Admin console > Type  
(TODO:image)  
- Clicking a button next to each type allows you to download the object type's definition file in JSON format.  

# Add new object type
UI: Admin console > Type  
(TODO:image)  
- Upload a definition file(JSON).
- The definition file can be edited based on a downloaded file of the inherited type.