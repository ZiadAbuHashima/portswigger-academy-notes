# Lab: Detecting server-side prototype pollution without polluted property reflection

**Official lab URL:** https://portswigger.net/web-security/prototype-pollution/server-side/lab-detecting-server-side-prototype-pollution-without-polluted-property-reflection

## Lab idea

This Node.js and Express challenge focuses on confirming server-side prototype pollution when the injected property is not directly reflected. It practices using noticeable but non-destructive behavioral changes as evidence, rather than progressing to exploitation.

## Vulnerability in brief
Prototype pollution is a JavaScript vulnerability class in which attacker-controlled input changes properties on an object prototype, most often the global `Object.prototype`. Other objects may then inherit those properties through JavaScript's prototype chain. A common cause is recursively merging an input object into an existing object without safely handling special property keys such as `__proto__` or constructor-related paths. Potential sources include URL query or fragment data, JSON input, and web messages.

## Solution idea
1. Log in and visit your account page.
2. In Burp, go to the Proxy > HTTP history tab and find the POST /my-account/change-address request.
3. Observe that when you submit the form, the data from the fields is sent to the server as JSON.
4. Send the request to Burp Repeater.
- …
6. Send the request and confirm that you receive the normal response containing your user object.
7. Intentionally break the JSON syntax again and reissue the request.
8. Notice that this time, although you triggered the same error, the status and statusCode properties in the JSON response match the arbitrary error code that you injected into…

## Payloads / key values
- `POST /my-account/change-address`
- `__proto__`
- `"__proto__": { "foo":"bar" }`
- `500`
- `status`
- `400`
- `"__proto__": { "status":555 }`
- `statusCode`
- `Object.prototype`

## Official source
- [PortSwigger Academy: Lab: Detecting server-side prototype pollution without polluted property reflection](https://portswigger.net/web-security/prototype-pollution/server-side/lab-detecting-server-side-prototype-pollution-without-polluted-property-reflection)
