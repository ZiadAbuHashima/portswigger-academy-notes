# Lab: File path traversal, traversal sequences blocked with absolute path bypass

**Official PortSwigger URL:** https://portswigger.net/web-security/file-path-traversal/lab-absolute-path-bypass

**Lab idea:** This challenge explores a file-handling feature that blocks traversal sequences but interprets the supplied filename relative to a default working directory. It practices reasoning about how path resolution and partial input restrictions affect the files an application can access.
