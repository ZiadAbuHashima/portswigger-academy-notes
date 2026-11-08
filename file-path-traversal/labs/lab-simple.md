# Lab: File path traversal, simple case

**Official PortSwigger URL:** https://portswigger.net/web-security/file-path-traversal/lab-simple

**Lab idea:** A product-image feature uses a request-supplied filename to access a file. This introductory challenge practices recognizing the risk of using a user-controlled filename without adequate confinement to the intended image directory.

## Vulnerability in brief
Path traversal is a vulnerability class that lets an attacker manipulate a file path used by an application to access files outside the intended directory. It is also known as directory traversal. It commonly occurs when an application incorporates user-controlled values, such as a filename in an image or download request, into a filesystem path without safely constraining the resolved destination. Relative path components can move up the directory hierarchy; path handling and validation can also be undermined when checks are incomplete or performed before later decoding or path interpretation.

## Solution idea
1. Use Burp Suite to intercept and modify a request that fetches a product image.
2. Modify the filename parameter, giving it the value: ../../../etc/passwd
3. Observe that the response contains the contents of the /etc/passwd file.

## Payloads / key values
- `filename`
- `../../../etc/passwd`
- `/etc/passwd`

## Official source
- [PortSwigger Academy: Lab: File path traversal, simple case](https://portswigger.net/web-security/file-path-traversal/lab-simple)
