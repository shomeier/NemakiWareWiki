You can add easily another database as a background for NemakiWare.

* Replace `jp.aegif.nemaki.service.dao.impl.CouchContentDaoServiceImpl/CouchPrincipalDaoServiceImpl`.  
`ContentDaoServiceImpl/PrincipalDaoServiceImpl` implement the caching mechanism and call `CouchContentDaoServiceImpl/CouchPrincipalDaoServiceImpl` as `nonCachedContentDaoService/nonCachedPrincipalDaoService`.

*  Spring configuration  
_`context.backend` in property files_: Overwrite it by the new Spring context file you defined.  
_Your new Spring context file_: Define the classes as couchContext.xml. 

* Methods in you DAO should return null(or empty list) when they have any error or no result.  
In the higher layer, the result is checked by CollectionUtils.isEmpty.