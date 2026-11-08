# Lab: Web cache poisoning with an unkeyed header

**Official PortSwigger URL:** https://portswigger.net/web-security/web-cache-poisoning/exploiting-design-flaws/lab-web-cache-poisoning-with-an-unkeyed-header

**Lab idea:** This lab centers on an unkeyed request header that is handled unsafely and affects a cached page response. It practices recognizing when a header changes back-end output even though the cache does not distinguish requests by that header.

## Vulnerability in brief
Web cache poisoning is a vulnerability in which an attacker causes a cache to store a harmful HTTP response and then serves that response to other users. In general, the attack requires both an input that changes the back-end response and a way to have the resulting response cached. A cache identifies requests using a cache key, usually a subset of request components; inputs omitted from that key are unkeyed. If an unkeyed value influences the response, the cache may treat a harmful response as interchangeable with a normal one. [PortSwigger's topic guide](https://portswigger.net/web-security/web-cache-poisoning)

## Solution idea
1. With Burp running, load the website's home page
2. In Burp, go to "Proxy" > "HTTP history" and study the requests and responses that you generated.
3. Add a cache-buster query parameter, such as ?cb=1234 .
4. Add the X-Forwarded-Host header with an arbitrary hostname, such as example.com , and send the request.
- …
6. Send your malicious request.
7. To simulate the victim, load the poisoned URL in the browser and make sure that the alert() is triggered.
8. If the lab is still not solved, the victim did not access the page while the cache was poisoned.

## Payloads / key values
- `GET`
- `?cb=1234`
- `X-Forwarded-Host`
- `example.com`
- `/resources/js/tracking.js`
- `X-Cache: hit`
- `alert(document.cookie)`
- `X-Forwarded-Host: YOUR-EXPLOIT-SERVER-ID.exploit-server.net`
- `alert()`

## Official source
- [PortSwigger Academy: Lab: Web cache poisoning with an unkeyed header](https://portswigger.net/web-security/web-cache-poisoning/exploiting-design-flaws/lab-web-cache-poisoning-with-an-unkeyed-header)
