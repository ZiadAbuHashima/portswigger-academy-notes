# Lab: File path traversal, validation of file extension with null byte bypass

**Official PortSwigger URL:** https://portswigger.net/web-security/file-path-traversal/lab-validate-file-extension-null-byte-bypass

**Lab idea:** The application checks that a supplied filename ends with an expected extension. This challenge practices considering how filename parsing and termination behavior can make a suffix-only validation check insufficient.
