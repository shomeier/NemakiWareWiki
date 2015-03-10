* 概要<br>
CMISセッションを作成してCMISサーバに接続し、セッションの持つCMISメソッドを呼び出して操作します。<br>
取得したCmisObject(フォルダやドキュメント)に対して同様のメソッドを呼び出すこともできます。<br>

* ライブラリ<br>
CMISクライアントを開発するための標準的なライブラリがオープンソースで用意されています。<br>
[Apache Chemistry](http://chemistry.apache.org/)の[OpenCMIS](http://chemistry.apache.org/java/opencmis.html)ライブラリを(mavenなどで)自分のプロジェクトにインポートします。<br>
通常、CMISクライアントを開発するためには、以下のパッケージをインポートする必要があるでしょう:<br>
chemistry-opencmis-commons-api  
chemistry-opencmis-commons-impl  
chemistry-opencmis-client-api  
chemistry-opencmis-client-impl  
chemistry-opencmis-client-bindings   

* CMISセッションの生成
```java
import org.apache.chemistry.opencmis.client.api.OperationContext;
import org.apache.chemistry.opencmis.client.api.Session;
import org.apache.chemistry.opencmis.client.api.SessionFactory;
import org.apache.chemistry.opencmis.client.runtime.SessionFactoryImpl;
import org.apache.chemistry.opencmis.commons.SessionParameter;

Map<String, String> parameter = new HashMap<String, String>();

// user credentials
parameter.put(SessionParameter.USER, id);
parameter.put(SessionParameter.PASSWORD, password);

// session locale
parameter.put(SessionParameter.LOCALE_ISO3166_COUNTRY, "");
parameter.put(SessionParameter.LOCALE_ISO639_LANGUAGE, "");

// repository url
parameter.put(SessionParameter.BINDING_TYPE, BindingType.ATOMPUB.value());
parameter.put(SessionParameter.ATOMPUB_URL, "http://localhost:8080/core/atom/");
parameter.put(SessionParameter.REPOSITORY_ID, "bedroom");

// create session
SessionFactory f = SessionFactoryImpl.newInstance();
Session session = f.createSession(parameter);
OperationContext operationContext = session.createOperationContext(null,
		true, true, false, IncludeRelationships.BOTH, null, false, null, true, 100);
session.setDefaultContext(operationContext);
```

* フォルダの作成
```java
HashMap<String, Object> param = new HashMap<String, Object>();
param.put(PropertyIds.OBJECT_TYPE_ID, "cmis:folder");
param.put(PropertyIds.NAME, "folder name");
ObjectId objectId = session.createFolder(param, parentId); //Returns object id of the created object
```

* ドキュメントの作成
```java
import org.apache.chemistry.opencmis.commons.data.ContentStream
HashMap<String, Object> param = new HashMap<String, Object>();
param.put(PropertyIds.OBJECT_TYPE_ID, "cmis:document");
param.put(PropertyIds.NAME, "document name");

//Get content stream(file content) from somewhere
ContentStream contentStream;
session.getObjectFactory().createContentStream(filename, length, mimetype, fileInputStream);

ObjectId objectId = session.createDocument(param, parentId, contentStream, VersioningState.MAJOR);
```

* オブジェクトの取得(ID指定)
```java
CmisObject object = session.getObject(id);
```

* ドキュメントのバージョン一覧の取得
```java
CmisObject object = session.getObject(id);
List<Document> versions = ((Document)object).getAllVersions();
```

* 属性の更新
```java
CmisObject object = session.getObject(id);

//Build property values (no need for the properties not to be updated)
Map<String, Object> properties = new HashMap<String, Object>();
properties.put(PropertyIds.NAME, "new name");

object.updateProperties(properties);
```