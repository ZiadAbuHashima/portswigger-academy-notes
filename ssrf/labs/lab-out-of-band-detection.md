# Lab: Blind SSRF with out-of-band detection

**Official lab:** [PortSwigger Web Security Academy](https://portswigger.net/web-security/ssrf/blind/lab-out-of-band-detection)

**Lab idea:** The challenge centers on analytics software that fetches a URL associated with a product-page request, while the resulting server-side response is not presented directly. It practices recognizing and verifying blind SSRF through an authorized out-of-band observation.

## Vulnerability in brief
Server-side request forgery (SSRF) is a vulnerability that lets an attacker influence a server-side application to send a request to an unintended destination. A common cause is a feature that fetches a user-supplied URL or constructs a URL using user-controlled input, such as a stock lookup, analytics service, or other backend integration. Because the request originates from the application server, it may reach local or internal services that are not directly accessible to an external user. The response may be returned to the user, or the request may be blind, with no backend response reflected in the page.

## Solution idea
1. Visit a product, intercept the request in Burp Suite, and send it to Burp Repeater.
2. Go to the Repeater tab.
3. Go to the Collaborator tab, and click "Poll now".
4. You should see some DNS and HTTP interactions that were initiated by the application as the result of your payload.

## Payloads / key values
The official walkthrough does not specify a reusable payload; follow its stated lab-specific actions and parameters.

## Official source
- [PortSwigger Academy: Lab: Blind SSRF with out-of-band detection](https://portswigger.net/web-security/ssrf/blind/lab-out-of-band-detection)
