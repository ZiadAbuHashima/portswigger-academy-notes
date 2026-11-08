# Lab: JWT authentication bypass via kid header path traversal

**Official URL:** https://portswigger.net/web-security/jwt/lab-jwt-authentication-bypass-via-kid-header-path-traversal

## Lab idea

This challenge uses a `kid` header value to select a verification key from the server's filesystem. The high-level objective is to identify the security risk when a key identifier is treated as an unconstrained path. It practices examining how JWT metadata reaches server-side key lookup logic.

## Vulnerability in brief
JWT is short for **JSON Web Token**. PortSwigger's JWT topic is a vulnerability subject, not a general testing category: it covers weaknesses in how applications create, accept, verify, and select keys for tokens. JWTs commonly carry claims used for authentication, sessions, and access control. A signed JWT generally has a header, payload, and signature, separated by dots. The header and payload are Base64URL-encoded JSON, not encrypted by default, so their contents should not be treated as secret. The signature is intended to let the recipient verify that the token has not been altered.

## Solution idea
1. In Burp, load the JWT Editor extension from the BApp store.
2. In the lab, log in to your own account and send the post-login GET /my-account request to Burp Repeater.
3. In Burp Repeater, change the path to /admin and send the request.
4. Go to the JWT Editor Keys tab in Burp's main tab bar.
- …
6. Make sure that the Don't modify header option is selected, then click OK .
7. Send the request and observe that you have successfully accessed the admin panel.
8. In the response, find the URL for deleting carlos ( /admin/delete?username=carlos ).

## Payloads / key values
- `kid`
- `/dev/null`
- `GET /my-account`
- `/admin`
- `administrator`
- `k`
- `GET /admin`
- `../../../../../../../dev/null`
- `sub`
- `carlos`
- `/admin/delete?username=carlos`

## Official source
- [PortSwigger Academy: Lab: JWT authentication bypass via kid header path traversal](https://portswigger.net/web-security/jwt/lab-jwt-authentication-bypass-via-kid-header-path-traversal)
