# Lab: HTTP request smuggling, confirming a TE.CL vulnerability via differential responses

**Official lab:** [https://portswigger.net/web-security/request-smuggling/finding/lab-confirming-te-cl-via-differential-responses](https://portswigger.net/web-security/request-smuggling/finding/lab-confirming-te-cl-via-differential-responses)

## Lab idea

This finding-focused exercise practices identifying a TE.CL parsing discrepancy through an unusual response to a subsequent request. It builds skill in recognizing differential behavior as evidence of desynchronization.

## Vulnerability in brief
HTTP request smuggling (often called **HTTP desync**) is a vulnerability class in which components that process a sequence of HTTP requests disagree about where one request ends and the next begins. In a common deployment, a frontend proxy or load balancer forwards multiple user requests over a reused connection to a backend. If the two systems parse an ambiguous request differently, bytes treated as body by one may be read as the start of another request by the other. This can cause an attacker-controlled prefix to interfere with a later request.

## Solution idea
1. In Burp Suite, go to the Repeater menu and ensure that the "Update Content-Length" option is unchecked.
2. Using Burp Repeater, issue the following request twice:
3. The second request should receive an HTTP 404 response.

## Payloads / key values
- `POST / HTTP/1.1 Host: YOUR-LAB-ID.web-security-academy.net Content-Type: application/x-www-form-urlencoded Content-length: 4 Transfer-Encoding: chunked 5e POST /404 HTTP/1.1 Content-Type: application/x-www-form-urlencoded Content-Length: 15 x=1 0`

## Official source
- [PortSwigger Academy: Lab: HTTP request smuggling, confirming a TE.CL vulnerability via differential responses](https://portswigger.net/web-security/request-smuggling/finding/lab-confirming-te-cl-via-differential-responses)
