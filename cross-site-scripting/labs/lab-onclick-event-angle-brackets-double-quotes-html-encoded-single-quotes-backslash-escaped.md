# Lab: Stored XSS into onclick event with angle brackets and double quotes HTML-encoded and single quotes and backslash escaped

**Official lab:** [https://portswigger.net/web-security/cross-site-scripting/contexts/lab-onclick-event-angle-brackets-double-quotes-html-encoded-single-quotes-backslash-escaped](https://portswigger.net/web-security/cross-site-scripting/contexts/lab-onclick-event-angle-brackets-double-quotes-html-encoded-single-quotes-backslash-escaped)

## Lab idea

A stored comment value is later placed in an onclick event-handler attribute, with several characters encoded or escaped. It practices assessing the heightened risk of inserting untrusted data into executable event-handler contexts.

## Vulnerability in brief
Cross-site scripting (XSS) is a web security vulnerability in which an application causes attacker-controlled content to be interpreted as executable script in a user’s browser. The code runs in the vulnerable site’s origin, so it can interfere with the victim’s interaction with that application and may access data or perform actions available to that user.

## Solution idea
1. Post a comment with a random alphanumeric string in the "Website" input, then use Burp Suite to intercept the request and send it to Burp Repeater.
2. Make a second request in the browser to view the post and use Burp Suite to intercept the request and send it to Burp Repeater.
3. Observe that the random string in the second Repeater tab has been reflected inside an onclick event handler attribute.
4. Repeat the process again but this time modify your input to inject a JavaScript URL that calls alert , using the following payload: http://foo?&apos;-alert(1)-&apos;
5. Verify the technique worked by right-clicking, selecting "Copy URL", and pasting the URL in the browser.

## Payloads / key values
- `onclick`
- `alert`
- `http://foo?&apos;-alert(1)-&apos;`

## Official source
- [PortSwigger Academy: Lab: Stored XSS into onclick event with angle brackets and double quotes HTML-encoded and single quotes and backslash escaped](https://portswigger.net/web-security/cross-site-scripting/contexts/lab-onclick-event-angle-brackets-double-quotes-html-encoded-single-quotes-backslash-escaped)
