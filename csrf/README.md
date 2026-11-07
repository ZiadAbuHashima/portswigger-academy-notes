# Cross-site request forgery (CSRF)

Cross-site request forgery (CSRF) is a web security vulnerability that tricks a user’s browser into sending an unintended, authenticated request to an application where that user is signed in. The browser may automatically attach session credentials, so the application can mistake the forged request for an action the user chose to perform. CSRF can also arise where browsers automatically supply credentials such as HTTP Basic authentication or client certificates. [Official topic](https://portswigger.net/web-security/csrf)

## Main concepts

A typical CSRF risk combines three conditions: an action worth inducing, authentication that is automatically attached to requests (commonly a session cookie), and no unpredictable request value that the attacker cannot know or obtain. The request must be accepted as an ordinary authorized action. CSRF tokens are intended to add such an unpredictable value. Browser cookie policies, especially SameSite, and checks of the HTTP Referer header are also used as defenses, though implementation details matter.

Common causes include missing CSRF defenses, predictable or improperly bound tokens, validation that is skipped for some methods or when a token is absent, and weak fallback behavior in Referer checks. Cookie-based defenses can also be undermined by incomplete coverage or by assumptions about site boundaries and related domains. A state-changing function that accepts easily constructed parameters is especially relevant when the browser supplies the user’s credentials automatically.

## Impact

A successful attack can make a victim change account details or passwords, transfer funds, or perform other actions without intending to do so. Depending on the action, this may enable account takeover. If a privileged user is affected, the consequences can extend to sensitive application data and functionality.

## High-level testing context

In authorized testing, identify sensitive actions and inspect how authentication and request validation work. Assess whether requests depend only on browser-supplied credentials, whether every relevant request requires a fresh unpredictable token, and whether token validation is correctly bound to the user session and enforced consistently. Review behavior across accepted methods and missing or malformed security metadata. Consider SameSite cookie settings, Referer validation, and related same-site hosts or client-side flows. Use controlled test accounts and non-production targets, and confirm impact without affecting real users.

## Prevention

Use unpredictable, high-entropy CSRF tokens bound to the current user session, and strictly validate them server-side for every relevant state-changing request. Reject requests when the token is missing or invalid, regardless of HTTP method or content type. Treat tokens as secrets; do not put them in cookies or URLs. Set explicit SameSite cookie restrictions, ideally `Strict` where suitable, and avoid `SameSite=None` unless required and understood. SameSite is an additional layer, not a replacement for robust token validation; Referer checks are generally less effective and should not be the sole control. Also isolate untrusted content and audit sibling domains, since same-site origins can still create risks. [Prevention guidance](https://portswigger.net/web-security/csrf/preventing)

## Lab notes

- [Lab: CSRF with broken Referer validation](labs/lab-referer-validation-broken.md)
- [Lab: CSRF where Referer validation depends on header being present](labs/lab-referer-validation-depends-on-header-being-present.md)
- [Lab: SameSite Lax bypass via method override](labs/lab-samesite-lax-bypass-via-method-override.md)
- [Lab: SameSite Strict bypass via client-side redirect](labs/lab-samesite-strict-bypass-via-client-side-redirect.md)
- [Lab: SameSite Strict bypass via sibling domain](labs/lab-samesite-strict-bypass-via-sibling-domain.md)
- [Lab: CSRF where token is duplicated in cookie](labs/lab-token-duplicated-in-cookie.md)
- [Lab: CSRF where token is not tied to user session](labs/lab-token-not-tied-to-user-session.md)
- [Lab: CSRF where token is tied to non-session cookie](labs/lab-token-tied-to-non-session-cookie.md)
- [Lab: CSRF where token validation depends on request method](labs/lab-token-validation-depends-on-request-method.md)
- [Lab: CSRF where token validation depends on token being present](labs/lab-token-validation-depends-on-token-being-present.md)
- [Lab: CSRF vulnerability with no defenses](labs/lab-no-defenses.md)

## References

- [Cross-site request forgery (CSRF) — official topic](https://portswigger.net/web-security/csrf)
- [How to prevent CSRF vulnerabilities — official guidance](https://portswigger.net/web-security/csrf/preventing)
- [Lab: CSRF with broken Referer validation](https://portswigger.net/web-security/csrf/bypassing-referer-based-defenses/lab-referer-validation-broken)
- [Lab: CSRF where Referer validation depends on header being present](https://portswigger.net/web-security/csrf/bypassing-referer-based-defenses/lab-referer-validation-depends-on-header-being-present)
- [Lab: SameSite Lax bypass via method override](https://portswigger.net/web-security/csrf/bypassing-samesite-restrictions/lab-samesite-lax-bypass-via-method-override)
- [Lab: SameSite Strict bypass via client-side redirect](https://portswigger.net/web-security/csrf/bypassing-samesite-restrictions/lab-samesite-strict-bypass-via-client-side-redirect)
- [Lab: SameSite Strict bypass via sibling domain](https://portswigger.net/web-security/csrf/bypassing-samesite-restrictions/lab-samesite-strict-bypass-via-sibling-domain)
- [Lab: CSRF where token is duplicated in cookie](https://portswigger.net/web-security/csrf/bypassing-token-validation/lab-token-duplicated-in-cookie)
- [Lab: CSRF where token is not tied to user session](https://portswigger.net/web-security/csrf/bypassing-token-validation/lab-token-not-tied-to-user-session)
- [Lab: CSRF where token is tied to non-session cookie](https://portswigger.net/web-security/csrf/bypassing-token-validation/lab-token-tied-to-non-session-cookie)
- [Lab: CSRF where token validation depends on request method](https://portswigger.net/web-security/csrf/bypassing-token-validation/lab-token-validation-depends-on-request-method)
- [Lab: CSRF where token validation depends on token being present](https://portswigger.net/web-security/csrf/bypassing-token-validation/lab-token-validation-depends-on-token-being-present)
- [Lab: CSRF vulnerability with no defenses](https://portswigger.net/web-security/csrf/lab-no-defenses)
