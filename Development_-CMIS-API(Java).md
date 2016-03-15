English/[日本語](https://github.com/aegif/NemakiWare/wiki/%E9%96%8B%E7%99%BA:-CMIS-API%28Java%29)
***
# Introduction
- First, you have to create CMIS session and connect it to your CMIS repository server.
- Then you invoke a method of the session to execute an operation.
- Alternatively, most of operations can be executed by calling a retrieved CmisObject(like Folder or Document)'s method.

# Library
The standarad library for development of CMIS client is provided as open source software.  
Import [Apache Chemistry](http://chemistry.apache.org/)'s [OpenCMIS](http://chemistry.apache.org/java/opencmis.html) library to your project (by maven, for example).    
The following packages are required usually to develop a CMIS client:
chemistry-opencmis-commons-api  
chemistry-opencmis-commons-impl  
chemistry-opencmis-client-api  
chemistry-opencmis-client-impl  
chemistry-opencmis-client-bindings   

# Code sample
## Create CMIS session
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

## Create a folder
```java
HashMap<String, Object> param = new HashMap<String, Object>();
param.put(PropertyIds.OBJECT_TYPE_ID, "cmis:folder");
param.put(PropertyIds.NAME, "folder name");
ObjectId objectId = session.createFolder(param, parentId); //Returns object id of the created object
```

## Create a document
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

## Create a relationship
```java
HashMap<String, Object> param = new HashMap<String, Object>();
param.put(PropertyIds.NAME, "relationship name");
param.put(PropertyIds.SOURCE_ID, sourceObjectId);
param.put(PropertyIds.TARGET_ID, sourceObjectId);

ObjectId objectId = session.createRelationship(properties);
```

## Get an object(specifying its ID)
```java
CmisObject object = session.getObject(id);
```

## Get the versions of a document
```java
CmisObject object = session.getObject(id);
List<Document> versions = ((Document)object).getAllVersions();
```

## Download a file
```java
CmisObject object = session.getObject(id);
Document document = (Document) object;
ContentStream contentStream = doc.getContentStream();

//Convert content stream to input stream or file
InputStream inputStream = contentStream.getStream();
File file = File.createTempFile(contentStream.getFileName(), "");
```

## Update properties(update directly without checking out)
```java
CmisObject object = session.getObject(id);

//Build property values (no need for the properties not to be updated)
Map<String, Object> properties = new HashMap<String, Object>();
properties.put(PropertyIds.NAME, "new name");

object.updateProperties(properties);
```

## Update file(update directly without checking out)
```java
CmisObject object = session.getObject(id);
Document doc = (Document) object;

ContentStream contentStream = ... //Get content stream from somewhere

doc.setContentStream(contentStream, true);
```

## Check out & Check in
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

## Cancel check out
```java
CmisObject object = session.getObject(id);
Document document = (Document) object;

document.cancelCheckOut();
```

## Delete an object
```java
CmisObject object = session.getObject(id);
object.delete();
```
or
```java
CmisObject object = session.getObject(id);
session.delete(new ObjectIdImpl(id));
```

## Delete a folder when it has children or descendants
```java
CmisObject object = session.getObject(id);
Folder folder = (Folder)object;
folder.deleteTree(true, null, true);
```

## Search
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

The statement is described following CMIS Query syntax.  
For CMIS Query syntax, see [this link](https://github.com/aegif/NemakiWare/wiki/CMIS-Query-%E3%81%AE%E5%88%A9%E7%94%A8).  