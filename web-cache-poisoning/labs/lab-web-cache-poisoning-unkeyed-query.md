# Lab: Web cache poisoning via an unkeyed query string

**Official PortSwigger URL:** https://portswigger.net/web-security/web-cache-poisoning/exploiting-implementation-flaws/lab-web-cache-poisoning-unkeyed-query

**Lab idea:** This lab explores a cache that does not include the query string in its cache key, even though the application reflects query data in the response. It practices assessing cache-key composition and the consequences of request components that affect output but not cache identity.

## Vulnerability in brief
Web cache poisoning is a vulnerability in which an attacker causes a cache to store a harmful HTTP response and then serves that response to other users. In general, the attack requires both an input that changes the back-end response and a way to have the resulting response cached. A cache identifies requests using a cache key, usually a subset of request components; inputs omitted from that key are unkeyed. If an unkeyed value influences the response, the cache may treat a harmful response as interchangeable with a normal one. [PortSwigger's topic guide](https://portswigger.net/web-security/web-cache-poisoning)

## Solution idea
1. With Burp running, load the website's home page.
2. Add arbitrary query parameters to the request.
3. Notice that you can use the Origin header as a cache buster.
4. When you get a cache miss, notice that your injected parameters are reflected in the response.
- …
6. To simulate the victim, remove the query string from your request and send it again (while using the same cache buster).
7. Remove the cache-buster Origin header and add your payload back to the query string.
8. The lab will be solved when the victim user visits the poisoned home page.

## Payloads / key values
- `GET`
- `Origin`
- `GET /?evil='/><script>alert(1)</script>`
- `X-Cache: hit`

## Official source
- [PortSwigger Academy: Lab: Web cache poisoning via an unkeyed query string](https://portswigger.net/web-security/web-cache-poisoning/exploiting-implementation-flaws/lab-web-cache-poisoning-unkeyed-query)
