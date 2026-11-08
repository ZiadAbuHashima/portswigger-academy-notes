# Lab: DOM-based cookie manipulation

**Official lab:** [https://portswigger.net/web-security/dom-based/cookie-manipulation/lab-dom-cookie-manipulation](https://portswigger.net/web-security/dom-based/cookie-manipulation/lab-dom-cookie-manipulation)

## Lab idea

This lab explores client-side cookie manipulation where cookie data is consumed on another page and can contribute to DOM XSS. It practices following data across pages and assessing both where client-side state is set and how it is later used.

## Vulnerability in brief
The Document Object Model (DOM) is the browser’s structured representation of a page and its elements. DOM manipulation is routine; vulnerabilities arise when client-side JavaScript takes attacker-controllable data from a **source** and passes it unsafely to a potentially dangerous **sink**. This topic is a family of client-side vulnerability classes, not a general learning or testing category. DOM-based cross-site scripting is commonly abbreviated **DOM XSS**.

## Solution idea
1. Notice that the home page uses a client-side cookie called lastViewedProduct , whose value is the URL of the last product page that the user visited.
2. Go to the exploit server and add the following iframe to the body, remembering to replace YOUR-LAB-ID with your lab ID: <iframe…
3. Store the exploit and deliver it to the victim.

## Payloads / key values
- `lastViewedProduct`
- `iframe`
- `YOUR-LAB-ID`
- `<iframe src="https://YOUR-LAB-ID.web-security-academy.net/product?productId=1&'><script>print()</script>" onload="if(!window.x)this.src='https://YOUR-LAB-ID.web-security-academy.net';window.x=1;">`
- `onload`

## Official source
- [PortSwigger Academy: Lab: DOM-based cookie manipulation](https://portswigger.net/web-security/dom-based/cookie-manipulation/lab-dom-cookie-manipulation)
