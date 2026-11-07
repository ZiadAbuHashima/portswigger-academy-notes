# Lab: DOM XSS in jQuery anchor href attribute sink using location.search source

**Official lab:** [https://portswigger.net/web-security/cross-site-scripting/dom-based/lab-jquery-href-attribute-sink](https://portswigger.net/web-security/cross-site-scripting/dom-based/lab-jquery-href-attribute-sink)

## Lab idea

A return-path parameter is used by jQuery to set a link href on the feedback page. It practices tracing URL data into a navigation attribute and distinguishing safe text assignment from safe URL handling.
