English/日本語 
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

