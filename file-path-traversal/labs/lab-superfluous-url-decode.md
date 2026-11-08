# Lab: File path traversal, traversal sequences stripped with superfluous URL-decode

**Official PortSwigger URL:** https://portswigger.net/web-security/file-path-traversal/lab-superfluous-url-decode

**Lab idea:** The application blocks traversal-related input and then decodes it before use. The challenge practices identifying how a mismatch in validation and decoding order can undermine file-path checks.

## Vulnerability in brief
Path traversal is a vulnerability class that lets an attacker manipulate a file path used by an application to access files outside the intended directory. It is also known as directory traversal. It commonly occurs when an application incorporates user-controlled values, such as a filename in an image or download request, into a filesystem path without safely constraining the resolved destination. Relative path components can move up the directory hierarchy; path handling and validation can also be undermined when checks are incomplete or performed before later decoding or path interpretation.

## Solution idea
1. Use Burp Suite to intercept and modify a request that fetches a product image.
2. Modify the filename parameter, giving it the value: ..%252f..%252f..%252fetc/passwd
3. Observe that the response contains the contents of the /etc/passwd file.

## Payloads / key values
- `filename`
- `..%252f..%252f..%252fetc/passwd`
- `/etc/passwd`

## Official source
- [PortSwigger Academy: Lab: File path traversal, traversal sequences stripped with superfluous URL-decode](https://portswigger.net/web-security/file-path-traversal/lab-superfluous-url-decode)
