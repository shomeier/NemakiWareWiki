[English](https://github.com/aegif/NemakiWare/wiki/Configuration%28UI%29:-Property)/日本語
***

# プロパティの変更
上書きしたいプロパティを以下のファイルに追加します:  
`<TOMCAT_PATH>/shared/classes/app-server-ui.properties`

# プロパティの一覧
設定可能なプロパティはすべて[application.conf](https://github.com/aegif/NemakiWare/blob/master/ui/conf/application.conf)に列挙されています。

# とくに重要なプロパティ
上記一覧からいくつかピックアップして説明します:  
- `navigation.paging.size`: フォルダ内一覧画面に表示される行数
- `navigation.column.displayed`: フォルダ内一覧画面にカラムとして表示されるCMISプロパティのID
