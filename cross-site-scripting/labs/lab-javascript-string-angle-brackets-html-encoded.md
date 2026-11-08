# Lab: Reflected XSS into a JavaScript string with angle brackets HTML encoded

**Official lab:** [https://portswigger.net/web-security/cross-site-scripting/contexts/lab-javascript-string-angle-brackets-html-encoded](https://portswigger.net/web-security/cross-site-scripting/contexts/lab-javascript-string-angle-brackets-html-encoded)

## Lab idea

The search term is reflected inside a JavaScript string, and angle brackets are HTML-encoded. This practices distinguishing HTML encoding from JavaScript-string encoding and assessing the actual parsing context.

## Vulnerability in brief
Cross-site scripting (XSS) is a web security vulnerability in which an application causes attacker-controlled content to be interpreted as executable script in a user’s browser. The code runs in the vulnerable site’s origin, so it can interfere with the victim’s interaction with that application and may access data or perform actions available to that user.

## Solution idea
1. Submit a random alphanumeric string in the search box, then use Burp Suite to intercept the search request and send it to Burp Repeater.
2. Observe that the random string has been reflected inside a JavaScript string.
3. Replace your input with the following payload to break out of the JavaScript string and inject an alert: '-alert(1)-'
4. Verify the technique worked by right clicking, selecting "Copy URL", and pasting the URL in the browser.

## Payloads / key values
- `'-alert(1)-'`

## Official source
- [PortSwigger Academy: Lab: Reflected XSS into a JavaScript string with angle brackets HTML encoded](https://portswigger.net/web-security/cross-site-scripting/contexts/lab-javascript-string-angle-brackets-html-encoded)
