# Lab: SSRF with blacklist-based input filter

**Official lab:** [PortSwigger Web Security Academy](https://portswigger.net/web-security/ssrf/lab-ssrf-with-blacklist-filter)

**Lab idea:** A stock-check request is subject to a blacklist-based anti-SSRF filter. The challenge practices evaluating the limitations of denylist validation and understanding why destination checks must account for alternate representations and parsing behavior.

## Vulnerability in brief
Server-side request forgery (SSRF) is a vulnerability that lets an attacker influence a server-side application to send a request to an unintended destination. A common cause is a feature that fetches a user-supplied URL or constructs a URL using user-controlled input, such as a stock lookup, analytics service, or other backend integration. Because the request originates from the application server, it may reach local or internal services that are not directly accessible to an external user. The response may be returned to the user, or the request may be blind, with no backend response reflected in the page.

## Solution idea
1. Visit a product, click "Check stock", intercept the request in Burp Suite, and send it to Burp Repeater.
2. Change the URL in the stockApi parameter to http://127.0.0.1/ and observe that the request is blocked.
3. Bypass the block by changing the URL to: http://127.1/
4. Change the URL to http://127.1/admin and observe that the URL is blocked again.
5. Obfuscate the "a" by double-URL encoding it to %2561 to access the admin interface and delete the target user.

## Payloads / key values
- `stockApi`
- `http://127.0.0.1/`
- `http://127.1/`
- `http://127.1/admin`

## Official source
- [PortSwigger Academy: Lab: SSRF with blacklist-based input filter](https://portswigger.net/web-security/ssrf/lab-ssrf-with-blacklist-filter)
