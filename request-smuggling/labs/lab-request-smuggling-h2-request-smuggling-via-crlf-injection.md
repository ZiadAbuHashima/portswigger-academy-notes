# Lab: HTTP/2 request smuggling via CRLF injection

**Official lab:** [https://portswigger.net/web-security/request-smuggling/advanced/lab-request-smuggling-h2-request-smuggling-via-crlf-injection](https://portswigger.net/web-security/request-smuggling/advanced/lab-request-smuggling-h2-request-smuggling-via-crlf-injection)

## Lab idea

The challenge centers on HTTP/2 downgrading and insufficient sanitization of incoming headers. It practices identifying how this combination can disrupt request boundaries and lead to another user’s account being exposed.

## Vulnerability in brief
HTTP request smuggling (often called **HTTP desync**) is a vulnerability class in which components that process a sequence of HTTP requests disagree about where one request ends and the next begins. In a common deployment, a frontend proxy or load balancer forwards multiple user requests over a reused connection to a backend. If the two systems parse an ambiguous request differently, bytes treated as body by one may be read as the start of another request by the other. This can cause an attacker-controlled prefix to interfere with a later request.

## Solution idea
1. In Burp's browser, use the lab's search function a couple of times and observe that the website records your recent search history.
2. Expand the Inspector's Request Attributes section and make sure the protocol is set to HTTP/2.
3. Using the Inspector, add an arbitrary header to the request.
4. In the body, attempt to smuggle an arbitrary prefix as follows: 0 SMUGGLED Observe that every second request you send receives a 404 response, confirming that you have caused the back-end…
5. Change the body of the request to the following: 0 POST / HTTP/1.1 Host: YOUR-LAB-ID.web-security-academy.net Cookie: session=YOUR-SESSION-COOKIE Content-Length: 800 search=x
6. Send the request, then immediately refresh the page in the browser.
7. Check the recent searches list.
8. In Burp Repeater, send a request for the home page using the stolen session cookie to solve the lab.

## Payloads / key values
- `POST /`
- `\r\n`
- `Transfer-Encoding: chunked`
- `foo`
- `bar \r\n Transfer-Encoding: chunked`
- `0 SMUGGLED`
- `0 POST / HTTP/1.1 Host: YOUR-LAB-ID.web-security-academy.net Cookie: session=YOUR-SESSION-COOKIE Content-Length: 800 search=x`
- `404 Not Found`
- `search=x`
- `GET`
- `POST`

## Official source
- [PortSwigger Academy: Lab: HTTP/2 request smuggling via CRLF injection](https://portswigger.net/web-security/request-smuggling/advanced/lab-request-smuggling-h2-request-smuggling-via-crlf-injection)
