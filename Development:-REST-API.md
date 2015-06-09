# User

# Group

# Archive

# Solr

# AuthToken
## Introduction
- You can request registering an authentication token for a user.
- A token is generated as UUID and expires at some point.

##Register
`http://localhost:8080/core/rest/authtoken/{userName}/register?app={appName}`
- {appName}: optional

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