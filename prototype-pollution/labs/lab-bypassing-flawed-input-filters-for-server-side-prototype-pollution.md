# Lab: Bypassing flawed input filters for server-side prototype pollution

**Official lab URL:** https://portswigger.net/web-security/prototype-pollution/server-side/lab-bypassing-flawed-input-filters-for-server-side-prototype-pollution

## Lab idea

This Node.js and Express challenge involves unsafe merging of user-controlled input and flawed filtering, with a privilege-escalation objective. It practices evaluating server-side pollution defenses and recognizing when inherited properties influence authorization-related behavior.

## Vulnerability in brief
Prototype pollution is a JavaScript vulnerability class in which attacker-controlled input changes properties on an object prototype, most often the global `Object.prototype`. Other objects may then inherit those properties through JavaScript's prototype chain. A common cause is recursively merging an input object into an existing object without safely handling special property keys such as `__proto__` or constructor-related paths. Potential sources include URL query or fragment data, JSON input, and web messages.

## Solution idea
1. Log in and visit your account page.
2. In Burp, go to the Proxy > HTTP history tab and find the POST /my-account/change-address request.
3. Observe that when you submit the form, the data from the fields is sent to the server as JSON.
4. Send the request to Burp Repeater.
- …
6. Modify the request to try polluting the prototype with your own isAdmin property: "constructor": { "prototype": { "isAdmin":true } }
7. In the browser, refresh the page and confirm that you now have a link to access the admin panel.
8. Go to the admin panel and delete carlos to solve the lab.

## Payloads / key values
- `POST /my-account/change-address`
- `__proto__`
- `json spaces`
- `"__proto__": { "json spaces":10 }`
- `constructor`
- `"constructor": { "prototype": { "json spaces":10 } }`
- `isAdmin`
- `false`
- `"constructor": { "prototype": { "isAdmin":true } }`
- `carlos`

## Official source
- [PortSwigger Academy: Lab: Bypassing flawed input filters for server-side prototype pollution](https://portswigger.net/web-security/prototype-pollution/server-side/lab-bypassing-flawed-input-filters-for-server-side-prototype-pollution)
