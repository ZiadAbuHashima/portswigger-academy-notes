# Lab: File path traversal, validation of file extension with null byte bypass

**Official PortSwigger URL:** https://portswigger.net/web-security/file-path-traversal/lab-validate-file-extension-null-byte-bypass

**Lab idea:** The application checks that a supplied filename ends with an expected extension. This challenge practices considering how filename parsing and termination behavior can make a suffix-only validation check insufficient.

## Vulnerability in brief
Path traversal is a vulnerability class that lets an attacker manipulate a file path used by an application to access files outside the intended directory. It is also known as directory traversal. It commonly occurs when an application incorporates user-controlled values, such as a filename in an image or download request, into a filesystem path without safely constraining the resolved destination. Relative path components can move up the directory hierarchy; path handling and validation can also be undermined when checks are incomplete or performed before later decoding or path interpretation.

## Solution idea
1. Use Burp Suite to intercept and modify a request that fetches a product image.
2. Modify the filename parameter, giving it the value: ../../../etc/passwd%00.png
3. Observe that the response contains the contents of the /etc/passwd file.

## Payloads / key values
- `filename`
- `../../../etc/passwd%00.png`
- `/etc/passwd`

## Official source
- [PortSwigger Academy: Lab: File path traversal, validation of file extension with null byte bypass](https://portswigger.net/web-security/file-path-traversal/lab-validate-file-extension-null-byte-bypass)
