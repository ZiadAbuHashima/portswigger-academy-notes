# Lab: SSRF with whitelist-based input filter

**Official lab:** [PortSwigger Web Security Academy](https://portswigger.net/web-security/ssrf/lab-ssrf-with-whitelist-filter)

**Lab idea:** The stock-check feature applies a whitelist to destinations. This challenge practices considering how URL parsers and validation rules can disagree, and why a whitelist must be applied to the destination the server will actually contact.