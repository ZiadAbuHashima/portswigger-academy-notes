# Lab: Web shell upload via path traversal

**Official lab:** [https://portswigger.net/web-security/file-upload/lab-file-upload-web-shell-upload-via-path-traversal](https://portswigger.net/web-security/file-upload/lab-file-upload-web-shell-upload-via-path-traversal)

## Lab idea

This lab contains a vulnerable image upload function. The server is configured to prevent execution of user-supplied files, but this restriction can be bypassed by exploiting a secondary vulnerability. The challenge combines upload handling with a path-handling weakness: a restriction on execution can be undermined if an uploaded file is placed somewhere unexpected. It practices considering both file processing and destination paths.
