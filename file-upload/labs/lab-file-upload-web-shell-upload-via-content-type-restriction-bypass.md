# Lab: Web shell upload via Content-Type restriction bypass

**Official lab:** [https://portswigger.net/web-security/file-upload/lab-file-upload-web-shell-upload-via-content-type-restriction-bypass](https://portswigger.net/web-security/file-upload/lab-file-upload-web-shell-upload-via-content-type-restriction-bypass)

## Lab idea

This lab contains a vulnerable image upload function. It attempts to prevent users from uploading unexpected file types, but relies on checking user-controllable input to verify this. This lab demonstrates the weakness of relying on user-controllable Content-Type information to decide whether an uploaded file is safe. It practices assessing whether validation is based on trustworthy evidence.
