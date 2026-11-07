# Lab: Remote code execution via polyglot web shell upload

**Official lab:** [https://portswigger.net/web-security/file-upload/lab-file-upload-remote-code-execution-via-polyglot-web-shell-upload](https://portswigger.net/web-security/file-upload/lab-file-upload-remote-code-execution-via-polyglot-web-shell-upload)

## Lab idea

This lab contains a vulnerable image upload function. Although it checks the contents of the file to verify that it is a genuine image, it is still possible to upload and execute server-side code. This challenge highlights that an image-content check may still accept a file that also contains server-side code, illustrating the limits of treating a valid image signature or structure as sufficient proof of safety.
