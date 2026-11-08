# Lab: Stored XSS into HTML context with nothing encoded

**Official lab:** [https://portswigger.net/web-security/cross-site-scripting/stored/lab-html-context-nothing-encoded](https://portswigger.net/web-security/cross-site-scripting/stored/lab-html-context-nothing-encoded)

## Lab idea

A blog comment is stored and later rendered into an HTML page without encoding. It practices distinguishing persistent XSS from request-reflected behavior and assessing exposure of users who view stored content.

## Vulnerability in brief
Cross-site scripting (XSS) is a web security vulnerability in which an application causes attacker-controlled content to be interpreted as executable script in a user’s browser. The code runs in the vulnerable site’s origin, so it can interfere with the victim’s interaction with that application and may access data or perform actions available to that user.

## Solution idea
1. Enter the following into the comment box: <script>alert(1)</script>
2. Enter a name, email and website.
3. Click "Post comment".
4. Go back to the blog.

## Payloads / key values
- `<script>alert(1)</script>`

## Official source
- [PortSwigger Academy: Lab: Stored XSS into HTML context with nothing encoded](https://portswigger.net/web-security/cross-site-scripting/stored/lab-html-context-nothing-encoded)
