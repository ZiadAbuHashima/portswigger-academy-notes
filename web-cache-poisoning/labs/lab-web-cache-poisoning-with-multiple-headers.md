# Lab: Web cache poisoning with multiple headers

**Official PortSwigger URL:** https://portswigger.net/web-security/web-cache-poisoning/exploiting-design-flaws/lab-web-cache-poisoning-with-multiple-headers

**Lab idea:** This challenge requires understanding how the combined effect of more than one supported request header changes a response that can be cached. It practices testing interactions between headers rather than evaluating each input in isolation.

## Vulnerability in brief
Web cache poisoning is a vulnerability in which an attacker causes a cache to store a harmful HTTP response and then serves that response to other users. In general, the attack requires both an input that changes the back-end response and a way to have the resulting response cached. A cache identifies requests using a cache key, usually a subset of request components; inputs omitted from that key are unkeyed. If an unkeyed value influences the response, the cache may treat a harmful response as interchangeable with a normal one. [PortSwigger's topic guide](https://portswigger.net/web-security/web-cache-poisoning)

## Solution idea
1. With Burp running, load the website's home page.
2. Go to "Proxy" > "HTTP history" and study the requests and responses that you generated.
3. Add a cache-buster query parameter and the X-Forwarded-Host header with an arbitrary hostname, such as example.com .
4. Remove the X-Forwarded-Host header and add the X-Forwarded-Scheme header instead.
- …
6. Go back to Burp Repeater, remove the cache buster, and resend the request until you poison the cache again.
7. To simulate the victim, reload the home page in the browser and make sure that the alert() fires.
8. Keep replaying the request to keep the cache poisoned until the victim visits the site and the lab is solved.

## Payloads / key values
- `GET`
- `/resources/js/tracking.js`
- `X-Forwarded-Host`
- `example.com`
- `X-Forwarded-Scheme`
- `HTTPS`
- `Location`
- `https://`
- `X-Forwarded-Host: example.com`
- `X-Forwarded-Scheme: nothttps`
- `https://example.com/`
- `alert(document.cookie)`
- `X-Forwarded-Host: YOUR-EXPLOIT-SERVER-ID.exploit-server.net`
- `X-Cache: hit`
- `alert()`

## Official source
- [PortSwigger Academy: Lab: Web cache poisoning with multiple headers](https://portswigger.net/web-security/web-cache-poisoning/exploiting-design-flaws/lab-web-cache-poisoning-with-multiple-headers)
