# Lab: JWT authentication bypass via jwk header injection

**Official URL:** https://portswigger.net/web-security/jwt/lab-jwt-authentication-bypass-via-jwk-header-injection

## Lab idea

The lab examines a verifier that accepts a public key embedded in the JWT's `jwk` header without establishing that the key is trusted. Its objective is to recognize how token-controlled verification keys can enable authentication bypass. It practices reviewing key provenance and signature-validation policy.

## Vulnerability in brief
JWT is short for **JSON Web Token**. PortSwigger's JWT topic is a vulnerability subject, not a general testing category: it covers weaknesses in how applications create, accept, verify, and select keys for tokens. JWTs commonly carry claims used for authentication, sessions, and access control. A signed JWT generally has a header, payload, and signature, separated by dots. The header and payload are Base64URL-encoded JSON, not encrypted by default, so their contents should not be treated as secret. The signature is intended to let the recipient verify that the token has not been altered.

## Solution idea
1. In Burp, load the JWT Editor extension from the BApp store.
2. In the lab, log in to your own account and send the post-login GET /my-account request to Burp Repeater.
3. In Burp Repeater, change the path to /admin and send the request.
4. Go to the JWT Editor Keys tab in Burp's main tab bar.
- …
6. In the header of the JWT, observe that a jwk parameter has been added containing your public key.
7. Send the request.
8. In the response, find the URL for deleting carlos ( /admin/delete?username=carlos ).

## Payloads / key values
- `GET /my-account`
- `/admin`
- `administrator`
- `GET /admin`
- `JSON Web Token`
- `sub`
- `jwk`
- `carlos`
- `/admin/delete?username=carlos`
- `kid`

## Official source
- [PortSwigger Academy: Lab: JWT authentication bypass via jwk header injection](https://portswigger.net/web-security/jwt/lab-jwt-authentication-bypass-via-jwk-header-injection)
