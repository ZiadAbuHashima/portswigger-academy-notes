# Web cache poisoning (WCP)

Web cache poisoning is a vulnerability in which an attacker causes a cache to store a harmful HTTP response and then serves that response to other users. In general, the attack requires both an input that changes the back-end response and a way to have the resulting response cached. A cache identifies requests using a cache key, usually a subset of request components; inputs omitted from that key are unkeyed. If an unkeyed value influences the response, the cache may treat a harmful response as interchangeable with a normal one. [PortSwigger's topic guide](https://portswigger.net/web-security/web-cache-poisoning)

## Main concepts and common causes

The central issue is a mismatch between what the cache uses to distinguish requests and what the application uses to generate responses. Common contributing conditions include unsafe handling of unkeyed headers, cookies, or query parameters; cache-key exclusions made for performance; inconsistent parsing or URL normalization between the cache and back end; accepting request bodies on `GET`; and complex behavior across multiple cache layers. Cacheability itself can depend on factors such as response headers, status, route, content type, or file extension.

The general attack pattern has two parts: elicit a harmful response from the back end, then get that response stored under a key that other users will request. Web cache poisoning can also involve separate client-side vulnerabilities or other implementation quirks, which is why both application behavior and cache behavior matter.

## Impact

A poisoned response can distribute client-side attacks such as cross-site scripting, JavaScript injection, or open redirection to users who request the affected resource while the cache entry is active. Impact depends on the harmful content that can be cached and the traffic to the affected page. A frequently visited resource can expose many users; a low-traffic or short-lived entry may affect fewer.

## Authorized assessment context

In an authorized test, compare responses as relevant request components change, and determine which inputs affect the application response versus the cache key. Observe cache hits, misses, expiry, and eligibility rules, and consider whether multiple cache layers behave differently. Use unique cache-busting values during investigation so test responses are not inadvertently served to other users. Keep testing within the agreed scope and avoid poisoning shared production caches.

## Prevention

Disable caching where it is not needed, or restrict it to genuinely static responses with safeguards against attacker-controlled content being served as a static resource. Review CDN and other third-party cache behavior, and disable unnecessary supported request headers. If an input is excluded from the cache key for performance, rewrite the request instead. Reject `GET` requests with bodies. Patch client-side vulnerabilities even when they appear difficult to exploit, because cache behavior can create unexpected paths to exploitation.

## Lab notes

- [Combining web cache poisoning vulnerabilities](labs/lab-web-cache-poisoning-combining-vulnerabilities.md)
- [Targeted web cache poisoning using an unknown header](labs/lab-web-cache-poisoning-targeted-using-an-unknown-header.md)
- [Web cache poisoning to exploit a DOM vulnerability via a cache with strict cacheability criteria](labs/lab-web-cache-poisoning-to-exploit-a-dom-vulnerability-via-a-cache-with-strict-cacheability-criteria.md)
- [Web cache poisoning with an unkeyed cookie](labs/lab-web-cache-poisoning-with-an-unkeyed-cookie.md)
- [Web cache poisoning with an unkeyed header](labs/lab-web-cache-poisoning-with-an-unkeyed-header.md)
- [Web cache poisoning with multiple headers](labs/lab-web-cache-poisoning-with-multiple-headers.md)
- [Cache key injection](labs/lab-web-cache-poisoning-cache-key-injection.md)
- [Web cache poisoning via a fat GET request](labs/lab-web-cache-poisoning-fat-get.md)
- [Internal cache poisoning](labs/lab-web-cache-poisoning-internal.md)
- [URL normalization](labs/lab-web-cache-poisoning-normalization.md)
- [Parameter cloaking](labs/lab-web-cache-poisoning-param-cloaking.md)
- [Web cache poisoning via an unkeyed query parameter](labs/lab-web-cache-poisoning-unkeyed-param.md)
- [Web cache poisoning via an unkeyed query string](labs/lab-web-cache-poisoning-unkeyed-query.md)

## References

- [Official topic: Web cache poisoning](https://portswigger.net/web-security/web-cache-poisoning)
- [Lab: Combining web cache poisoning vulnerabilities](https://portswigger.net/web-security/web-cache-poisoning/exploiting-design-flaws/lab-web-cache-poisoning-combining-vulnerabilities)
- [Lab: Targeted web cache poisoning using an unknown header](https://portswigger.net/web-security/web-cache-poisoning/exploiting-design-flaws/lab-web-cache-poisoning-targeted-using-an-unknown-header)
- [Lab: Web cache poisoning to exploit a DOM vulnerability via a cache with strict cacheability criteria](https://portswigger.net/web-security/web-cache-poisoning/exploiting-design-flaws/lab-web-cache-poisoning-to-exploit-a-dom-vulnerability-via-a-cache-with-strict-cacheability-criteria)
- [Lab: Web cache poisoning with an unkeyed cookie](https://portswigger.net/web-security/web-cache-poisoning/exploiting-design-flaws/lab-web-cache-poisoning-with-an-unkeyed-cookie)
- [Lab: Web cache poisoning with an unkeyed header](https://portswigger.net/web-security/web-cache-poisoning/exploiting-design-flaws/lab-web-cache-poisoning-with-an-unkeyed-header)
- [Lab: Web cache poisoning with multiple headers](https://portswigger.net/web-security/web-cache-poisoning/exploiting-design-flaws/lab-web-cache-poisoning-with-multiple-headers)
- [Lab: Cache key injection](https://portswigger.net/web-security/web-cache-poisoning/exploiting-implementation-flaws/lab-web-cache-poisoning-cache-key-injection)
- [Lab: Web cache poisoning via a fat GET request](https://portswigger.net/web-security/web-cache-poisoning/exploiting-implementation-flaws/lab-web-cache-poisoning-fat-get)
- [Lab: Internal cache poisoning](https://portswigger.net/web-security/web-cache-poisoning/exploiting-implementation-flaws/lab-web-cache-poisoning-internal)
- [Lab: URL normalization](https://portswigger.net/web-security/web-cache-poisoning/exploiting-implementation-flaws/lab-web-cache-poisoning-normalization)
- [Lab: Parameter cloaking](https://portswigger.net/web-security/web-cache-poisoning/exploiting-implementation-flaws/lab-web-cache-poisoning-param-cloaking)
- [Lab: Web cache poisoning via an unkeyed query parameter](https://portswigger.net/web-security/web-cache-poisoning/exploiting-implementation-flaws/lab-web-cache-poisoning-unkeyed-param)
- [Lab: Web cache poisoning via an unkeyed query string](https://portswigger.net/web-security/web-cache-poisoning/exploiting-implementation-flaws/lab-web-cache-poisoning-unkeyed-query)
