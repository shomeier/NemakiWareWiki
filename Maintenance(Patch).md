# Patch system
From ver.2.4, patch system is adopted to upgrade the database automatically.  
Patches are executed on starting the application, to be more precisely at the last position of Spring context xml files.   

A patch is _idempotent_, i.e. it is applied once and for all.  

**FOR DEVELOPER:**  
Once a patch is applied, its history is logged in the database not to be executed once more.  
However, you should write patch codes _idempotent_ in itself.  
For example, if you want to create a system folder in the root, you should check previously whether the target folder already exists, and if it is found, skip the action.  

## ver.2.4
- Add patch view
- Add system folder
- Add user/group item views
- Convert existing user/group to cmis:item