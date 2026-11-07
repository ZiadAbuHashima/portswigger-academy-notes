# Lab: Web shell upload via obfuscated file extension

**Official lab:** [https://portswigger.net/web-security/file-upload/lab-file-upload-web-shell-upload-via-obfuscated-file-extension](https://portswigger.net/web-security/file-upload/lab-file-upload-web-shell-upload-via-obfuscated-file-extension)

## Lab idea

This lab contains a vulnerable image upload function. Certain file extensions are blacklisted, but this defense can be bypassed using a classic obfuscation technique. This lab explores how differences in filename parsing can undermine extension checks. It practices assessing whether a file-type restriction remains reliable when names are interpreted differently across components.
