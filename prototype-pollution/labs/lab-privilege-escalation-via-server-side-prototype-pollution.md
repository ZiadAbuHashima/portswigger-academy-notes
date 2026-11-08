# Lab: Privilege escalation via server-side prototype pollution

**Official lab URL:** https://portswigger.net/web-security/prototype-pollution/server-side/lab-privilege-escalation-via-server-side-prototype-pollution

## Lab idea

This Node.js and Express challenge makes inherited polluted properties visible in an HTTP response and uses a privilege-escalation objective. It practices recognizing prototype-chain reflection and assessing how a gadget can affect authorization.

## Vulnerability in brief
Prototype pollution is a JavaScript vulnerability class in which attacker-controlled input changes properties on an object prototype, most often the global `Object.prototype`. Other objects may then inherit those properties through JavaScript's prototype chain. A common cause is recursively merging an input object into an existing object without safely handling special property keys such as `__proto__` or constructor-related paths. Potential sources include URL query or fragment data, JSON input, and web messages.

## Solution idea
1. Log in and visit your account page.
2. In Burp, go to the Proxy > HTTP history tab and find the POST /my-account/change-address request.
3. Observe that when you submit the form, the data from the fields is sent to the server as JSON.
4. Notice that the server responds with a JSON object that appears to represent your user.
- …
6. Modify the request to try polluting the prototype with your own isAdmin property: "__proto__": { "isAdmin":true }
7. In the browser, refresh the page and confirm that you now have a link to access the admin panel.
8. Go to the admin panel and delete carlos to solve the lab.

## Payloads / key values
- `POST /my-account/change-address`
- `__proto__`
- `"__proto__": { "foo":"bar" }`
- `isAdmin`
- `false`
- `"__proto__": { "isAdmin":true }`
- `carlos`

## Official source
- [PortSwigger Academy: Lab: Privilege escalation via server-side prototype pollution](https://portswigger.net/web-security/prototype-pollution/server-side/lab-privilege-escalation-via-server-side-prototype-pollution)
