# Lab: JWT authentication bypass via algorithm confusion

**Official URL:** https://portswigger.net/web-security/jwt/algorithm-confusion/lab-jwt-authentication-bypass-via-algorithm-confusion

## Lab idea

The challenge explores algorithm confusion in a JWT verifier that uses an RSA key pair. Its high-level objective is to understand how inconsistent algorithm handling can undermine trust in token signatures and enable an authorization bypass. It practices recognizing the boundary between asymmetric and symmetric key use in JWT verification.

## Vulnerability in brief
JWT is short for **JSON Web Token**. PortSwigger's JWT topic is a vulnerability subject, not a general testing category: it covers weaknesses in how applications create, accept, verify, and select keys for tokens. JWTs commonly carry claims used for authentication, sessions, and access control. A signed JWT generally has a header, payload, and signature, separated by dots. The header and payload are Base64URL-encoded JSON, not encrypted by default, so their contents should not be treated as secret. The signature is intended to let the recipient verify that the token has not been altered.

## Solution idea
1. In Burp, load the JWT Editor extension from the BApp store.
2. In the lab, log in to your own account and send the post-login GET /my-account request to Burp Repeater.
3. In Burp Repeater, change the path to /admin and send the request.
4. In the browser, go to the standard endpoint /jwks.json and observe that the server exposes a JWK Set containing a single public key.
- …
6. Make sure that the Don't modify header option is selected, then click OK .
7. Send the request and observe that you have successfully accessed the admin panel.
8. In the response, find the URL for deleting carlos ( /admin/delete?username=carlos ).

## Payloads / key values
- `GET /my-account`
- `/admin`
- `administrator`
- `/jwks.json`
- `keys`
- `GET /admin`
- `alg`
- `HS256`
- `sub`
- `carlos`
- `/admin/delete?username=carlos`

## Official source
- [PortSwigger Academy: Lab: JWT authentication bypass via algorithm confusion](https://portswigger.net/web-security/jwt/algorithm-confusion/lab-jwt-authentication-bypass-via-algorithm-confusion)
