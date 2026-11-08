# Lab: CSRF vulnerability with no defenses

**Official lab:** [Lab: CSRF vulnerability with no defenses](https://portswigger.net/web-security/csrf/lab-no-defenses)

## Lab idea

This is a baseline CSRF challenge in which an email-change function lacks defenses. It practices recognizing the core condition: a browser can submit a state-changing request while carrying the victim’s authenticated session.

## Vulnerability in brief
Cross-site request forgery (CSRF) is a web security vulnerability that tricks a user’s browser into sending an unintended, authenticated request to an application where that user is signed in. The browser may automatically attach session credentials, so the application can mistake the forged request for an action the user chose to perform. CSRF can also arise where browsers automatically supply credentials such as HTTP Basic authentication or client certificates. [Official topic](https://portswigger.net/web-security/csrf)

## Solution idea
1. Open Burp's browser and log in to your account.
2. If you're using Burp Suite Professional, right-click on the request and select Engagement tools / Generate CSRF PoC.
3. Go to the exploit server, paste your exploit HTML into the "Body" section, and click "Store".
4. To verify that the exploit works, try it on yourself by clicking "View exploit" and then check the resulting HTTP request and response.
5. Change the email address in your exploit so that it doesn't match your own.
6. Click "Deliver to victim" to solve the lab.

## Payloads / key values
- `<form method="POST" action="https://YOUR-LAB-ID.web-security-academy.net/my-account/change-email"> <input type="hidden" name="email" value="anything@web-security-academy.net"> </form> <script> document.forms[0].submit(); </script>`

## Official source
- [PortSwigger Academy: Lab: CSRF vulnerability with no defenses](https://portswigger.net/web-security/csrf/lab-no-defenses)
