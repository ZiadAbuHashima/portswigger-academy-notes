# Lab: Web shell upload via extension blacklist bypass

**Official lab:** [https://portswigger.net/web-security/file-upload/lab-file-upload-web-shell-upload-via-extension-blacklist-bypass](https://portswigger.net/web-security/file-upload/lab-file-upload-web-shell-upload-via-extension-blacklist-bypass)

## Lab idea

This lab contains a vulnerable image upload function. Certain file extensions are blacklisted, but this defense can be bypassed due to a fundamental flaw in the configuration of this blacklist. The challenge examines an incomplete or flawed extension blacklist. It practices recognizing why a denylist can fail when extension handling and server configuration do not align.
