[English](https://github.com/aegif/NemakiWare/wiki/Development_-Development-in-Eclipse)/日本語 
***
# プロジェクトのセットアップ
セットアップ後、Eclipseで既存プロジェクトとしてインポートしてください。  
## Core/Solr
```mvn eclipse:eclipse``` をルートフォルダで実行（複数のサブプロジェクトがありますが、すべて実行されます）

### UI
```mvn package; mvn install:install-file -Dfile=nemakiware-common-<Version>.jar -DgroupId=jp.aegif.nemakiware -DartifactId=nemakiware-common -Dversion=<Version> -Dpackaging=jar``` を/commonフォルダで実行し、ローカルリポジトリへインストール

その後 ```activator eclipse``` をプロジェクトフォルダで実行(/ui)

# アプリケーションサーバ
## Core/Solr
標準でJettyにより起動できます。  
```mvn jetty:run```  または  
Eclipse上のプラグインから起動(たとえば[Run Jetty Run](https://code.google.com/p/run-jetty-run/))  

デフォルトではポート8080(core)、ポート8983(solr)で起動します

## UI
```activator run``` (デフォルトではポート9000で起動します)

# デバッグ
##UI
起動時に```activator -jvm-debug 9999 run```  
EclipseのRemote Java Applicationでポート9999に接続