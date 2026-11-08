# Lab: Reflected XSS into HTML context with nothing encoded

**Official lab:** [https://portswigger.net/web-security/cross-site-scripting/reflected/lab-html-context-nothing-encoded](https://portswigger.net/web-security/cross-site-scripting/reflected/lab-html-context-nothing-encoded)

## Lab idea

A search parameter is reflected into an HTML response without encoding. It practices recognizing a basic reflected-XSS data flow from request input to an HTML response.

## Vulnerability in brief
Cross-site scripting (XSS) is a web security vulnerability in which an application causes attacker-controlled content to be interpreted as executable script in a user’s browser. The code runs in the vulnerable site’s origin, so it can interfere with the victim’s interaction with that application and may access data or perform actions available to that user.

## Solution idea
1. Copy and paste the following into the search box: <script>alert(1)</script>
2. Click "Search".

## Payloads / key values
- `<script>alert(1)</script>`

## Official source
- [PortSwigger Academy: Lab: Reflected XSS into HTML context with nothing encoded](https://portswigger.net/web-security/cross-site-scripting/reflected/lab-html-context-nothing-encoded)
