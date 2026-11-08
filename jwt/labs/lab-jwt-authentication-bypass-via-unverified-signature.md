# Lab: JWT authentication bypass via unverified signature

**Official URL:** https://portswigger.net/web-security/jwt/lab-jwt-authentication-bypass-via-unverified-signature

## Lab idea

The lab's session mechanism does not verify signatures on received JWTs. Its high-level objective is to see how changing untrusted identity claims can bypass authentication or authorization when integrity checks are absent. It practices identifying the distinction between merely decoding a token and securely verifying it.

## Vulnerability in brief
JWT is short for **JSON Web Token**. PortSwigger's JWT topic is a vulnerability subject, not a general testing category: it covers weaknesses in how applications create, accept, verify, and select keys for tokens. JWTs commonly carry claims used for authentication, sessions, and access control. A signed JWT generally has a header, payload, and signature, separated by dots. The header and payload are Base64URL-encoded JSON, not encrypted by default, so their contents should not be treated as secret. The signature is intended to let the recipient verify that the token has not been altered.

## Solution idea
1. In the lab, log in to your own account.
2. In Burp, go to the Proxy > HTTP history tab and look at the post-login GET /my-account request.
3. Double-click the payload part of the token to view its decoded JSON form in the Inspector panel.
4. In Burp Repeater, change the path to /admin and send the request.
5. Select the payload of the JWT again.
6. Send the request again.
7. In the response, find the URL for deleting carlos ( /admin/delete?username=carlos ).

## Payloads / key values
- `GET /my-account`
- `sub`
- `/admin`
- `administrator`
- `wiener`
- `carlos`
- `/admin/delete?username=carlos`

## Official source
- [PortSwigger Academy: Lab: JWT authentication bypass via unverified signature](https://portswigger.net/web-security/jwt/lab-jwt-authentication-bypass-via-unverified-signature)
