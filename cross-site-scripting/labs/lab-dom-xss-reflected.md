# Lab: Reflected DOM XSS

**Official lab:** [https://portswigger.net/web-security/cross-site-scripting/dom-based/lab-dom-xss-reflected](https://portswigger.net/web-security/cross-site-scripting/dom-based/lab-dom-xss-reflected)

## Lab idea

The server reflects search data in a response that client-side JavaScript then processes unsafely and writes to a dangerous sink. It practices tracing the full reflected-DOM data flow across server and browser code.
