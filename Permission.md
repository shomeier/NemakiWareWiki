English/[日本語](https://github.com/aegif/NemakiWare/wiki/%E7%92%B0%E5%A2%83%E8%A8%AD%E5%AE%9A%28%E3%83%AA%E3%83%9D%E3%82%B8%E3%83%88%E3%83%AA%29:-%E6%A8%A9%E9%99%90) 
***
# How it works
## Principal(user/group) -> Permission -> Action
- Each node(document/folder) has its ACL(Access Control List).
- ACE(Access Control Entity) maps a principal to some permissions.
- A permission is mapped to some CMIS action by the repository configuration.
- If a user is mapped to an action eventually, the action is allowed for the user.

## Inheritance from the parent folder
- A new node inherits its parent's ACL by default.  
- You can change the ACL if you have the appropriate permission to do so.  
- Inherited each ACE can be overwritten , not necessarily switching off the whole ACL.  

## Inheritance from the group
- User or group can belong to groups.
- If an ACE maps the group to some permissions, it members are also mapped to them.

# Configure permissions
## ACL(principal & permission)
UI: Detail > Permission tab  

## List of permissions
[See](https://github.com/aegif/NemakiWare/wiki/Configuration%28Repository%29:-Property#permission)  

## Mapping of permissions and actions
[See](https://github.com/aegif/NemakiWare/wiki/Configuration%28Repository%29:-Property#permission)