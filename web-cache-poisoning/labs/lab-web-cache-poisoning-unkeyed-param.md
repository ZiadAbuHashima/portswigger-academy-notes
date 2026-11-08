# Lab: Web cache poisoning via an unkeyed query parameter

**Official PortSwigger URL:** https://portswigger.net/web-security/web-cache-poisoning/exploiting-implementation-flaws/lab-web-cache-poisoning-unkeyed-param

**Lab idea:** The challenge demonstrates a supported query parameter that is excluded from the cache key but still reflected in the response. It practices identifying unkeyed parameters and understanding the risk when their values influence generated content.

## Vulnerability in brief
Web cache poisoning is a vulnerability in which an attacker causes a cache to store a harmful HTTP response and then serves that response to other users. In general, the attack requires both an input that changes the back-end response and a way to have the resulting response cached. A cache identifies requests using a cache key, usually a subset of request components; inputs omitted from that key are unkeyed. If an unkeyed value influences the response, the cache may treat a harmful response as interchangeable with a normal one. [PortSwigger's topic guide](https://portswigger.net/web-security/web-cache-poisoning)

## Solution idea
1. Observe that the home page is a suitable cache oracle.
2. Add a cache-buster query parameter.
3. Use Param Miner's "Guess GET parameters" feature to identify that the parameter utm_content is supported by the application.
4. Confirm that this parameter is unkeyed by adding it to the query string and checking that you still get a cache hit.
5. Send a request with a utm_content parameter that breaks out of the reflected string and injects an XSS payload: GET /?utm_content='/><script>alert(1)</script>
6. Once your payload is cached, remove the utm_content parameter, right-click on the request, and select "Copy URL".
7. Remove your cache buster, re-add the utm_content parameter with your payload, and replay the request until the cache is poisoned for normal users.

## Payloads / key values
- `utm_content`
- `GET /?utm_content='/><script>alert(1)</script>`
- `alert()`

## Official source
- [PortSwigger Academy: Lab: Web cache poisoning via an unkeyed query parameter](https://portswigger.net/web-security/web-cache-poisoning/exploiting-implementation-flaws/lab-web-cache-poisoning-unkeyed-param)
