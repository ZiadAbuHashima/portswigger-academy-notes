# Lab: Basic SSRF against the local server

**Official lab:** [PortSwigger Web Security Academy](https://portswigger.net/web-security/ssrf/lab-basic-ssrf-against-localhost)

**Lab idea:** A stock-check feature makes a server-side request, and the challenge concerns reaching functionality on the application’s own server. It practices recognizing the local-server trust boundary that can make SSRF impactful.

## Vulnerability in brief
Server-side request forgery (SSRF) is a vulnerability that lets an attacker influence a server-side application to send a request to an unintended destination. A common cause is a feature that fetches a user-supplied URL or constructs a URL using user-controlled input, such as a stock lookup, analytics service, or other backend integration. Because the request originates from the application server, it may reach local or internal services that are not directly accessible to an external user. The response may be returned to the user, or the request may be blind, with no backend response reflected in the page.

## Solution idea
1. Browse to /admin and observe that you can't directly access the admin page.
2. Visit a product, click "Check stock", intercept the request in Burp Suite, and send it to Burp Repeater.
3. Change the URL in the stockApi parameter to http://localhost/admin .
4. Read the HTML to identify the URL to delete the target user, which is: http://localhost/admin/delete?username=carlos
5. Submit this URL in the stockApi parameter, to deliver the SSRF attack.

## Payloads / key values
- `/admin`
- `stockApi`
- `http://localhost/admin`
- `http://localhost/admin/delete?username=carlos`

## Official source
- [PortSwigger Academy: Lab: Basic SSRF against the local server](https://portswigger.net/web-security/ssrf/lab-basic-ssrf-against-localhost)
