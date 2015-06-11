English/日本語 
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

## Inheritance from the user group
- User or group can belong to a group.
- If an ACE maps the group to some permissions, it members are also mapped to them.

# Configure permissions
## ACL(principal & permission)
UI: Detail > Permission tab  

## List of permissions
[See](https://github.com/aegif/NemakiWare/wiki/Configuration%28Repository%29:-Property#permission)  

## Mapping of permissions and actions
[See](https://github.com/aegif/NemakiWare/wiki/Configuration%28Repository%29:-Property#permission)