English/[日本語]()
***
# ver.2.4+
Users and groups are exposed cmis:item, whose object type is respectively _nemaki:user_ and _nemaki:group_.  
Of course you can define a subtype of either _nemaki:user_ or _nemaki:group_, adding some property definitions.  
Existing _User_ and _Group_ entity are automatically converted to cmis:item by Patch system, which are also introduced from ver.2.4.  
For the moment User/Group REST APIs works as before. These APIs output User/Group with the same JSON format as before by converting cmis:item-ized user/group.  

## Constraints  
- User password is not exposed as CMIS property.  
  It means when you create a user item its password remains blank.  
  You MUST set/change it by REST API.  
- TWD: Get list of users/groups  
- TWD: Get user/group by userId/groupId  

## Change password  
REST API  
```PUT http://<host>:<port>/rest/repo/<repositoryId>/user/changePassword```  
FormData  
```
oldPassword: xxxxx
newPassword: yyyyy
```
