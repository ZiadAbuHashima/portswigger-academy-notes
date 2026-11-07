# Lab: Web shell upload via race condition

**Official lab:** [https://portswigger.net/web-security/file-upload/lab-file-upload-web-shell-upload-via-race-condition](https://portswigger.net/web-security/file-upload/lab-file-upload-web-shell-upload-via-race-condition)

## Lab idea

This lab contains a vulnerable image upload function. Although it performs robust validation on any files that are uploaded, it is possible to bypass this validation entirely by exploiting a race condition in the way it processes them. This lab focuses on a timing flaw in otherwise robust upload validation. It practices reasoning about whether uploaded content becomes accessible before validation and cleanup have fully completed.
