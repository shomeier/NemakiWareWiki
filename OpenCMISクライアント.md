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