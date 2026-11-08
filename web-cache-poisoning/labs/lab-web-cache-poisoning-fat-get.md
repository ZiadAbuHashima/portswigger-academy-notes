# Lab: Web cache poisoning via a fat GET request

**Official PortSwigger URL:** https://portswigger.net/web-security/web-cache-poisoning/exploiting-implementation-flaws/lab-web-cache-poisoning-fat-get

**Lab idea:** The challenge illustrates a mismatch in which a GET request body can influence the response while being omitted from the cache key. It practices identifying nonstandard request handling and assessing whether the cache and application interpret the same request components.

## Vulnerability in brief
Web cache poisoning is a vulnerability in which an attacker causes a cache to store a harmful HTTP response and then serves that response to other users. In general, the attack requires both an input that changes the back-end response and a way to have the resulting response cached. A cache identifies requests using a cache key, usually a subset of request components; inputs omitted from that key are unkeyed. If an unkeyed value influences the response, the cache may treat a harmful response as interchangeable with a normal one. [PortSwigger's topic guide](https://portswigger.net/web-security/web-cache-poisoning)

## Solution idea
1. Observe that every page imports the script /js/geolocate.js , executing the callback function setCountryCookie() .
2. Notice that you can control the name of the function that is called in the response by passing in a duplicate callback parameter via the request body.
3. Send the request again, but this time pass in alert(1) as the callback function.
4. Remove any cache busters and re-poison the cache.

## Payloads / key values
- `/js/geolocate.js`
- `setCountryCookie()`
- `GET /js/geolocate.js?callback=setCountryCookie`
- `callback`
- `GET /js/geolocate.js?callback=setCountryCookie … callback=arbitraryFunction HTTP/1.1 200 OK X-Cache-Key: /js/geolocate.js?callback=setCountryCookie … arbitraryFunction({"country" : "United Kingdom"})`
- `alert(1)`

## Official source
- [PortSwigger Academy: Lab: Web cache poisoning via a fat GET request](https://portswigger.net/web-security/web-cache-poisoning/exploiting-implementation-flaws/lab-web-cache-poisoning-fat-get)
