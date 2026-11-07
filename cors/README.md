# Cross-origin resource sharing (CORS)

Cross-origin resource sharing (CORS) is a browser mechanism that lets a server selectively permit web pages from other origins to read its resources. It relaxes the same-origin policy (SOP), which otherwise restricts cross-origin access to responses. CORS is a security-sensitive trust configuration, not a general defense against cross-site request forgery (CSRF). [1]

## Main concepts and common weaknesses

A browser sends an `Origin` request header, and the server communicates its cross-origin policy through response headers such as `Access-Control-Allow-Origin` (ACAO). `Access-Control-Allow-Credentials: true` indicates that credentialed cross-origin requests may be allowed by the browser when the other requirements are met. [1]

Misconfigurations commonly include reflecting arbitrary `Origin` values, applying an overly broad or incorrectly parsed origin allowlist, trusting the special `null` origin, or trusting a subdomain that is not securely controlled. A trusted origin with a cross-site scripting flaw can also undermine the trust relationship. [1]

## Potential impact

If a browser accepts a credentialed cross-origin response, a hostile site may be able to read sensitive information available to the victim, such as account data, API keys, or tokens. Broad non-credentialed access can also matter for resources reachable from a user's browser, including internal services. The impact depends on the data exposed, the user's access, and the exact policy. CORS controls browser behavior; it does not stop direct requests or replace authentication and authorization. [1]

## High-level authorized assessment

For an authorized test, identify sensitive endpoints that are intended to support cross-origin access and examine how their CORS response changes for expected and unexpected origins. Review whether ACAO reflects input, whether allowlist matching is strict and exact, whether credentials are enabled, and whether `null`, insecure origins, or insufficiently controlled subdomains are trusted. Consider the sensitivity of readable responses and the security of every origin in the trust relationship. [1]

## Prevention

Allow only specifically identified, trusted origins and validate origins with exact, well-defined comparisons. Do not reflect arbitrary origins or allow `null` without a compelling, carefully reviewed need. Avoid wildcard trust for sensitive or internal resources, and ensure trusted subdomains use secure transport and are protected from compromise. Keep authentication, authorization, and other server-side controls in place because CORS is not a substitute for them. [1]

## Lab notes

- [CORS vulnerability with basic origin reflection](labs/lab-basic-origin-reflection-attack.md)
- [CORS vulnerability with trusted insecure protocols](labs/lab-breaking-https-attack.md)
- [CORS vulnerability with trusted null origin](labs/lab-null-origin-whitelisted-attack.md)

## References

[1]: https://portswigger.net/web-security/cors "PortSwigger Web Security Academy: Cross-origin resource sharing (CORS)"
[2]: https://portswigger.net/web-security/cors/lab-basic-origin-reflection-attack "PortSwigger Web Security Academy: CORS vulnerability with basic origin reflection"
[3]: https://portswigger.net/web-security/cors/lab-breaking-https-attack "PortSwigger Web Security Academy: CORS vulnerability with trusted insecure protocols"
[4]: https://portswigger.net/web-security/cors/lab-null-origin-whitelisted-attack "PortSwigger Web Security Academy: CORS vulnerability with trusted null origin"
