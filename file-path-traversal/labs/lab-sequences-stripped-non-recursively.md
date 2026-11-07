# Lab: File path traversal, traversal sequences stripped non-recursively

**Official PortSwigger URL:** https://portswigger.net/web-security/file-path-traversal/lab-sequences-stripped-non-recursively

**Lab idea:** The application removes traversal sequences from a user-supplied filename before using it. The challenge practices assessing why one-pass or non-recursive sanitization can leave path handling unsafe.
