# Lab: Internal cache poisoning

**Official PortSwigger URL:** https://portswigger.net/web-security/web-cache-poisoning/exploiting-implementation-flaws/lab-web-cache-poisoning-internal

**Lab idea:** This lab uses multiple cache layers whose treatment of request inputs differs. It practices distinguishing behavior at an external cache from behavior in an internal cache and understanding how a response fragment can be stored separately.

## Vulnerability in brief
Web cache poisoning is a vulnerability in which an attacker causes a cache to store a harmful HTTP response and then serves that response to other users. In general, the attack requires both an input that changes the back-end response and a way to have the resulting response cached. A cache identifies requests using a cache key, usually a subset of request components; inputs omitted from that key are unkeyed. If an unkeyed value influences the response, the cache may treat a harmful response as interchangeable with a normal one. [PortSwigger's topic guide](https://portswigger.net/web-security/web-cache-poisoning)

## Solution idea
1. Notice that the home page is a suitable cache oracle and send the GET / request to Burp Repeater.
2. Observe that any changes to the query string are always reflected in the response.
3. Observe that the X-Forwarded-Host header is supported.
4. Send the request.
- …
6. Go to the exploit server and create a file at /js/geolocate.js containing the payload alert(document.cookie) .
7. Back in Burp Repeater, disable the dynamic cache buster in the query string and re-add the X-Forwarded-Host header to point to your exploit server.
8. Send the request over and over until all three of the dynamic URLs in the response point to your exploit server.

## Payloads / key values
- `GET /`
- `X-Forwarded-Host`
- `X-Forwarded-Host: YOUR-EXPLOIT-SERVER-ID.exploit-server.net`
- `analytics.js`
- `geolocate.js`
- `/js/geolocate.js`
- `alert(document.cookie)`

## Official source
- [PortSwigger Academy: Lab: Internal cache poisoning](https://portswigger.net/web-security/web-cache-poisoning/exploiting-implementation-flaws/lab-web-cache-poisoning-internal)
