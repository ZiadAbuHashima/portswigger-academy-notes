# Lab: Reflected DOM XSS

**Official lab:** [https://portswigger.net/web-security/cross-site-scripting/dom-based/lab-dom-xss-reflected](https://portswigger.net/web-security/cross-site-scripting/dom-based/lab-dom-xss-reflected)

## Lab idea

The server reflects search data in a response that client-side JavaScript then processes unsafely and writes to a dangerous sink. It practices tracing the full reflected-DOM data flow across server and browser code.

## Vulnerability in brief
Cross-site scripting (XSS) is a web security vulnerability in which an application causes attacker-controlled content to be interpreted as executable script in a user’s browser. The code runs in the vulnerable site’s origin, so it can interfere with the victim’s interaction with that application and may access data or perform actions available to that user.

## Solution idea
1. In Burp Suite, go to the Proxy tool and make sure that the Intercept feature is switched on.
2. Back in the lab, go to the target website and use the search bar to search for a random test string, such as "XSS" .
3. Return to the Proxy tool in Burp Suite and forward the request.
4. On the Intercept tab, notice that the string is reflected in a JSON response called search-results .
5. From the Site Map, open the searchResults.js file and notice that the JSON response is used with an eval() function call.
6. By experimenting with different search strings, you can identify that the JSON response is escaping quotation marks.
7. To solve this lab, enter the following search term: \"-alert(1)}//

## Payloads / key values
- `"XSS"`
- `search-results`
- `searchResults.js`
- `eval()`
- `\"-alert(1)}//`
- `alert()`
- `{"searchTerm":"\\"-alert(1)}//", "results":[]}`

## Official source
- [PortSwigger Academy: Lab: Reflected DOM XSS](https://portswigger.net/web-security/cross-site-scripting/dom-based/lab-dom-xss-reflected)
