# Lab: Performing CSRF exploits over GraphQL

**Official PortSwigger URL:** https://portswigger.net/web-security/graphql/lab-graphql-csrf-via-graphql-api

**Lab idea:** The GraphQL endpoint accepts form-encoded requests, creating a CSRF risk for a state-changing email update. The challenge practices assessing whether request formats and browser behavior allow cross-site actions, and evaluating the need for robust CSRF defenses.

## Vulnerability in brief
GraphQL API vulnerabilities is a topic for learning how to assess GraphQL APIs, not one single vulnerability class. The Academy highlights implementation and design flaws: a GraphQL service commonly exposes multiple operations through one endpoint, while each client request selects fields and can invoke queries or state-changing mutations. If schema exposure, authorization, transport handling, or resource controls are weak, a request may reveal data or trigger actions the caller should not be allowed to perform.

## Solution idea
1. Open Burp's browser, access the lab and log in to your account.
2. Enter a new email address, then click Update email .
3. In Burp, go to Proxy > HTTP history and check the resulting request.
4. Right-click the email change request and select Send to Repeater .
- …
6. Copy the HTML.
7. In the lab, click Go to exploit server .
8. Paste the HTML into the exploit server and click Deliver exploit to victim to solve the lab.

## Payloads / key values
- `Content-Type`
- `x-www-form-urlencoded`
- `query=%0A++++mutation+changeEmail%28%24input%3A+ChangeEmailInput%21%29+%7B%0A++++++++changeEmail%28input%3A+%24input%29+%7B%0A++++++++++++email%0A++++++++%7D%0A++++%7D%0A&operationName=changeEmail&variables=%7B%22input%22%3A%7B%22email%22%3A%22hacker%40hacker.com%22%7D%7D`

## Official source
- [PortSwigger Academy: Lab: Performing CSRF exploits over GraphQL](https://portswigger.net/web-security/graphql/lab-graphql-csrf-via-graphql-api)
