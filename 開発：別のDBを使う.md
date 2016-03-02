NemakiWare のバックエンド DB を別のものに差し替えるには以下の開発が必要となります。

* DaoServiceImpl の変更

`jp.aegif.nemaki.service.dao.impl.CouchContentDaoServiceImpl/CouchPrincipalDaoServiceImpl` を  `ContentDaoService/PrincipalDaoService` インターフェースを実装した別のクラスに差し替えします。
  
`ContentDaoServiceImpl/PrincipalDaoServiceImpl` はキャッシュのメカニズムを供えており、差し替えてもそのままキャッシュを使うことが出来ます。

*  Spring 設定

_`context.backend` in property files_: Overwrite it by the new Spring context file you defined.  
_Your new Spring context file_: Define the classes as couchContext.xml. 

* 注意
エラーもしくは結果がない場合、 DAO の戻り値は null か空の配列にしてください。上位レイヤーにおいて CollectionUtils.isEmpty メソッドにより結果がチェックされます。 