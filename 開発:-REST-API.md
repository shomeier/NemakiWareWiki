[English](https://github.com/aegif/NemakiWare/wiki/Development%3A-REST-API/_edit)/日本語 
***
# User

# Group

# Archive

# Solr

# AuthToken
## 概要
- ユーザに対して､認証用トークンを登録することができます。
- トークンはUUIDとして生成され、一定期間後に失効します。

## 登録
`http://localhost:8080/core/rest/authtoken/{userName}/register?app={appName}`
- {appName}: 省略可

```json
{
    "status": "success",
    "value": {
        "app": "",
        "expiration": 1433898326668,
        "token": "22d418e3-0f69-4394-a60f-24555b5760f8",
        "userName": "admin"
    }
}
```

## 送信
トークンは以下のHTTPパラメータとして送信されます:  
- `nemaki_auth_token`: 登録されたトークン
- `nemaki_auth_token_app`: {appName}