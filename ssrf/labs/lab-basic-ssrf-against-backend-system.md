# Lab: Basic SSRF against another back-end system

**Official lab:** [PortSwigger Web Security Academy](https://portswigger.net/web-security/ssrf/lab-basic-ssrf-against-backend-system)

**Lab idea:** The application’s stock-check feature fetches information from an internal system. The challenge practices identifying how server-side URL fetching can reach another backend system that is not ordinarily available to a user.

## Vulnerability in brief
Server-side request forgery (SSRF) is a vulnerability that lets an attacker influence a server-side application to send a request to an unintended destination. A common cause is a feature that fetches a user-supplied URL or constructs a URL using user-controlled input, such as a stock lookup, analytics service, or other backend integration. Because the request originates from the application server, it may reach local or internal services that are not directly accessible to an external user. The response may be returned to the user, or the request may be blind, with no backend response reflected in the page.

## Solution idea
1. Visit a product, click Check stock , intercept the request in Burp Suite, and send it to Burp Intruder.
2. Change the stockApi parameter to http://192.168.0.1:8080/admin then highlight the final octet of the IP address (the number 1 ) and click Add § .
3. In the Payloads side panel, change the payload type to Numbers , and enter 1, 255, and 1 in the From and To and Step boxes respectively.
4. Click Start attack .
5. Click on the Status column to sort it by status code ascending.
6. Click on this request, send it to Burp Repeater, and change the path in the stockApi to: /admin/delete?username=carlos

## Payloads / key values
- `stockApi`
- `http://192.168.0.1:8080/admin`
- `1`
- `200`
- `/admin/delete?username=carlos`

## Official source
- [PortSwigger Academy: Lab: Basic SSRF against another back-end system](https://portswigger.net/web-security/ssrf/lab-basic-ssrf-against-backend-system)
