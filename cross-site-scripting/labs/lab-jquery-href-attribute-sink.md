# Lab: DOM XSS in jQuery anchor href attribute sink using location.search source

**Official lab:** [https://portswigger.net/web-security/cross-site-scripting/dom-based/lab-jquery-href-attribute-sink](https://portswigger.net/web-security/cross-site-scripting/dom-based/lab-jquery-href-attribute-sink)

## Lab idea

A return-path parameter is used by jQuery to set a link href on the feedback page. It practices tracing URL data into a navigation attribute and distinguishing safe text assignment from safe URL handling.

## Vulnerability in brief
Cross-site scripting (XSS) is a web security vulnerability in which an application causes attacker-controlled content to be interpreted as executable script in a user’s browser. The code runs in the vulnerable site’s origin, so it can interfere with the victim’s interaction with that application and may access data or perform actions available to that user.

## Solution idea
1. On the Submit feedback page, change the query parameter returnPath to / followed by a random alphanumeric string.
2. Right-click and inspect the element, and observe that your random string has been placed inside an a href attribute.
3. Change returnPath to: javascript:alert(document.cookie) Hit enter and click "back".

## Payloads / key values
- `returnPath`
- `/`
- `href`
- `javascript:alert(document.cookie)`

## Official source
- [PortSwigger Academy: Lab: DOM XSS in jQuery anchor href attribute sink using location.search source](https://portswigger.net/web-security/cross-site-scripting/dom-based/lab-jquery-href-attribute-sink)
