# Lab: SSRF with filter bypass via open redirection vulnerability

**Official lab:** [PortSwigger Web Security Academy](https://portswigger.net/web-security/ssrf/lab-ssrf-filter-bypass-via-open-redirection)

**Lab idea:** The stock-check feature fetches a URL, while an open redirect exists in the application. This challenge practices assessing how redirect-following behavior can undermine destination restrictions in an SSRF context.

## Vulnerability in brief
Server-side request forgery (SSRF) is a vulnerability that lets an attacker influence a server-side application to send a request to an unintended destination. A common cause is a feature that fetches a user-supplied URL or constructs a URL using user-controlled input, such as a stock lookup, analytics service, or other backend integration. Because the request originates from the application server, it may reach local or internal services that are not directly accessible to an external user. The response may be returned to the user, or the request may be blind, with no backend response reflected in the page.

## Solution idea
1. Visit a product, click "Check stock", intercept the request in Burp Suite, and send it to Burp Repeater.
2. Try tampering with the stockApi parameter and observe that it isn't possible to make the server issue the request directly to a different host.
3. Click "next product" and observe that the path parameter is placed into the Location header of a redirection response, resulting in an open redirection.
4. Create a URL that exploits the open redirection vulnerability, and redirects to the admin interface, and feed this into the stockApi parameter on the stock checker…
5. Observe that the stock checker follows the redirection and shows you the admin page.
6. Amend the path to delete the target user: /product/nextProduct?path=http://192.168.0.12:8080/admin/delete?username=carlos

## Payloads / key values
- `stockApi`
- `path`
- `/product/nextProduct?path=http://192.168.0.12:8080/admin`
- `/product/nextProduct?path=http://192.168.0.12:8080/admin/delete?username=carlos`

## Official source
- [PortSwigger Academy: Lab: SSRF with filter bypass via open redirection vulnerability](https://portswigger.net/web-security/ssrf/lab-ssrf-filter-bypass-via-open-redirection)
