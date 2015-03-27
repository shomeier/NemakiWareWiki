---

## プロパティ設定のアーキテクチャ
* CMISサーバはSpring frameworkを利用しており、プロパティへのアクセスはすべてSpringのpropertyConfiguratorに集約されています。
* プロパティファイルの値は上書きが可能です。複数のプロパティファイルがありますが、以下の順序で上書きされます(下に行くほど、後から上書きされるので、優先されます)。  
具体的には次で定義されています: `<SOURCE_PATH>/nemakiware/src/main/webapp/WEB-INF/classes/propertyContextxml`

  1. `<SOURCE_PATH>/nemakiware/src/main/webapp/WEB-INF/classes/nemakiware.properties`
  2. `<SOURCE_PATH>/nemakiware/src/main/resources/custom-nemakiware.properties`  
(以下はNemakiWareがTomcat環境で動作している場合:)
  3. `<INSTALL_PATH>/apache-tomcat-7.x.xx/shared/classes/app-server-couchdb.properties`
  4. `<INSTALL_PATH>/apache-tomcat-7.x.xx/shared/classes/app-server-solr.properties`
  5. `<INSTALL_PATH>/apache-tomcat-7.x.xx/shared/classes/app-server-general.properties`  
  

* 開発者にとっては、`custom-nemakiware.properties`がもっとも重要です。このプロパティファイルはwarの中に含まれます。
* サーバ管理者にとっては、`app-server-xxx.properties`がもっとも重要です。インストーラでの設定値もここに反映されます。またapp-server-general.propertiesでは、どんなプロパティでも上書きできます。