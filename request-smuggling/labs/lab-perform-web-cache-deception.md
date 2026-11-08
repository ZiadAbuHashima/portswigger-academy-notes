# Lab: Exploiting HTTP request smuggling to perform web cache deception

**Official lab:** [https://portswigger.net/web-security/request-smuggling/exploiting/lab-perform-web-cache-deception](https://portswigger.net/web-security/request-smuggling/exploiting/lab-perform-web-cache-deception)

## Lab idea

This challenge combines request smuggling with caching of static resources so that a victim’s API key can become available through cached content. It practices assessing cache-deception risks created by request desynchronization.

## Vulnerability in brief
HTTP request smuggling (often called **HTTP desync**) is a vulnerability class in which components that process a sequence of HTTP requests disagree about where one request ends and the next begins. In a common deployment, a frontend proxy or load balancer forwards multiple user requests over a reused connection to a backend. If the two systems parse an ambiguous request differently, bytes treated as body by one may be read as the start of another request by the other. This can cause an attacker-controlled prefix to interfere with a later request.

## Solution idea
1. Log in to your account and access the user account page.
2. Observe that the response doesn't have any anti-caching headers.
3. Smuggle a request to fetch the API key: POST / HTTP/1.1 Host: YOUR-LAB-ID.web-security-academy.net Content-Type: application/x-www-form-urlencoded Content-Length: 42 Transfer-Encoding…
4. Repeat this request a few times, then load the home page in an incognito browser window.
5. Use the Search function on the Burp menu to see if the phrase "Your API Key" has appeared in any static resources.
6. Submit the victim's API key as the lab solution.

## Payloads / key values
- `POST / HTTP/1.1 Host: YOUR-LAB-ID.web-security-academy.net Content-Type: application/x-www-form-urlencoded Content-Length: 42 Transfer-Encoding: chunked 0 GET /my-account HTTP/1.1 X-Ignore: X`

## Official source
- [PortSwigger Academy: Lab: Exploiting HTTP request smuggling to perform web cache deception](https://portswigger.net/web-security/request-smuggling/exploiting/lab-perform-web-cache-deception)
