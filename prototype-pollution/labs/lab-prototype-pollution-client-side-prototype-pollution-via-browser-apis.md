# Lab: Client-side prototype pollution via browser APIs

**Official lab URL:** https://portswigger.net/web-security/prototype-pollution/client-side/browser-apis/lab-prototype-pollution-client-side-prototype-pollution-via-browser-apis

## Lab idea

This challenge centers on client-side prototype pollution leading to DOM XSS, with developers having attempted to mitigate a potential gadget. It practices recognizing a pollution source and analyzing browser-side gadget behavior despite an incomplete defense.

## Vulnerability in brief
Prototype pollution is a JavaScript vulnerability class in which attacker-controlled input changes properties on an object prototype, most often the global `Object.prototype`. Other objects may then inherit those properties through JavaScript's prototype chain. A common cause is recursively merging an input object into an existing object without safely handling special property keys such as `__proto__` or constructor-related paths. Potential sources include URL query or fragment data, JSON input, and web messages.

## Solution idea

### Manual solution
1. In your browser, try polluting Object.prototype by injecting an arbitrary property via the query string: /?__proto__[foo]=bar
2. Open the browser DevTools panel and go to the Console tab.
3. Enter Object.prototype .
4. Study the properties of the returned object and observe that your injected foo property has been added.
- …
6. In the browser DevTools panel, go to the Elements tab and study the HTML content of the page.
7. Modify the payload in the URL to inject an XSS proof-of-concept.
8. Observe that the alert(1) is called and the lab is solved.

### DOM Invader solution
1. Load the lab in Burp's built-in browser.
2. Enable DOM Invader and enable the prototype pollution option .
3. Open the browser DevTools panel, go to the DOM Invader tab, then reload the page.
4. Observe that DOM Invader has identified two prototype pollution vectors in the search property i.e.
5. Click Scan for gadgets .
6. When the scan is complete, open the DevTools panel in the same tab as the scan, then go to the DOM Invader tab.
7. Observe that DOM Invader has successfully accessed the script.src sink via the value gadget.
8. Click Exploit .

## Payloads / key values
- `Object.prototype`
- `/?__proto__[foo]=bar`
- `foo`
- `searchLoggerConfigurable.js`
- `config`
- `transport_url`
- `Object.defineProperty()`
- `value`
- `/?__proto__[value]=foo`
- `<script>`
- `src`
- `data:`
- `/?__proto__[value]=data:,alert(1);`
- `alert(1)`
- `search`
- `script.src`

## Official source
- [PortSwigger Academy: Lab: Client-side prototype pollution via browser APIs](https://portswigger.net/web-security/prototype-pollution/client-side/browser-apis/lab-prototype-pollution-client-side-prototype-pollution-via-browser-apis)
