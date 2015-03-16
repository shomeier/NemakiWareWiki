
CMIS API を PHP から利用するには [Apache Chemistry の PHP クライアントの例](http://chemistry.apache.org/php/phpclient.html) が参考になります。サンプルのソースをSubversionでチェックアウトし、examples以下のサンプルを動かすと、CMIS APIを叩くことができます。

コードを動かす前にパスを通す必要があります。引数でパスを渡すか、php.ini をひらいて、

```PHP
include_path=".;C:\xampp\php\PEAR;
```

にパスを書くと動きます。

```PHP
C:\phpclient\trunk\atom;C:\phpclient\trunk\atom\cmis
```

例では

php -f cmis_ls.php <rest-endpoint> <username> <password> <folderpath> [debug option 1](2.html)

とありますが、この cmis_ls.php サンプルソースコードにはバグがあり、require_once で cmis_service を読みこむ必要があります。

```php
require_once ('cmis_service.php');
```
