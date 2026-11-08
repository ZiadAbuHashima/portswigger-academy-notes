# Lab: DOM XSS in innerHTML sink using source location.search

**Official lab:** [https://portswigger.net/web-security/cross-site-scripting/dom-based/lab-innerhtml-sink](https://portswigger.net/web-security/cross-site-scripting/dom-based/lab-innerhtml-sink)

## Lab idea

A URL-controlled search value is assigned to an element through innerHTML. It practices identifying a dangerous DOM sink and tracing user-controlled data from location.search into HTML parsing.

## Vulnerability in brief
Cross-site scripting (XSS) is a web security vulnerability in which an application causes attacker-controlled content to be interpreted as executable script in a user’s browser. The code runs in the vulnerable site’s origin, so it can interfere with the victim’s interaction with that application and may access data or perform actions available to that user.

## Solution idea
1. Enter the following into the into the search box: <img src=1 onerror=alert(1)>
2. Click "Search".

## Payloads / key values
- `<img src=1 onerror=alert(1)>`
- `src`
- `onerror`
- `alert()`

## Official source
- [PortSwigger Academy: Lab: DOM XSS in innerHTML sink using source location.search](https://portswigger.net/web-security/cross-site-scripting/dom-based/lab-innerhtml-sink)
