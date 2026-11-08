# Lab: Web cache poisoning with an unkeyed cookie

**Official PortSwigger URL:** https://portswigger.net/web-security/web-cache-poisoning/exploiting-design-flaws/lab-web-cache-poisoning-with-an-unkeyed-cookie

**Lab idea:** The challenge demonstrates the risk when a cookie influences generated response content but is not part of the cache key. It practices identifying the relationship between cookie-controlled data, response generation, and cache equivalence.

## Vulnerability in brief
Web cache poisoning is a vulnerability in which an attacker causes a cache to store a harmful HTTP response and then serves that response to other users. In general, the attack requires both an input that changes the back-end response and a way to have the resulting response cached. A cache identifies requests using a cache key, usually a subset of request components; inputs omitted from that key are unkeyed. If an unkeyed value influences the response, the cache may treat a harmful response as interchangeable with a normal one. [PortSwigger's topic guide](https://portswigger.net/web-security/web-cache-poisoning)

## Solution idea
1. With Burp running, load the website's home page.
2. In Burp, go to "Proxy" > "HTTP history" and study the requests and responses that you generated.
3. Reload the home page and observe that the value from the fehost cookie is reflected inside a double-quoted JavaScript object in the response.
4. Send this request to Burp Repeater and add a cache-buster query parameter.
- …
6. Replay the request until you see the payload in the response and X-Cache: hit in the headers.
7. Load the URL in the browser and confirm the alert() fires.
8. Go back Burp Repeater, remove the cache buster, and replay the request to keep the cache poisoned until the victim visits the site and the lab is solved.

## Payloads / key values
- `fehost=prod-cache-01`
- `fehost`
- `fehost=someString"-alert(1)-"someString`
- `X-Cache: hit`
- `alert()`

## Official source
- [PortSwigger Academy: Lab: Web cache poisoning with an unkeyed cookie](https://portswigger.net/web-security/web-cache-poisoning/exploiting-design-flaws/lab-web-cache-poisoning-with-an-unkeyed-cookie)
