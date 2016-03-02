NemakiWare のバックエンド DB を別のものに差し替えるには以下の開発が必要となります。

* DaoServiceImpl の変更

`jp.aegif.nemaki.service.dao.impl.CouchContentDaoServiceImpl/CouchPrincipalDaoServiceImpl` を  `ContentDaoService/PrincipalDaoService` インターフェースを実装した別のクラスに差し替えします。
  
`ContentDaoServiceImpl/PrincipalDaoServiceImpl` はキャッシュのメカニズムを供えており、差し替えてもそのままキャッシュを使うことが出来ます。

*  Spring 設定

_`context.backend` in property files_: Overwrite it by the new Spring context file you defined.  
_Your new Spring context file_: Define the classes as couchContext.xml. 

* Methods in you DAO should return null(or empty list) when they have any error or no result.  
In the higher layer, the result is checked by CollectionUtils.isEmpty.