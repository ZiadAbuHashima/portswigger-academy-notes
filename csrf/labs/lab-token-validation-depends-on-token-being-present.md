# Lab: CSRF where token validation depends on token being present

**Official lab:** [Lab: CSRF where token validation depends on token being present](https://portswigger.net/web-security/csrf/bypassing-token-validation/lab-token-validation-depends-on-token-being-present)

## Lab idea

This challenge examines a token check that behaves differently when the token parameter is omitted. It practices verifying that missing tokens are rejected just like invalid tokens.

## Vulnerability in brief
Cross-site request forgery (CSRF) is a web security vulnerability that tricks a user’s browser into sending an unintended, authenticated request to an application where that user is signed in. The browser may automatically attach session credentials, so the application can mistake the forged request for an action the user chose to perform. CSRF can also arise where browsers automatically supply credentials such as HTTP Basic authentication or client certificates. [Official topic](https://portswigger.net/web-security/csrf)

## Solution idea
1. Open Burp's browser and log in to your account.
2. Send the request to Burp Repeater and observe that if you change the value of the csrf parameter then the request is rejected.
3. Delete the csrf parameter entirely and observe that the request is now accepted.
4. If you're using Burp Suite Professional, right-click on the request, and from the context menu select Engagement tools / Generate CSRF PoC.
5. Go to the exploit server, paste your exploit HTML into the "Body" section, and click "Store".
6. To verify if the exploit will work, try it on yourself by clicking "View exploit" and checking the resulting HTTP request and response.
7. Change the email address in your exploit so that it doesn't match your own.
8. Store the exploit, then click "Deliver to victim" to solve the lab.

## Payloads / key values
- `csrf`
- `<form method="POST" action="https://YOUR-LAB-ID.web-security-academy.net/my-account/change-email"> <input type="hidden" name="$param1name" value="$param1value"> </form> <script> document.forms[0].submit(); </script>`

## Official source
- [PortSwigger Academy: Lab: CSRF where token validation depends on token being present](https://portswigger.net/web-security/csrf/bypassing-token-validation/lab-token-validation-depends-on-token-being-present)
