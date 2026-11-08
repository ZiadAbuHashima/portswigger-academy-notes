# Lab: Forced OAuth profile linking

**Official PortSwigger URL:** https://portswigger.net/web-security/oauth/lab-oauth-forced-oauth-profile-linking

**Lab idea:** This challenge concerns an insecure OAuth account-linking flow that can be manipulated to attach an attacker's social profile to another user's application account. It practices assessing CSRF protections and the security of identity-linking actions.

## Vulnerability in brief
OAuth is a framework for delegated access; applications also use OAuth flows to sign users in through an identity held by another service. This Academy section is a **vulnerability topic**, not a general learning or testing category. It focuses on security failures in OAuth-based authentication and related OpenID Connect implementations.

## Solution idea
1. While proxying traffic through Burp, click "My account".
2. Notice that you have the option to attach your social media profile to your existing account.
3. Click "Attach a social profile".
4. Log out and then click "My account" to go back to the login page.
- …
6. Go to the exploit server and create an iframe in which the src attribute points to the URL you just copied.
7. Deliver the exploit to the victim.
8. Go back to the blog website and select the "Log in with social media" option again.

## Payloads / key values
- `GET /auth?client_id[...]`
- `redirect_uri`
- `/oauth-linking`
- `state`
- `GET /oauth-linking?code=[...]`
- `iframe`
- `src`
- `<iframe src="https://YOUR-LAB-ID.web-security-academy.net/oauth-linking?code=STOLEN-CODE"></iframe>`
- `carlos`

## Official source
- [PortSwigger Academy: Lab: Forced OAuth profile linking](https://portswigger.net/web-security/oauth/lab-oauth-forced-oauth-profile-linking)
