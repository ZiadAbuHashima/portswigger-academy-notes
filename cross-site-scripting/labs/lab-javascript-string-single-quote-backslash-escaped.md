# Lab: Reflected XSS into a JavaScript string with single quote and backslash escaped

**Official lab:** [https://portswigger.net/web-security/cross-site-scripting/contexts/lab-javascript-string-single-quote-backslash-escaped](https://portswigger.net/web-security/cross-site-scripting/contexts/lab-javascript-string-single-quote-backslash-escaped)

## Lab idea

The reflected value is placed in a JavaScript string where single quotes and backslashes are escaped. It practices reasoning about JavaScript string delimiters and escape handling in context-specific output.

## Vulnerability in brief
Cross-site scripting (XSS) is a web security vulnerability in which an application causes attacker-controlled content to be interpreted as executable script in a user’s browser. The code runs in the vulnerable site’s origin, so it can interfere with the victim’s interaction with that application and may access data or perform actions available to that user.

## Solution idea
1. Submit a random alphanumeric string in the search box, then use Burp Suite to intercept the search request and send it to Burp Repeater.
2. Observe that the random string has been reflected inside a JavaScript string.
3. Try sending the payload test'payload and observe that your single quote gets backslash-escaped, preventing you from breaking out of the string.
4. Replace your input with the following payload to break out of the script block and inject a new script: </script><script>alert(1)</script>
5. Verify the technique worked by right clicking, selecting "Copy URL", and pasting the URL in the browser.

## Payloads / key values
- `test'payload`
- `</script><script>alert(1)</script>`

## Official source
- [PortSwigger Academy: Lab: Reflected XSS into a JavaScript string with single quote and backslash escaped](https://portswigger.net/web-security/cross-site-scripting/contexts/lab-javascript-string-single-quote-backslash-escaped)
