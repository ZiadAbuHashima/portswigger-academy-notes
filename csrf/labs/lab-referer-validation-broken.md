# Lab: CSRF with broken Referer validation

**Official lab:** [Lab: CSRF with broken Referer validation](https://portswigger.net/web-security/csrf/bypassing-referer-based-defenses/lab-referer-validation-broken)

## Lab idea

This challenge focuses on a change-email action protected by a flawed Referer check. It practices assessing whether origin/referrer validation actually distinguishes trusted application requests from cross-domain requests.

## Vulnerability in brief
Cross-site request forgery (CSRF) is a web security vulnerability that tricks a user’s browser into sending an unintended, authenticated request to an application where that user is signed in. The browser may automatically attach session credentials, so the application can mistake the forged request for an action the user chose to perform. CSRF can also arise where browsers automatically supply credentials such as HTTP Basic authentication or client certificates. [Official topic](https://portswigger.net/web-security/csrf)

## Solution idea
1. Open Burp's browser and log in to your account.
2. Send the request to Burp Repeater.
3. Copy the original domain of your lab instance and append it to the Referer header in the form of a query string.
4. Send the request and observe that it is now accepted.
5. Create a CSRF proof of concept exploit as described in the solution to the CSRF vulnerability with no defenses lab and host it on the exploit server.
6. If you store the exploit and test it by clicking "View exploit", you may encounter the "invalid Referer header" error again.
7. Change the email address in your exploit so that it doesn't match your own.
8. Store the exploit, then click "Deliver to victim" to solve the lab.

## Payloads / key values
- `Referer: https://arbitrary-incorrect-domain.net?YOUR-LAB-ID.web-security-academy.net`
- `history.pushState()`
- `history.pushState("", "", "/?YOUR-LAB-ID.web-security-academy.net")`
- `Referrer-Policy: unsafe-url`

## Official source
- [PortSwigger Academy: Lab: CSRF with broken Referer validation](https://portswigger.net/web-security/csrf/bypassing-referer-based-defenses/lab-referer-validation-broken)
