# Lab: Bypassing GraphQL brute force protections

**Official PortSwigger URL:** https://portswigger.net/web-security/graphql/lab-graphql-brute-force-protection-bypass

**Lab idea:** This challenge explores how a GraphQL login API's request-based rate limiter can fail to account for multiple operations represented in one request. It practices assessing authentication protections in the context of GraphQL aliases and recognizing why limits should consider the work performed by an operation.

## Vulnerability in brief
GraphQL API vulnerabilities is a topic for learning how to assess GraphQL APIs, not one single vulnerability class. The Academy highlights implementation and design flaws: a GraphQL service commonly exposes multiple operations through one endpoint, while each client request selects fields and can invoke queries or state-changing mutations. If schema exposure, authorization, transport handling, or resource controls are weak, a request may reveal data or trigger actions the caller should not be allowed to perform.

## Solution idea
1. In Burp's browser, access the lab and select My account .
2. Attempt to log in to the site using incorrect credentials.
3. In Burp, go to Proxy > HTTP history .
4. Right-click the login request and select Send to Repeater .
- …
6. Use the search bar below the response to search for the string true .
7. Check the request for the password that was used by the successful alias.
8. Log in to the site using the carlos credentials to solve the lab.

## Payloads / key values
- `mutation {}`
- `carlos`
- `operationName`
- `success`
- `mutation { bruteforce0:login(input:{password: "123456", username: "carlos"}) { token success } bruteforce1:login(input:{password: "password", username: "carlos"}) { token success } ... bruteforce99:login(input:{password: "12345678", username: "carlos"}) { token success } }`
- `true`

## Official source
- [PortSwigger Academy: Lab: Bypassing GraphQL brute force protections](https://portswigger.net/web-security/graphql/lab-graphql-brute-force-protection-bypass)
