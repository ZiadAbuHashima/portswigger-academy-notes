# Lab: JWT authentication bypass via weak signing key

**Official URL:** https://portswigger.net/web-security/jwt/lab-jwt-authentication-bypass-via-weak-signing-key

## Lab idea

This challenge uses a JWT signing secret that is weak enough to be guessed from common values. Its high-level objective is to understand that signature verification alone is insufficient when the signing key lacks strength. It practices recognizing weak-secret risk and its consequences for the integrity of token claims.

## Vulnerability in brief
JWT is short for **JSON Web Token**. PortSwigger's JWT topic is a vulnerability subject, not a general testing category: it covers weaknesses in how applications create, accept, verify, and select keys for tokens. JWTs commonly carry claims used for authentication, sessions, and access control. A signed JWT generally has a header, payload, and signature, separated by dots. The header and payload are Base64URL-encoded JSON, not encrypted by default, so their contents should not be treated as secret. The signature is intended to let the recipient verify that the token has not been altered.

## Solution idea
1. In Burp, load the JWT Editor extension from the BApp store.
2. In the lab, log in to your own account and send the post-login GET /my-account request to Burp Repeater.
3. In Burp Repeater, change the path to /admin and send the request.
4. Copy the JWT and brute-force the secret.
- …
6. Make sure that the Don't modify header option is selected, then click OK .
7. Send the request and observe that you have successfully accessed the admin panel.
8. In the response, find the URL for deleting carlos ( /admin/delete?username=carlos ).

## Payloads / key values
- `GET /my-account`
- `/admin`
- `administrator`
- `hashcat -a 0 -m 16500 <YOUR-JWT> /path/to/jwt.secrets.list`
- `secret1`
- `--show`
- `k`
- `GET /admin`
- `sub`
- `Sign`
- `Don't modify header`
- `OK`
- `carlos`
- `/admin/delete?username=carlos`

## Official source
- [PortSwigger Academy: Lab: JWT authentication bypass via weak signing key](https://portswigger.net/web-security/jwt/lab-jwt-authentication-bypass-via-weak-signing-key)
