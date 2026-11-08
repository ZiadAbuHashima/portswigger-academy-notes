# Lab: DOM-based open redirection

**Official lab:** [https://portswigger.net/web-security/dom-based/open-redirection/lab-dom-open-redirection](https://portswigger.net/web-security/dom-based/open-redirection/lab-dom-open-redirection)

## Lab idea

This lab concerns an open redirect driven by a URL parameter that affects a page’s return link. It practices identifying URL-derived navigation decisions and assessing whether destinations are appropriately constrained.

## Vulnerability in brief
The Document Object Model (DOM) is the browser’s structured representation of a page and its elements. DOM manipulation is routine; vulnerabilities arise when client-side JavaScript takes attacker-controllable data from a **source** and passes it unsafely to a potentially dangerous **sink**. This topic is a family of client-side vulnerability classes, not a general learning or testing category. DOM-based cross-site scripting is commonly abbreviated **DOM XSS**.

## Solution idea
1. The blog post page contains the following link, which returns to the home page of the blog:
2. The url parameter contains an open redirection vulnerability that allows you to change where the "Back to Blog" link takes the user.

## Payloads / key values
- `<a href='#' onclick='returnURL' = /url=https?:\/\/.+)/.exec(location); if(returnUrl)location.href = returnUrl[1];else location.href = "/"'>Back to Blog</a>`
- `url`
- `https://YOUR-LAB-ID.web-security-academy.net/post?postId=4&url=https://YOUR-EXPLOIT-SERVER-ID.exploit-server.net/`

## Official source
- [PortSwigger Academy: Lab: DOM-based open redirection](https://portswigger.net/web-security/dom-based/open-redirection/lab-dom-open-redirection)
