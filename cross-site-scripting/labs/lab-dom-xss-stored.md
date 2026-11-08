# Lab: Stored DOM XSS

**Official lab:** [https://portswigger.net/web-security/cross-site-scripting/dom-based/lab-dom-xss-stored](https://portswigger.net/web-security/cross-site-scripting/dom-based/lab-dom-xss-stored)

## Lab idea

A stored blog comment is later processed by client-side code that attempts to encode angle brackets. The challenge practices recognizing persistent DOM-based XSS and the danger of incomplete client-side replacement logic.

## Vulnerability in brief
Cross-site scripting (XSS) is a web security vulnerability in which an application causes attacker-controlled content to be interpreted as executable script in a user’s browser. The code runs in the vulnerable site’s origin, so it can interfere with the victim’s interaction with that application and may access data or perform actions available to that user.

## Solution idea
1. Post a comment containing the following vector:
2. In an attempt to prevent XSS, the website uses the JavaScript replace() function to encode angle brackets.

## Payloads / key values
- `<><img src=1 onerror=alert(1)>`
- `replace()`

## Official source
- [PortSwigger Academy: Lab: Stored DOM XSS](https://portswigger.net/web-security/cross-site-scripting/dom-based/lab-dom-xss-stored)
