# Lab: DOM XSS in document.write sink using source location.search

**Official lab:** [https://portswigger.net/web-security/cross-site-scripting/dom-based/lab-document-write-sink](https://portswigger.net/web-security/cross-site-scripting/dom-based/lab-document-write-sink)

## Lab idea

A URL query value reaches JavaScript document.write and is written into the page. It practices tracing a controllable source to a DOM-writing sink and assessing unsafe client-side HTML construction.
