English/日本語
***
# 概要
- ドキュメントやフォルダを検索するには、CMIS Queryという記法でクエリ文を書いてメソッドに渡します。
- CMIS QueryはSQL-92をベースにしたもので、CMIS独自の拡張や制約があります。
- 使える記法には、SELECT、FROM、WHERE、ORDER BYなどがあります。
- JOIN、GROUP BY、HAVINGなどは使えません。

クエリを自分で書いて挙動を試してみたければ、[CMIS Workbench](https://github.com/aegif/NemakiWare/wiki/CMIS-Workbench(Simple-client))を利用すると簡単です。CMIS Workbench の Query タブからクエリを実行することが出来ます。

# サンプル
以下に簡単なサンプルを示します。

すべてのドキュメントを取得します。
```SQL
SELECT * FROM cmis:document
```

すべてのフォルダを取得します。
```SQL
SELECT * FROM cmis:folder
```

特定のプロパティのみを取得します。
```SQL
SELECT cmis:name, cmis:objectId FROM cmis:document
```

エイリアスも使えます。
```SQL
SELECT
   F.cmis:name AS name
 , F.cmis:objectId AS id
FROM 
  cmis:folder AS F
```

WHERE句を使った例
```SQL
SELECT * FROM cmis:document WHERE cmis:objectId = 'f4970bc7faffc7295d44b25fb105ca88'
SELECT * FROM cmis:document WHERE cmis:name LIKE  '%サンプル%'
SELECT * FROM cmis:document WHERE cmis:description IS NULL
SELECT * FROM cmis:document WHERE cmis:versionLabel IN ('1.1', '2.0')
```

特殊な構文として WHERE 句の中で IN_FOLDER と IN_TREE が使えます。
WHERE句で IN_FOLDER('folderのobjectId') を使うと、指定したフォルダ内を検索します。

```SQL
SELECT * FROM cmis:document WHERE IN_FOLDER('b11bf1bf25317a8fa2941b8f140148b6')
```

WHERE句で IN_TREE('folderのobjectId') を使うと、指定したフォルダ以下を再帰的に検索します。
```SQL
SELECT * FROM cmis:document WHERE IN_TREE('b11bf1bf25317a8fa2941b8f140148b6') 
```

ORDER BY による並べ替えは使用できます。GROUP BY や HAVING は使用できません。以下は、登録日順にソートして、ドキュメントをすべて取得します。
```SQL
SELECT * FROM cmis:document  ORDER BY cmis:creationDate
```
