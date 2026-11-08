# Lab: JWT authentication bypass via flawed signature verification

**Official URL:** https://portswigger.net/web-security/jwt/lab-jwt-authentication-bypass-via-flawed-signature-verification

## Lab idea

The lab focuses on a JWT-based session mechanism that accepts unsigned tokens because of flawed signature handling. Its objective is to recognize how that verification failure can let token claims influence access control. It practices examining JWT headers, claims, and the integrity assumptions made by an application.

## Vulnerability in brief
JWT is short for **JSON Web Token**. PortSwigger's JWT topic is a vulnerability subject, not a general testing category: it covers weaknesses in how applications create, accept, verify, and select keys for tokens. JWTs commonly carry claims used for authentication, sessions, and access control. A signed JWT generally has a header, payload, and signature, separated by dots. The header and payload are Base64URL-encoded JSON, not encrypted by default, so their contents should not be treated as secret. The signature is intended to let the recipient verify that the token has not been altered.

## Solution idea
1. In the lab, log in to your own account.
2. In Burp, go to the Proxy > HTTP history tab and look at the post-login GET /my-account request.
3. Double-click the payload part of the token to view its decoded JSON form in the Inspector panel.
4. In Burp Repeater, change the path to /admin and send the request.
- …
6. In the message editor, remove the signature from the JWT, but remember to leave the trailing dot after the payload.
7. Send the request and observe that you have successfully accessed the admin panel.
8. In the response, find the URL for deleting carlos ( /admin/delete?username=carlos ).

## Payloads / key values
- `GET /my-account`
- `sub`
- `/admin`
- `administrator`
- `alg`
- `none`
- `carlos`
- `/admin/delete?username=carlos`

## Official source
- [PortSwigger Academy: Lab: JWT authentication bypass via flawed signature verification](https://portswigger.net/web-security/jwt/lab-jwt-authentication-bypass-via-flawed-signature-verification)
