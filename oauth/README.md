# OAuth 2.0 Authentication

OAuth is a framework for delegated access; applications also use OAuth flows to sign users in through an identity held by another service. This Academy section is a **vulnerability topic**, not a general learning or testing category. It focuses on security failures in OAuth-based authentication and related OpenID Connect implementations. [1]

## Main concepts

An OAuth flow connects a client application, a user (resource owner), and an OAuth provider. The client requests scoped access, receives an authorization result such as a code or token, and may use provider-supplied identity information to establish a local session. In the authorization-code and implicit flows, important data may pass through the user's browser. OpenID Connect extends OAuth with authentication features and identity tokens. [1]

The standard leaves significant implementation choices to providers and clients, so mistakes can occur on either side. Common patterns include weak `redirect_uri` validation that permits codes or tokens to be sent to an unintended destination; missing or ineffective session-bound `state` checks that enable cross-site request forgery (CSRF), including forced account linking; and client applications that trust user identity fields or tokens without validating their relationship. Browser-exposed tokens can also be exposed through redirects or other weaknesses in the client site. OpenID Connect dynamic registration can create additional risk if client-supplied metadata is fetched unsafely. [1] [2]

## Impact

Depending on the flow and flaw, an attacker may impersonate a user, take over an account, force an identity profile to be linked, or steal an authorization code or access token. A stolen token may enable access to protected APIs and sensitive account data. Unsafe server-side retrieval of registration metadata can expose the OAuth provider to server-side request forgery (SSRF). [1]

## High-level detection and assessment

In an authorized assessment, identify whether sign-in delegates to another service, then inspect the full browser-mediated flow and its HTTP requests. Note authorization endpoints and parameters such as `client_id`, `redirect_uri`, and `response_type`; determine how codes, tokens, and identity claims are returned and validated. Assess whether callback destinations are restricted to exact registered URIs, whether `state` is unpredictable and bound to the initiating session, and whether the client validates that identity data and tokens belong together. Review account-linking behavior, token exposure, and any OpenID Connect registration metadata handling. Keep testing within explicitly authorized systems. [1] [2]

## Prevention

Providers should register and enforce exact callback URI allowlists, bind an unguessable `state` value to the user's session, and verify that tokens are issued to the requesting client and used within their granted scope. Clients should use `state`, send and validate the expected `redirect_uri` during both authorization and code exchange, and avoid leaking authorization codes through referrers or externally loaded content. Use PKCE for public clients where a secret cannot be kept confidential, and validate OpenID Connect ID tokens according to the relevant specifications. Treat registration metadata as untrusted input and prevent unsafe server-side fetches. [2]

## Lab notes

- [OAuth account hijacking via `redirect_uri`](labs/lab-oauth-account-hijacking-via-redirect-uri.md)
- [Authentication bypass via OAuth implicit flow](labs/lab-oauth-authentication-bypass-via-oauth-implicit-flow.md)
- [Forced OAuth profile linking](labs/lab-oauth-forced-oauth-profile-linking.md)
- [Stealing OAuth access tokens via a proxy page](labs/lab-oauth-stealing-oauth-access-tokens-via-a-proxy-page.md)
- [Stealing OAuth access tokens via an open redirect](labs/lab-oauth-stealing-oauth-access-tokens-via-an-open-redirect.md)
- [SSRF via OpenID dynamic client registration](labs/lab-oauth-ssrf-via-openid-dynamic-client-registration.md)

## References

[1]: https://portswigger.net/web-security/oauth "PortSwigger Web Security Academy: OAuth authentication"
[2]: https://portswigger.net/web-security/oauth/preventing "PortSwigger Web Security Academy: Preventing OAuth authentication vulnerabilities"

Lab sources: [account hijacking via redirect_uri](https://portswigger.net/web-security/oauth/lab-oauth-account-hijacking-via-redirect-uri) · [authentication bypass via implicit flow](https://portswigger.net/web-security/oauth/lab-oauth-authentication-bypass-via-oauth-implicit-flow) · [forced profile linking](https://portswigger.net/web-security/oauth/lab-oauth-forced-oauth-profile-linking) · [token theft via a proxy page](https://portswigger.net/web-security/oauth/lab-oauth-stealing-oauth-access-tokens-via-a-proxy-page) · [token theft via an open redirect](https://portswigger.net/web-security/oauth/lab-oauth-stealing-oauth-access-tokens-via-an-open-redirect) · [SSRF via OpenID dynamic client registration](https://portswigger.net/web-security/oauth/openid/lab-oauth-ssrf-via-openid-dynamic-client-registration)
