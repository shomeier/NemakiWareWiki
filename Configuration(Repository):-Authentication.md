[English](https://github.com/aegif/NemakiWare/wiki/%E7%92%B0%E5%A2%83%E8%A8%AD%E5%AE%9A%28%E3%83%AA%E3%83%9D%E3%82%B8%E3%83%88%E3%83%AA%29:-%E8%AA%8D%E8%A8%BC)/日本語 
***
# Available authentication
## Basic authentication
- Sends username/password on the HTTP header.
- This is the default authentication method in NemakiWare.

## Simplified token authentication
- Sends a token as a parameter on the HTTP header.
- Token is published by the REST API based on the basic authentication.
- This will do good for performance since decoding a password each time takes some time.

### How to get a token
[See this link](https://github.com/aegif/NemakiWare/wiki/Development:-REST-API#authtoken)

