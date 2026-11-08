# Lab: DOM XSS via an alternative prototype pollution vector

**Official lab URL:** https://portswigger.net/web-security/prototype-pollution/client-side/lab-prototype-pollution-dom-xss-via-an-alternative-prototype-pollution-vector

## Lab idea

This challenge practices identifying an alternate client-side pollution path and a JavaScript gadget that can lead to DOM XSS. Its emphasis is on analyzing the execution context and how inherited data interacts with application code.

## Vulnerability in brief
Prototype pollution is a JavaScript vulnerability class in which attacker-controlled input changes properties on an object prototype, most often the global `Object.prototype`. Other objects may then inherit those properties through JavaScript's prototype chain. A common cause is recursively merging an input object into an existing object without safely handling special property keys such as `__proto__` or constructor-related paths. Potential sources include URL query or fragment data, JSON input, and web messages.

## Solution idea

### Manual solution
1. In your browser, try polluting Object.prototype by injecting an arbitrary property via the query string: /?__proto__[foo]=bar
2. Open the browser DevTools panel and go to the Console tab.
3. Enter Object.prototype .
4. Study the properties of the returned object and observe that your injected foo property has not been added.
- …
6. Click the line number again to remove the breakpoint, then click the play icon at the top of the browser window to resume code execution.
7. Add trailing minus character to the payload to fix up the final JavaScript syntax: /?__proto__.sequence=alert(1)-
8. Observe that the alert(1) is called and the lab is solved.

### DOM Invader solution
1. Load the lab in Burp's built-in browser.
2. Enable DOM Invader and enable the prototype pollution option .
3. Open the browser DevTools panel and go to the DOM Invader tab and reload the page.
4. Observe that DOM Invader has identified a prototype pollution vector in the search property i.e.
- …
6. Go back to the previous browser tab and look at the eval() sink again in DOM Invader.
7. Click Exploit again.
8. Observe that the alert(1) is called and the lab is solved.

## Payloads / key values
- `Object.prototype`
- `/?__proto__[foo]=bar`
- `foo`
- `/?__proto__.foo=bar`
- `bar`
- `eval()`
- `searchLoggerAlternative.js`
- `manager.sequence`
- `sequence`
- `/?__proto__.sequence=alert(1)`
- `alert(1)1`
- `1`
- `/?__proto__.sequence=alert(1)-`
- `alert(1)`
- `search`
- `alert()`
- `-`

## Official source
- [PortSwigger Academy: Lab: DOM XSS via an alternative prototype pollution vector](https://portswigger.net/web-security/prototype-pollution/client-side/lab-prototype-pollution-dom-xss-via-an-alternative-prototype-pollution-vector)
