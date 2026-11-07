# Lab: DOM XSS in innerHTML sink using source location.search

**Official lab:** [https://portswigger.net/web-security/cross-site-scripting/dom-based/lab-innerhtml-sink](https://portswigger.net/web-security/cross-site-scripting/dom-based/lab-innerhtml-sink)

## Lab idea

A URL-controlled search value is assigned to an element through innerHTML. It practices identifying a dangerous DOM sink and tracing user-controlled data from location.search into HTML parsing.
