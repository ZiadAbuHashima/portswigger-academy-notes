# Lab: File path traversal, traversal sequences stripped with superfluous URL-decode

**Official PortSwigger URL:** https://portswigger.net/web-security/file-path-traversal/lab-superfluous-url-decode

**Lab idea:** The application blocks traversal-related input and then decodes it before use. The challenge practices identifying how a mismatch in validation and decoding order can undermine file-path checks.
