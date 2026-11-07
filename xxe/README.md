# XML external entity (XXE) injection

XML external entity (XXE) injection is a vulnerability in applications that process attacker-influenced XML. When an XML parser resolves externally defined entities, the application may be made to access local files or issue network requests using the server's own access and network position. Whether data is exposed directly depends on how the application handles parsed values and errors. [1]

## Main concepts

External entities are XML entities whose values are obtained from outside their declaration, such as from a file path or URL. If a parser processes a document type definition (DTD) and resolves these references, attacker-controlled XML can influence what the server reads or contacts. XXE may be in-band, when entity contents appear in a response, or blind, when they do not. Blind cases may still be detectable through controlled out-of-band interactions or, in some cases, error messages. [1]

The attack surface is not limited to requests that visibly contain XML. It can also arise when user data is embedded into server-generated XML, when XML-based features such as XInclude are used, or when uploaded formats with XML components (for example, SVG) are processed. Applications that accept XML after a content-type or format change can expose additional parsing paths. [1]

## Impact

XXE can disclose files readable by the application, expose sensitive information through parsing errors, or cause server-side request forgery (SSRF) by making the application contact back-end or external systems. Depending on reachable services and available privileges, the consequences can extend to sensitive infrastructure data or compromise of the server or other back-end systems. [1]

## High-level detection and assessment

In an authorized assessment, inventory XML parsing paths and features that may create XML indirectly, including uploads and server-side XML construction. Check whether parsed values or parser errors are reflected in responses. Where no direct output is visible, a controlled out-of-band endpoint can help identify parser-initiated network activity. Assess only systems for which testing is authorized, and keep any checks narrowly scoped. [1]

## Prevention

The primary defense is to disable XML capabilities the application does not require. In particular, configure the parser to disable external entity resolution and XInclude; disable DTD processing when it is unnecessary. Use safe parser configuration for every XML-processing component, including upload processors, and apply least privilege and outbound network controls as defense in depth. [1]

## Lab notes

- [Exploiting XXE to retrieve data by repurposing a local DTD](labs/lab-xxe-trigger-error-message-by-repurposing-local-dtd.md)
- [Exploiting blind XXE to retrieve data via error messages](labs/lab-xxe-with-data-retrieval-via-error-messages.md)
- [Exploiting blind XXE to exfiltrate data using a malicious external DTD](labs/lab-xxe-with-out-of-band-exfiltration.md)
- [Blind XXE with out-of-band interaction](labs/lab-xxe-with-out-of-band-interaction.md)
- [Blind XXE with out-of-band interaction via XML parameter entities](labs/lab-xxe-with-out-of-band-interaction-using-parameter-entities.md)
- [Exploiting XXE to perform SSRF attacks](labs/lab-exploiting-xxe-to-perform-ssrf.md)
- [Exploiting XXE using external entities to retrieve files](labs/lab-exploiting-xxe-to-retrieve-files.md)
- [Exploiting XInclude to retrieve files](labs/lab-xinclude-attack.md)
- [Exploiting XXE via image file upload](labs/lab-xxe-via-file-upload.md)

## References

[1]: https://portswigger.net/web-security/xxe "PortSwigger Web Security Academy: XML external entity injection"
[2]: https://portswigger.net/web-security/xxe/blind/lab-xxe-trigger-error-message-by-repurposing-local-dtd "Lab: Exploiting XXE to retrieve data by repurposing a local DTD"
[3]: https://portswigger.net/web-security/xxe/blind/lab-xxe-with-data-retrieval-via-error-messages "Lab: Exploiting blind XXE to retrieve data via error messages"
[4]: https://portswigger.net/web-security/xxe/blind/lab-xxe-with-out-of-band-exfiltration "Lab: Exploiting blind XXE to exfiltrate data using a malicious external DTD"
[5]: https://portswigger.net/web-security/xxe/blind/lab-xxe-with-out-of-band-interaction "Lab: Blind XXE with out-of-band interaction"
[6]: https://portswigger.net/web-security/xxe/blind/lab-xxe-with-out-of-band-interaction-using-parameter-entities "Lab: Blind XXE with out-of-band interaction via XML parameter entities"
[7]: https://portswigger.net/web-security/xxe/lab-exploiting-xxe-to-perform-ssrf "Lab: Exploiting XXE to perform SSRF attacks"
[8]: https://portswigger.net/web-security/xxe/lab-exploiting-xxe-to-retrieve-files "Lab: Exploiting XXE using external entities to retrieve files"
[9]: https://portswigger.net/web-security/xxe/lab-xinclude-attack "Lab: Exploiting XInclude to retrieve files"
[10]: https://portswigger.net/web-security/xxe/lab-xxe-via-file-upload "Lab: Exploiting XXE via image file upload"
