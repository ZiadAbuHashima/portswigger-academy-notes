# Lab: URL normalization

**Official PortSwigger URL:** https://portswigger.net/web-security/web-cache-poisoning/exploiting-implementation-flaws/lab-web-cache-poisoning-normalization

**Lab idea:** The challenge explores how browser URL encoding and cache normalization can cause the browser and cache to interpret a request path differently. It practices assessing parsing and normalization discrepancies in the context of a reflected client-side weakness.

## Vulnerability in brief
Web cache poisoning is a vulnerability in which an attacker causes a cache to store a harmful HTTP response and then serves that response to other users. In general, the attack requires both an input that changes the back-end response and a way to have the resulting response cached. A cache identifies requests using a cache key, usually a subset of request components; inputs omitted from that key are unkeyed. If an unkeyed value influences the response, the cache may treat a harmful response as interchangeable with a normal one. [PortSwigger's topic guide](https://portswigger.net/web-security/web-cache-poisoning)

## Solution idea
1. In Burp Repeater, browse to any non-existent path, such as GET /random .
2. Add a suitable reflected XSS payload to the request line: GET /random</p><script>alert(1)</script><p>foo
3. Notice that if you request this URL in the browser, the payload doesn't execute because it is URL-encoded.
4. In Burp Repeater, poison the cache with your payload and then immediately load the URL in the browser.
5. Re-poison the cache then immediately go to the lab and click "Deliver link to victim".

## Payloads / key values
- `GET /random`
- `GET /random</p><script>alert(1)</script><p>foo`
- `alert()`

## Official source
- [PortSwigger Academy: Lab: URL normalization](https://portswigger.net/web-security/web-cache-poisoning/exploiting-implementation-flaws/lab-web-cache-poisoning-normalization)
