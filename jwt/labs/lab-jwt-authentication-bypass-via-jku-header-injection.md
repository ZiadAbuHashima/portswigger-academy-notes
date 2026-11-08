# Lab: JWT authentication bypass via jku header injection

**Official URL:** https://portswigger.net/web-security/jwt/lab-jwt-authentication-bypass-via-jku-header-injection

## Lab idea

This challenge concerns a verifier that follows a `jku` header URL without restricting it to a trusted domain. Its high-level objective is to understand how untrusted remote key selection can weaken JWT signature validation. It practices assessing trust boundaries around externally fetched JWK Sets.

## Vulnerability in brief
JWT is short for **JSON Web Token**. PortSwigger's JWT topic is a vulnerability subject, not a general testing category: it covers weaknesses in how applications create, accept, verify, and select keys for tokens. JWTs commonly carry claims used for authentication, sessions, and access control. A signed JWT generally has a header, payload, and signature, separated by dots. The header and payload are Base64URL-encoded JSON, not encrypted by default, so their contents should not be treated as secret. The signature is intended to let the recipient verify that the token has not been altered.

## Solution idea
1. In Burp, load the JWT Editor extension from the BApp store.
2. In the lab, log in to your own account and send the post-login GET /my-account request to Burp Repeater.
3. In Burp Repeater, change the path to /admin and send the request.
4. Go to the JWT Editor Keys tab in Burp's main tab bar.
- …
6. Make sure that the Don't modify header option is selected, then click OK .
7. Send the request.
8. In the response, find the URL for deleting carlos ( /admin/delete?username=carlos ).

## Payloads / key values
- `GET /my-account`
- `/admin`
- `administrator`
- `{ "keys": [ ] }`
- `keys`
- `{ "keys": [ { "kty": "RSA", "e": "AQAB", "kid": "893d8f0b-061f-42c2-a4aa-5056e12b8ae7", "n": "yy1wpYmffgXBxhAUJzHHocCuJolwDqql75ZWuCQ_cb33K2vh9mk6GPM9gNN4Y_qTVX67WhsN3JvaFYw" } ] }`
- `GET /admin`
- `kid`
- `jku`
- `sub`
- `carlos`
- `/admin/delete?username=carlos`

## Official source
- [PortSwigger Academy: Lab: JWT authentication bypass via jku header injection](https://portswigger.net/web-security/jwt/lab-jwt-authentication-bypass-via-jku-header-injection)
