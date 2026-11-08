# Lab: Client-side prototype pollution in third-party libraries

**Official lab URL:** https://portswigger.net/web-security/prototype-pollution/client-side/lab-prototype-pollution-client-side-prototype-pollution-in-third-party-libraries

## Lab idea

This challenge explores DOM XSS caused by a gadget in a third-party JavaScript library, where minified source can make the relevant behavior less apparent. It practices tracing client-side pollution into dependency behavior and understanding the victim-side impact.

## Vulnerability in brief
Prototype pollution is a JavaScript vulnerability class in which attacker-controlled input changes properties on an object prototype, most often the global `Object.prototype`. Other objects may then inherit those properties through JavaScript's prototype chain. A common cause is recursively merging an input object into an existing object without safely handling special property keys such as `__proto__` or constructor-related paths. Potential sources include URL query or fragment data, JSON input, and web messages.

## Solution idea
1. Load the lab in Burp's built-in browser.
2. Enable DOM Invader and enable the prototype pollution option .
3. Open the browser DevTools panel, go to the DOM Invader tab, then reload the page.
4. Observe that DOM Invader has identified two prototype pollution vectors in the hash property i.e.
- …
6. In the Body section, craft an exploit that will navigate the victim to a malicious URL as follows: <script>…
7. Test the exploit on yourself, making sure that you're navigated to the lab's home page and that the alert(document.cookie) payload is triggered.
8. Go back to the exploit server and deliver the exploit to the victim to solve the lab.

## Payloads / key values
- `hash`
- `setTimeout()`
- `hitCallback`
- `alert(1)`
- `<script> location="https://YOUR-LAB-ID.web-security-academy.net/#__proto__[hitCallback]=alert%28document.cookie%29" </script>`
- `alert(document.cookie)`

## Official source
- [PortSwigger Academy: Lab: Client-side prototype pollution in third-party libraries](https://portswigger.net/web-security/prototype-pollution/client-side/lab-prototype-pollution-client-side-prototype-pollution-in-third-party-libraries)
