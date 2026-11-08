# Lab: 0.CL request smuggling

**Official lab:** [https://portswigger.net/web-security/request-smuggling/advanced/lab-request-smuggling-0cl-request-smuggling](https://portswigger.net/web-security/request-smuggling/advanced/lab-request-smuggling-0cl-request-smuggling)

## Lab idea

This advanced exercise focuses on 0.CL request smuggling and the way a request-boundary mismatch can affect a later visitor. It practices recognizing a newer desynchronization pattern and assessing its potential browser-side impact in a controlled environment.

## Vulnerability in brief
HTTP request smuggling (often called **HTTP desync**) is a vulnerability class in which components that process a sequence of HTTP requests disagree about where one request ends and the next begins. In a common deployment, a frontend proxy or load balancer forwards multiple user requests over a reused connection to a backend. If the two systems parse an ambiguous request differently, bytes treated as body by one may be read as the start of another request by the other. This can cause an attacker-controlled prefix to interfere with a later request.

## Solution idea
Solution Livestream with James Kettle

## Payloads / key values
The official walkthrough does not specify a reusable payload; follow its stated lab-specific actions and parameters.

## Official source
- [PortSwigger Academy: Lab: 0.CL request smuggling](https://portswigger.net/web-security/request-smuggling/advanced/lab-request-smuggling-0cl-request-smuggling)
