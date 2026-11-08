# Lab: DOM XSS in document.write sink using source location.search

**Official lab:** [https://portswigger.net/web-security/cross-site-scripting/dom-based/lab-document-write-sink](https://portswigger.net/web-security/cross-site-scripting/dom-based/lab-document-write-sink)

## Lab idea

A URL query value reaches JavaScript document.write and is written into the page. It practices tracing a controllable source to a DOM-writing sink and assessing unsafe client-side HTML construction.

## Vulnerability in brief
Cross-site scripting (XSS) is a web security vulnerability in which an application causes attacker-controlled content to be interpreted as executable script in a user’s browser. The code runs in the vulnerable site’s origin, so it can interfere with the victim’s interaction with that application and may access data or perform actions available to that user.

## Solution idea
1. Enter a random alphanumeric string into the search box.
2. Right-click and inspect the element, and observe that your random string has been placed inside an img src attribute.
3. Break out of the img attribute by searching for: "><svg onload=alert(1)>

## Payloads / key values
- `img src`
- `img`
- `"><svg onload=alert(1)>`

## Official source
- [PortSwigger Academy: Lab: DOM XSS in document.write sink using source location.search](https://portswigger.net/web-security/cross-site-scripting/dom-based/lab-document-write-sink)
