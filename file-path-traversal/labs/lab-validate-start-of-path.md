# Lab: File path traversal, validation of start of path

**Official PortSwigger URL:** https://portswigger.net/web-security/file-path-traversal/lab-validate-start-of-path

**Lab idea:** The application accepts a full path in a request parameter and checks that it starts with an expected folder. The challenge practices distinguishing a textual prefix check from verifying that the final resolved file remains inside the permitted directory.

## Vulnerability in brief
Path traversal is a vulnerability class that lets an attacker manipulate a file path used by an application to access files outside the intended directory. It is also known as directory traversal. It commonly occurs when an application incorporates user-controlled values, such as a filename in an image or download request, into a filesystem path without safely constraining the resolved destination. Relative path components can move up the directory hierarchy; path handling and validation can also be undermined when checks are incomplete or performed before later decoding or path interpretation.

## Solution idea
1. Use Burp Suite to intercept and modify a request that fetches a product image.
2. Modify the filename parameter, giving it the value: /var/www/images/../../../etc/passwd
3. Observe that the response contains the contents of the /etc/passwd file.

## Payloads / key values
- `filename`
- `/var/www/images/../../../etc/passwd`
- `/etc/passwd`

## Official source
- [PortSwigger Academy: Lab: File path traversal, validation of start of path](https://portswigger.net/web-security/file-path-traversal/lab-validate-start-of-path)
