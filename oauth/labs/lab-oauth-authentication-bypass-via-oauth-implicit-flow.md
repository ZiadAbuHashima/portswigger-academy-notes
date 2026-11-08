# Lab: Authentication bypass via OAuth implicit flow

**Official PortSwigger URL:** https://portswigger.net/web-security/oauth/lab-oauth-authentication-bypass-via-oauth-implicit-flow

**Lab idea:** The client application mishandles validation in an OAuth implicit-flow sign-in, creating a path to impersonate another account without that user's password. The challenge practices examining how a client consumes identity information and access tokens returned through the browser.

## Vulnerability in brief
OAuth is a framework for delegated access; applications also use OAuth flows to sign users in through an identity held by another service. This Academy section is a **vulnerability topic**, not a general learning or testing category. It focuses on security failures in OAuth-based authentication and related OpenID Connect implementations.

## Solution idea
1. While proxying traffic through Burp, click "My account" and complete the OAuth login process.
2. In Burp, go to "Proxy" > "HTTP history" and study the requests and responses that make up the OAuth flow.
3. Notice that the client application (the blog website) receives some basic information about the user from the OAuth service.
4. Send the POST /authenticate request to Burp Repeater.
5. Right-click on the POST request and select "Request in browser" > "In original session".

## Payloads / key values
- `GET /auth?client_id=[...]`
- `POST`
- `/authenticate`
- `POST /authenticate`
- `carlos@carlos-montoya.net`

## Official source
- [PortSwigger Academy: Lab: Authentication bypass via OAuth implicit flow](https://portswigger.net/web-security/oauth/lab-oauth-authentication-bypass-via-oauth-implicit-flow)
