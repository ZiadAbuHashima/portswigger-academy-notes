# Lab: DOM XSS via client-side prototype pollution

**Official lab URL:** https://portswigger.net/web-security/prototype-pollution/client-side/lab-prototype-pollution-dom-xss-via-client-side-prototype-pollution

## Lab idea

This introductory challenge demonstrates the relationship between a client-side pollution source, an inherited gadget property, and a DOM XSS sink. It practices reasoning from controllable input to unsafe browser behavior.

## Vulnerability in brief
Prototype pollution is a JavaScript vulnerability class in which attacker-controlled input changes properties on an object prototype, most often the global `Object.prototype`. Other objects may then inherit those properties through JavaScript's prototype chain. A common cause is recursively merging an input object into an existing object without safely handling special property keys such as `__proto__` or constructor-related paths. Potential sources include URL query or fragment data, JSON input, and web messages.

## Solution idea

### Manual solution
1. In your browser, try polluting Object.prototype by injecting an arbitrary property via the query string: /?__proto__[foo]=bar
2. Open the browser DevTools panel and go to the Console tab.
3. Enter Object.prototype .
4. Study the properties of the returned object.
- …
6. In the browser DevTools panel, go to the Elements tab and study the HTML content of the page.
7. Modify the payload in the URL to inject an XSS proof-of-concept.
8. Observe that the alert(1) is called and the lab is solved.

### DOM Invader solution
1. Open the lab in Burp's built-in browser.
2. Enable DOM Invader and enable the prototype pollution option .
3. Open the browser DevTools panel, go to the DOM Invader tab, then reload the page.
4. Observe that DOM Invader has identified two prototype pollution vectors in the search property i.e.
5. Click Scan for gadgets .
6. When the scan is complete, open the DevTools panel in the same tab as the scan, then go to the DOM Invader tab.
7. Observe that DOM Invader has successfully accessed the script.src sink via the transport_url gadget.
8. Click Exploit .

## Payloads / key values
- `Object.prototype`
- `/?__proto__[foo]=bar`
- `foo`
- `bar`
- `searchLogger.js`
- `config`
- `transport_url`
- `src`
- `<script>`
- `/?__proto__[transport_url]=foo`
- `data:`
- `/?__proto__[transport_url]=data:,alert(1);`
- `alert(1)`
- `search`
- `script.src`

## Official source
- [PortSwigger Academy: Lab: DOM XSS via client-side prototype pollution](https://portswigger.net/web-security/prototype-pollution/client-side/lab-prototype-pollution-dom-xss-via-client-side-prototype-pollution)
