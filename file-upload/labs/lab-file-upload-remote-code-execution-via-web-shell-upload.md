# Lab: Remote code execution via web shell upload

**Official lab:** [https://portswigger.net/web-security/file-upload/lab-file-upload-remote-code-execution-via-web-shell-upload](https://portswigger.net/web-security/file-upload/lab-file-upload-remote-code-execution-via-web-shell-upload)

## Lab idea

This lab contains a vulnerable image upload function. It doesn't perform any validation on the files users upload before storing them on the server's filesystem. The challenge focuses on the consequences of accepting uploaded files without validation when they are stored on the server, and the risk that a server-side file may be interpreted as code.
