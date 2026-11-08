# Lab: Stored XSS into anchor href attribute with double quotes HTML-encoded

**Official lab:** [https://portswigger.net/web-security/cross-site-scripting/contexts/lab-href-attribute-double-quotes-html-encoded](https://portswigger.net/web-security/cross-site-scripting/contexts/lab-href-attribute-double-quotes-html-encoded)

## Lab idea

A blog comment is stored and later reflected in an anchor href attribute, with double quotes HTML-encoded. It practices analyzing persistent input in a URL-bearing attribute and the distinction between attribute encoding and safe URL validation.

## Vulnerability in brief
Cross-site scripting (XSS) is a web security vulnerability in which an application causes attacker-controlled content to be interpreted as executable script in a user’s browser. The code runs in the vulnerable site’s origin, so it can interfere with the victim’s interaction with that application and may access data or perform actions available to that user.

## Solution idea
1. Post a comment with a random alphanumeric string in the "Website" input, then use Burp Suite to intercept the request and send it to Burp Repeater.
2. Make a second request in the browser to view the post and use Burp Suite to intercept the request and send it to Burp Repeater.
3. Observe that the random string in the second Repeater tab has been reflected inside an anchor href attribute.
4. Repeat the process again but this time replace your input with the following payload to inject a JavaScript URL that calls alert: javascript:alert(1)
5. Verify the technique worked by right-clicking, selecting "Copy URL", and pasting the URL in the browser.

## Payloads / key values
- `href`
- `javascript:alert(1)`

## Official source
- [PortSwigger Academy: Lab: Stored XSS into anchor href attribute with double quotes HTML-encoded](https://portswigger.net/web-security/cross-site-scripting/contexts/lab-href-attribute-double-quotes-html-encoded)
