# Lab: DOM XSS in document.write sink using source location.search inside a select element

**Official lab:** [https://portswigger.net/web-security/cross-site-scripting/dom-based/lab-document-write-sink-inside-select-element](https://portswigger.net/web-security/cross-site-scripting/dom-based/lab-document-write-sink-inside-select-element)

## Lab idea

A stock-checker parameter reaches document.write inside a select element. It practices tracing URL input into a DOM sink and accounting for the surrounding HTML element context.

## Vulnerability in brief
Cross-site scripting (XSS) is a web security vulnerability in which an application causes attacker-controlled content to be interpreted as executable script in a user’s browser. The code runs in the vulnerable site’s origin, so it can interfere with the victim’s interaction with that application and may access data or perform actions available to that user.

## Solution idea
1. On the product pages, notice that the dangerous JavaScript extracts a storeId parameter from the location.search source.
2. Add a storeId query parameter to the URL and enter a random alphanumeric string as its value.
3. In the browser, notice that your random string is now listed as one of the options in the drop-down list.
4. Right-click and inspect the drop-down list to confirm that the value of your storeId parameter has been placed inside a select element.
5. Change the URL to include a suitable XSS payload inside the storeId parameter as follows: product?productId=1&storeId="></select><img%20src=1%20onerror=alert(1)>

## Payloads / key values
- `storeId`
- `location.search`
- `document.write`
- `product?productId=1&storeId="></select><img%20src=1%20onerror=alert(1)>`

## Official source
- [PortSwigger Academy: Lab: DOM XSS in document.write sink using source location.search inside a select element](https://portswigger.net/web-security/cross-site-scripting/dom-based/lab-document-write-sink-inside-select-element)
