# Lab: CSRF where token is not tied to user session

**Official lab:** [Lab: CSRF where token is not tied to user session](https://portswigger.net/web-security/csrf/bypassing-token-validation/lab-token-not-tied-to-user-session)

## Lab idea

This challenge uses a CSRF token that is not integrated with the user’s session. It practices checking whether a token is genuinely bound to the session it is intended to protect.

## Vulnerability in brief
Cross-site request forgery (CSRF) is a web security vulnerability that tricks a user’s browser into sending an unintended, authenticated request to an application where that user is signed in. The browser may automatically attach session credentials, so the application can mistake the forged request for an action the user chose to perform. CSRF can also arise where browsers automatically supply credentials such as HTTP Basic authentication or client certificates. [Official topic](https://portswigger.net/web-security/csrf)

## Solution idea
1. Open Burp's browser and log in to your account.
2. Make a note of the value of the CSRF token, then drop the request.
3. Open a private/incognito browser window, log in to your other account, and send the update email request into Burp Repeater.
4. Observe that if you swap the CSRF token with the value from the other account, then the request is accepted.
5. Create and host a proof of concept exploit as described in the solution to the CSRF vulnerability with no defenses lab.
6. Change the email address in your exploit so that it doesn't match your own.
7. Store the exploit, then click "Deliver to victim" to solve the lab.

## Payloads / key values
The official walkthrough does not specify a reusable payload; follow its stated lab-specific actions and parameters.

## Official source
- [PortSwigger Academy: Lab: CSRF where token is not tied to user session](https://portswigger.net/web-security/csrf/bypassing-token-validation/lab-token-not-tied-to-user-session)
