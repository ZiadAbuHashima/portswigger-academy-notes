# Lab: Exploiting blind XXE to retrieve data via error messages

**Official lab:** [PortSwigger Web Security Academy](https://portswigger.net/web-security/xxe/blind/lab-xxe-with-data-retrieval-via-error-messages)

**Lab idea:** The stock-check feature parses XML without returning parsed values. The challenge is to understand how a blind XXE condition can disclose data through a deliberately triggered parser error, practicing error-based assessment when direct entity output is unavailable.
