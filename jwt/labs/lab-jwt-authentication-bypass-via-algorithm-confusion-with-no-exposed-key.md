# Lab: JWT authentication bypass via algorithm confusion with no exposed key

**Official URL:** https://portswigger.net/web-security/jwt/algorithm-confusion/lab-jwt-authentication-bypass-via-algorithm-confusion-with-no-exposed-key

## Lab idea

This challenge adds a key-discovery dimension to algorithm confusion: the server's RSA public key is not directly exposed. The high-level objective is to reason about deriving or identifying the public verification key from server-issued tokens, then assess the risk of an unsafe algorithm switch. It practices JWT analysis when key material is not published through an obvious endpoint.

## Vulnerability in brief
JWT is short for **JSON Web Token**. PortSwigger's JWT topic is a vulnerability subject, not a general testing category: it covers weaknesses in how applications create, accept, verify, and select keys for tokens. JWTs commonly carry claims used for authentication, sessions, and access control. A signed JWT generally has a header, payload, and signature, separated by dots. The header and payload are Base64URL-encoded JSON, not encrypted by default, so their contents should not be treated as secret. The signature is intended to let the recipient verify that the token has not been altered.

## Solution idea
1. In Burp, load the JWT Editor extension from the BApp store.
2. In the lab, log in to your own account and send the post-login GET /my-account request to Burp Repeater.
3. In Burp Repeater, change the path to /admin and send the request.
4. Copy your JWT session cookie and save it somewhere for later.
- …
6. Make sure that the Don't modify header option is selected, then click OK .
7. Send the request and observe that you have successfully accessed the admin panel.
8. In the response, find the URL for deleting carlos ( /admin/delete?username=carlos ).

## Payloads / key values
- `GET /my-account`
- `/admin`
- `administrator`
- `docker run --rm -it portswigger/sig2n <token1> <token2>`
- `n`
- `/my-account`
- `/login`
- `k`
- `alg`
- `HS256`
- `sub`
- `carlos`
- `/admin/delete?username=carlos`

## Official source
- [PortSwigger Academy: Lab: JWT authentication bypass via algorithm confusion with no exposed key](https://portswigger.net/web-security/jwt/algorithm-confusion/lab-jwt-authentication-bypass-via-algorithm-confusion-with-no-exposed-key)
