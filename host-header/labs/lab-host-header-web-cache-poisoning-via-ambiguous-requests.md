# Lab: Web cache poisoning via ambiguous requests

**Official lab:** [Web cache poisoning via ambiguous requests](https://portswigger.net/web-security/host-header/exploiting/lab-host-header-web-cache-poisoning-via-ambiguous-requests)

**Lab idea:** This challenge concerns a mismatch between how a cache and a back-end application handle an ambiguous request. It practices recognizing when inconsistent parsing and cache behavior can preserve a manipulated response that affects later visitors.

## Vulnerability in brief
HTTP Host header attacks exploit unsafe handling of the `Host` request header, which identifies the domain or virtual host a client intends to reach. Servers, reverse proxies, load balancers, and applications may rely on this value to route requests or build absolute URLs. When components trust an attacker-controlled value without consistent validation or escaping, the header can influence behavior beyond selecting a site. This topic is a vulnerability class, not a general testing category.

## Solution idea
1. In Burp's browser, open the lab and click Home to refresh the home page.
2. In Proxy > HTTP history , right-click the GET / request and select Send to Repeater .
3. In Repeater, study the lab's behavior.
4. In the original response, notice the verbose caching headers, which tell you when you get a cache hit and how old the cached response is.
- …
6. Back in Burp Repeater, add a second Host header containing your exploit server domain name.
7. Send the request a couple of times until you get a cache hit with your exploit server URL reflected in the response.
8. In Burp Repeater, remove any cache busters and keep replaying the request until you have re-poisoned the cache.

## Payloads / key values
- `GET /`
- `GET /?cb=123`
- `/resources/js/tracking.js`
- `alert(document.cookie)`
- `GET /?cb=123 HTTP/1.1 Host: YOUR-LAB-ID.web-security-academy.net Host: YOUR-EXPLOIT-SERVER-ID.exploit-server.net`
- `alert()`

## Official source
- [PortSwigger Academy: Lab: Web cache poisoning via ambiguous requests](https://portswigger.net/web-security/host-header/exploiting/lab-host-header-web-cache-poisoning-via-ambiguous-requests)
