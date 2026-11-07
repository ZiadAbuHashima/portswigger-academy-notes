# Lab: DOM XSS in jQuery selector sink using a hashchange event

**Official lab:** [https://portswigger.net/web-security/cross-site-scripting/dom-based/lab-jquery-selector-hash-change-event](https://portswigger.net/web-security/cross-site-scripting/dom-based/lab-jquery-selector-hash-change-event)

## Lab idea

A value from the URL fragment is passed to jQuery’s selector logic to locate and scroll to a post after a hash change. It practices recognizing DOM sources beyond query parameters and libraries that interpret strings as selectors or markup.
