# Lab: Cache key injection

**Official PortSwigger URL:** https://portswigger.net/web-security/web-cache-poisoning/exploiting-implementation-flaws/lab-web-cache-poisoning-cache-key-injection

**Lab idea:** This lab combines several independent web behaviors, including a weakness that allows input to affect how the cache key is constructed. It practices tracing interactions across request parsing, response handling, and cache identity at a conceptual level.

## Vulnerability in brief
Web cache poisoning is a vulnerability in which an attacker causes a cache to store a harmful HTTP response and then serves that response to other users. In general, the attack requires both an input that changes the back-end response and a way to have the resulting response cached. A cache identifies requests using a cache key, usually a subset of request components; inputs omitted from that key are unkeyed. If an unkeyed value influences the response, the cache may treat a harmful response as interchangeable with a normal one. [PortSwigger's topic guide](https://portswigger.net/web-security/web-cache-poisoning)

## Solution idea
1. Observe that the redirect at /login excludes the parameter utm_content from the cache key using a flawed regex.
2. Observe that the page at /login/ has an import from /js/localize.js .
3. Observe that the login page references an endpoint at /js/localize.js that is vulnerable to response header injection via the Origin request header, provided the cors parameter is set to 1 .
4. Use the Pragma: x-get-cache-key header to identify that the server is vulnerable to cache key injection, meaning the header injection can be triggered via a crafted URL.
5. Combine these four behaviors by poisoning the cache with following two requests: GET /js/localize.js?lang=en?utm_content=z&cors=1&x=1 HTTP/2 Origin…
6. This will poison /login?lang=en such that it redirects to a login page with a poisoned localization import that executes alert(1) , solving the lab.

## Payloads / key values
- `/login`
- `utm_content`
- `lang`
- `/login?lang=en?utm_content=anything`
- `/login/`
- `/js/localize.js`
- `Origin`
- `cors`
- `1`
- `Pragma: x-get-cache-key`
- `GET /js/localize.js?lang=en?utm_content=z&cors=1&x=1 HTTP/2 Origin: x%0d%0aContent-Length:%208%0d%0a%0d%0aalert(1)$$$$ GET /login?lang=en?utm_content=x%26cors=1%26x=1$$origin=x%250d%250aContent-Length:%208%250d%250a%250d%250aalert(1)$$%23 HTTP/2`
- `/login?lang=en`
- `alert(1)`

## Official source
- [PortSwigger Academy: Lab: Cache key injection](https://portswigger.net/web-security/web-cache-poisoning/exploiting-implementation-flaws/lab-web-cache-poisoning-cache-key-injection)
