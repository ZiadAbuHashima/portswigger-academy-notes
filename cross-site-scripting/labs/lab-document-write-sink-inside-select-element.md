# Lab: DOM XSS in document.write sink using source location.search inside a select element

**Official lab:** [https://portswigger.net/web-security/cross-site-scripting/dom-based/lab-document-write-sink-inside-select-element](https://portswigger.net/web-security/cross-site-scripting/dom-based/lab-document-write-sink-inside-select-element)

## Lab idea

A stock-checker parameter reaches document.write inside a select element. It practices tracing URL input into a DOM sink and accounting for the surrounding HTML element context.
