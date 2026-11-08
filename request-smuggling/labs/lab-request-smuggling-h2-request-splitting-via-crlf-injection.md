# Lab: HTTP/2 request splitting via CRLF injection

**Official lab:** [https://portswigger.net/web-security/request-smuggling/advanced/lab-request-smuggling-h2-request-splitting-via-crlf-injection](https://portswigger.net/web-security/request-smuggling/advanced/lab-request-smuggling-h2-request-splitting-via-crlf-injection)

## Lab idea

This exercise examines request splitting caused by header sanitization failures during HTTP/2 downgrading. It practices understanding response-queue poisoning as a way that request desynchronization can affect privileged application behavior.

## Vulnerability in brief
HTTP request smuggling (often called **HTTP desync**) is a vulnerability class in which components that process a sequence of HTTP requests disagree about where one request ends and the next begins. In a common deployment, a frontend proxy or load balancer forwards multiple user requests over a reused connection to a backend. If the two systems parse an ambiguous request differently, bytes treated as body by one may be read as the start of another request by the other. This can cause an attacker-controlled prefix to interfere with a later request.

## Solution idea
1. Send a request for GET / to Burp Repeater.
2. Change the path of the request to a non-existent endpoint, such as /x .
3. Using the Inspector, append an arbitrary header to the end of the request.
4. Send the request.
5. Wait for around 5 seconds, then send the request again to fetch an arbitrary response.
6. Copy the session cookie and use it to send the following request: GET /admin HTTP/2 Host: YOUR-LAB-ID.web-security-academy.net Cookie: session=STOLEN-SESSION-COOKIE
7. Send the request repeatedly until you receive a 200 response containing the admin panel.
8. In the response, find the URL for deleting carlos ( /admin/delete?username=carlos ), then update the path in your request accordingly.

## Payloads / key values
- `GET /`
- `/x`
- `\r\n`
- `foo`
- `bar \r\n \r\n GET /x HTTP/1.1 \r\n Host: YOUR-LAB-ID.web-security-academy.net`
- `\r\n\r\n`
- `GET /admin HTTP/2 Host: YOUR-LAB-ID.web-security-academy.net Cookie: session=STOLEN-SESSION-COOKIE`
- `carlos`
- `/admin/delete?username=carlos`

## Official source
- [PortSwigger Academy: Lab: HTTP/2 request splitting via CRLF injection](https://portswigger.net/web-security/request-smuggling/advanced/lab-request-smuggling-h2-request-splitting-via-crlf-injection)
