# Web cache deception (WCD)

Web cache deception (WCD) is a vulnerability in which an attacker can cause a shared web cache to store a victim's sensitive, personalized response as though it were a cacheable static resource. The core weakness is a mismatch between how the cache and the origin server interpret the same request URL. A victim's browser can be induced to request an ambiguous URL; if the origin serves private content while the cache treats the request as cacheable, another party may retrieve that stored response. This differs from web cache poisoning, which aims to place attacker-controlled content in a cache. [1]

## Main concepts and impact

Caches use cache keys and configured rules to decide whether requests are equivalent and which responses to store. Rules may match static file extensions, directory prefixes, or exact file names. WCD can arise when cache and origin disagree about path mapping, delimiter characters, or path normalization. The origin may route an unusual-looking path to a personalized endpoint while the cache classifies it as static content. [1]

Successful exploitation can expose account-specific information, such as API keys or other private data, to an unauthorized party. The risk depends on what the endpoint returns, whether the response is stored in a shared cache, and whether an attacker can cause a victim to make the relevant request. [1]

## High-level assessment context

During authorized testing, identify endpoints that return user-specific content and compare how the origin and cache handle URL paths. Look for differences in path mapping, delimiter handling, and normalization, and determine whether responses appear to be cached. Cache-related response headers such as `X-Cache` and `Cache-Control`, repeated-request behavior, and response timing can provide clues; a single header or timing observation is not conclusive. Keep testing within scope and avoid collecting or exposing other users' sensitive data. [1]

## Prevention

Do not store personalized or authenticated responses in shared caches. Set explicit cache directives appropriate to sensitive responses, such as `private` or `no-store`, and review CDN and reverse-proxy rules so that dynamic endpoints cannot be classified as static based only on ambiguous URL patterns. Ensure the cache and origin apply consistent URL parsing, path normalization, and delimiter handling. Test cache behavior for authenticated responses and unusual paths as part of security review. [1]

## Lab notes

- [Exploiting cache server normalization for web cache deception](labs/lab-wcd-exploiting-cache-server-normalization.md)
- [Exploiting exact-match cache rules for web cache deception](labs/lab-wcd-exploiting-exact-match-cache-rules.md)
- [Exploiting origin server normalization for web cache deception](labs/lab-wcd-exploiting-origin-server-normalization.md)
- [Exploiting path delimiters for web cache deception](labs/lab-wcd-exploiting-path-delimiters.md)
- [Exploiting path mapping for web cache deception](labs/lab-wcd-exploiting-path-mapping.md)

## References

[1]: https://portswigger.net/web-security/web-cache-deception "PortSwigger Web Security Academy: Web cache deception"
[2]: https://portswigger.net/web-security/web-cache-deception/lab-wcd-exploiting-cache-server-normalization "Lab: Exploiting cache server normalization for web cache deception"
[3]: https://portswigger.net/web-security/web-cache-deception/lab-wcd-exploiting-exact-match-cache-rules "Lab: Exploiting exact-match cache rules for web cache deception"
[4]: https://portswigger.net/web-security/web-cache-deception/lab-wcd-exploiting-origin-server-normalization "Lab: Exploiting origin server normalization for web cache deception"
[5]: https://portswigger.net/web-security/web-cache-deception/lab-wcd-exploiting-path-delimiters "Lab: Exploiting path delimiters for web cache deception"
[6]: https://portswigger.net/web-security/web-cache-deception/lab-wcd-exploiting-path-mapping "Lab: Exploiting path mapping for web cache deception"
