English/[日本語](https://github.com/aegif/NemakiWare/wiki/%E9%96%8B%E7%99%BA:-CMIS-API%28PHP%29)
***
# Introduction
To use CMIS API from PHP, [Apache Chemistry's PHP client example](http://chemistry.apache.org/php/phpclient.html) is useful. Checking out the sample source code from the Subversion repository, you can call CMIS API in the exmaples.  

# Preparation
Before running the codes, you should add the following path to PATH by passing it as an argument
```PHP
C:\phpclient\trunk\atom;C:\phpclient\trunk\atom\cmis
```
or adding it to the include_path in php.ini:
```PHP
include_path=".;C:\xampp\php\PEAR;
```

## BugIn the examples, it is written:
```
php -f cmis_ls.php <rest-endpoint> <username> <password> <folderpath> [debug option 1](2.html)
```

However this `cmis_ls.php` sample source code has a bug, you should read cmis_service by require_once.
```php
require_once ('cmis_service.php');
```