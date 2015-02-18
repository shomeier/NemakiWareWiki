---
## RepositoryInfo

## Capability

## ObjectType

## Permission
権限の種類の定義(デフォルト)は以下のファイルに定義されています。
* `<SOURCE_PATH>/nemakiware/src/main/webapp/WEB-INF/classes/permission.yml`  
権限とアクションの対応関係(デフォルト)は以下のファイルに定義されています。
* `<SOURCE_PATH>/nemakiware/src/main/webapp/WEB-INF/classes/permission-mapping.yml`  
See [Spec 2.1.12.3.2](http://docs.oasis-open.org/cmis/CMIS/v1.1/os/CMIS-v1.1-os.html#x1-7700012)

### 権限設定を変更するには?
* permission.yml  
プロパティの`permission.definition`キーで指定されています。
* permission-mapping.yml  
プロパティの`permission.mapping.definition`キーで指定されています。

権限を変更するには、新しい権限設定ファイルを作成し、**TODO プロパティ設定**にしたがって上記のキーを上書きします。