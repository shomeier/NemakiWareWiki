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
parameter.put(SessionParameter.LOCALE_ISO3166_COUNTRY, country);
parameter.put(SessionParameter.LOCALE_ISO639_LANGUAGE, language);

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

* リレーションの作成
```java
HashMap<String, Object> param = new HashMap<String, Object>();
param.put(PropertyIds.NAME, "relationship name");
param.put(PropertyIds.SOURCE_ID, sourceObjectId);
param.put(PropertyIds.TARGET_ID, sourceObjectId);

ObjectId objectId = session.createRelationship(properties);
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

* ファイルのダウンロード
```java
CmisObject object = session.getObject(id);
Document document = (Document) object;
ContentStream contentStream = doc.getContentStream();

//Convert content stream to input stream or file
InputStream inputStream = contentStream.getStream();
File file = File.createTempFile(contentStream.getFileName(), "");
```

* 属性の更新(チェックアウトなし・直接更新)
```java
CmisObject object = session.getObject(id);

//Build property values (no need for the properties not to be updated)
Map<String, Object> properties = new HashMap<String, Object>();
properties.put(PropertyIds.NAME, "new name");

object.updateProperties(properties);
```

* ファイルの更新(チェックアウトなし・直接更新)
```java
CmisObject object = session.getObject(id);
Document document = (Document) object;

ContentStream contentStream = ... //Get content stream from somewhere

doc.setContentStream(contentStream, true);
```

* チェックアウト・チェックイン
```java
CmisObject object = session.getObject(id);
Document document = (Document) object;

//Check out
if (doc.isVersionSeriesCheckedOut()) {
   // You cannot checked out a document twice!
}

//Check out action makes a private working copy as an independent object
ObjectId pwcId = doc.checkOut(); //Returns private working copy id

//Some udpate to the private working copy (pwc)
CmisObject pwc = session.getObject(pwcId.getId());
pwc.setContentStream(contentStream, true);
pwc.updateProperties(properties);
...

//Check in
//the first argument "true" means major version update
ObjectId newDocId = pwc.checkIn(true, properties, contentStream, "Check in comment");
```

* オブジェクトの削除
```java
CmisObject object = session.getObject(id);
object.delete();
```
or
```java
CmisObject object = session.getObject(id);
session.delete(new ObjectIdImpl(id));
```

* フォルダ(子要素が存在する場合)の削除
```java
CmisObject object = session.getObject(id);
Folder folder = (Folder)object;
folder.deleteTree(true, null, true);
```

* 検索
```java
//Build query statement
MessageFormat format = new MessageFormat("cmis:name LIKE ''%{0}%'' OR CONTAINS(''{0}'')");
String statement = "";
if (StringUtils.isNotBlank(term)) {
   statement = format.format(new String[] { term });
}

//Execute query
ItemIterable<CmisObject> results = session.queryObjects("cmis:document", statement, false, session.getDefaultContext());
Iterator<CmisObject> itr = docResults.iterator();
List<CmisObject> list = new ArrayList<CmisObject>();
while (itr.hasNext()) {
   list.add(itr.next());
}
```