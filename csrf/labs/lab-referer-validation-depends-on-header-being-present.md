# Lab: CSRF where Referer validation depends on header being present

**Official lab:** [Lab: CSRF where Referer validation depends on header being present](https://portswigger.net/web-security/csrf/bypassing-referer-based-defenses/lab-referer-validation-depends-on-header-being-present)

## Lab idea

This challenge examines a Referer-based defense with an insecure fallback when the header is absent. It practices checking how security controls behave when expected request metadata is missing.

## Vulnerability in brief
Cross-site request forgery (CSRF) is a web security vulnerability that tricks a user’s browser into sending an unintended, authenticated request to an application where that user is signed in. The browser may automatically attach session credentials, so the application can mistake the forged request for an action the user chose to perform. CSRF can also arise where browsers automatically supply credentials such as HTTP Basic authentication or client certificates. [Official topic](https://portswigger.net/web-security/csrf)

## Solution idea
1. Open Burp's browser and log in to your account.
2. Send the request to Burp Repeater and observe that if you change the domain in the Referer HTTP header then the request is rejected.
3. Delete the Referer header entirely and observe that the request is now accepted.
4. Create and host a proof of concept exploit as described in the solution to the CSRF vulnerability with no defenses lab.
5. Change the email address in your exploit so that it doesn't match your own.
6. Store the exploit, then click "Deliver to victim" to solve the lab.

## Payloads / key values
- `<meta name="referrer" content="no-referrer">`

## Official source
- [PortSwigger Academy: Lab: CSRF where Referer validation depends on header being present](https://portswigger.net/web-security/csrf/bypassing-referer-based-defenses/lab-referer-validation-depends-on-header-being-present)
